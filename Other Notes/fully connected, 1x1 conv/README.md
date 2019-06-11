If you kernel is 1x1, then you will have only 1 weight, and you feature layer will be the same size as your input layer.
Output_i = w * Input_i.
This construction has no point,  since there is one unique weight that is reused for every input. 

If you want a equivalent to a fully connected layer, you have to make your kernel the size of your input. And you will have
Output_i = w_i * Input_i.
In this case, no convolution will be done since 1 round of dot product is enough to cover the whole area of input.