# Upsampling vs Conv2DTranspose

* An alternative to using `Conv2DTranspose` layers is to instead use an `UpSampling2D` layer followed by a normal `Conv2D` layer with stride 1
*

    ```
    x = layers.UpSampling2D(size = 2)(x)
    x = layers.Conv2D(256, kernel_size=4, strides=1, padding="same")(x)
    ```
* The UsSampling2D layer simply repeats each row and column of its input in order to double the size.&#x20;
* The Conv2D layer with stride 1 then performs the convolution operation. It is a similar idea to convolutional transpose, but instead of filling the gaps between pixels with zeros, upsampling just repeats the existing pixel values
* It has been shown that the Conv2DTranspose method can lead to _artifacts_, or small checkerboard patterns in the output image
*

    <figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Both of these methods—UpSampling2D + Conv2D and Conv2DTranspose—are acceptable ways to transform back to the original image domain.&#x20;
* It really is a case of testing both methods in your own problem setting and seeing which produces better results.
