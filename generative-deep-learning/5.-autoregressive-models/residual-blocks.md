# Residual Blocks

* A residual block is a set of layers where the output is added to the input before being passed on to the rest of the network
*

    <figure><img src="../../.gitbook/assets/image (12).png" alt="" width="279"><figcaption></figcaption></figure>
*

    ```python
    class ResidualBlock(layers.Layer):
        def __init__(self, filters, **kwargs):
            super(ResidualBlock, self).__init__(**kwargs)
            self.conv1 = layers.Conv2D(
                filters=filters // 2, kernel_size=1, activation="relu"
            ) 
            self.pixel_conv = MaskedConv2D(
                mask_type="B",
                filters=filters // 2,
                kernel_size=3,
                activation="relu",
                padding="same",
            ) 
            self.conv2 = layers.Conv2D(
                filters=filters, kernel_size=1, activation="relu"
            ) 

        def call(self, inputs):
            x = self.conv1(inputs)
            x = self.pixel_conv(x)
            x = self.conv2(x)
            return layers.add([inputs, x])
    ```
*
