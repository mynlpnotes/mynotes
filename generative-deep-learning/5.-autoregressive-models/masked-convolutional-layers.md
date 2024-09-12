# Masked Convolutional Layers

* Whilst convolutional layers are extremely useful for feature detection, they cannot directly be used in an autoregressive sense, because there is no ordering placed on the pixels
* For us to be able to apply convolutional layers to image generation in an autoregressive sense, we must first place an ordering on the pixels and ensure that the filters are only able to see pixels that precede the pixel in question
* We can then generate images one pixel at a time, by applying convolutional filters to the current image to predict the value of the next pixel from all preceding pixels
* Ordering for the pixels - top left to bottom right, moving first along the rows and then down the columns
* We then mask the convolutional filters so that the output of the layer at each pixel is only influenced by pixel values that precede the pixel in question
* This is achieved by multiplying a mask of ones and zeros with the filter weights matrix, so that the values of any pixels that are after the target pixel are zeroed

Types of mask:

1. Type A: Central pixel is masked
2. Type B: Central pixel is not masked

*

    <figure><img src="../../.gitbook/assets/image (11) (1).png" alt="" width="450"><figcaption></figcaption></figure>
* The initial masked convolutional layer (i.e., the one that is applied directly to the input image) cannot use the central pixel, because this is precisely the pixel we want the network to guess!
* However, subsequent layers can use the central pixel because this will have been calculated only as a result of information from preceding pixels in the original input image
*

    ```python
    class MaskedConvLayer(layers.Layer):
        def __init__(self, mask_type, **kwargs):
            super(MaskedConvLayer, self).__init__()
            self.mask_type = mask_type
            self.conv = layers.Conv2D(**kwargs) 

        def build(self, input_shape):
            self.conv.build(input_shape)
            kernel_shape = self.conv.kernel.get_shape()
            self.mask = np.zeros(shape=kernel_shape) 
            self.mask[: kernel_shape[0] // 2, ...] = 1.0 
            self.mask[kernel_shape[0] // 2, : kernel_shape[1] // 2, ...] = 1.0 
            if self.mask_type == "B":
                self.mask[kernel_shape[0] // 2, kernel_shape[1] // 2, ...] = 1.0 

        def call(self, inputs):
            self.conv.kernel.assign(self.conv.kernel * self.mask) 
            return self.conv(inputs)
    ```
*
