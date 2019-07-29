





### Fully convolutional network

*****

Fully **convolutional** indicates that the neural network is composed of convolutional layers without any fully-**connected** layers or MLP usually found at the end of the network.

1. #### Why called fully convolutional network?

In classification, conventionally, an input image is downsized and goes through the convolution layers and fully connected (FC) layers, and output one predicted label for the input image, as follows:

![fcn1](./res/fcn1.png)



Imagine we **turn the FC layers into 1×1 convolutional layers**:

![fcn2](./res/fcn2.png)

And if the image is not downsized, the output will not be a single label. Instead, the output has a size smaller than the input image (due to the max pooling):

![fcn3](./res/fcn3.png)

If we upsample the output above, then we can calculate the pixelwise output (label map) as below:

![fcn4](./res/fcn4.png)

![fcn5](./res/fcn5.png)

2. #### FCN variants

![fcn](fcn.png)