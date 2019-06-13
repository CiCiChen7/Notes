## ROI Pooling



Let’s consider a small example to see how it works. We’re going to perform region of interest pooling on a single 8×8 feature map, one region of interest and an output size of 2×2. Our input feature map looks like this:

![1](/Users/cuijingchen/Documents/Notes/Other Notes/RoI pooling, RoI Align/res/1.jpg)

Let’s say we also have a region proposal (top left, bottom right coordinates): (0, 3), (7, 8). In the picture it would look like this:

![2](/Users/cuijingchen/Documents/Notes/Other Notes/RoI pooling, RoI Align/res/2.jpg)



Normally, there’d be multiple feature maps and multiple proposals for each of them, but we’re keeping things simple for the example.
By dividing it into (2×2) sections (because the output size is 2×2) we get:

![3](/Users/cuijingchen/Documents/Notes/Other Notes/RoI pooling, RoI Align/res/3.jpg)

Notice that the size of the region of interest doesn’t have to be perfectly divisible by the number of pooling sections (in this case our RoI is 7×5 and we have 2×2 pooling sections).
The max values in each of the sections are:

![4](/Users/cuijingchen/Documents/Notes/Other Notes/RoI pooling, RoI Align/res/4.jpg)

And that’s the output from the Region of Interest pooling layer. 



## RoI Align

Another major contribution of Mask R-CNN is the refinement of the ROI pooling. In ROI, the warping is digitalized (top left diagram below): the cell boundaries of the target feature map are forced to realign with the boundary of the input feature maps. Therefore, each target cells may not be in the same size (bottom left diagram). Mask R-CNN uses **ROI Align** which does not digitalize the boundary of the cells (top right) and make every target cell to have the same size (bottom right). It also applies interpolation to calculate the feature map values within the cell better. For example, by applying interpolation, the maximum feature value on the top left is changed from 0.8 to 0.88 now.

![roi_align](/Users/cuijingchen/Documents/Notes/Other Notes/RoI pooling, RoI Align/res/roi_align.png)