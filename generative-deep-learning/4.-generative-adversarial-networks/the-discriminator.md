# The Discriminator

* This is a supervised image classification problem
* We use stacked convolutional layers, with a single output node
*

    ```python
    discriminator_input = layers.Input(shape=(64, 64, 1)) 
    x = layers.Conv2D(64, kernel_size=4, strides=2, padding="same", use_bias = False)(
        discriminator_input
    ) 
    x = layers.LeakyReLU(0.2)(x)
    x = layers.Dropout(0.3)(x)
    x = layers.Conv2D(
        128, kernel_size=4, strides=2, padding="same", use_bias = False
    )(x)
    x = layers.BatchNormalization(momentum = 0.9)(x)
    x = layers.LeakyReLU(0.2)(x)
    x = layers.Dropout(0.3)(x)
    x = layers.Conv2D(
        256, kernel_size=4, strides=2, padding="same", use_bias = False
    )(x)
    x = layers.BatchNormalization(momentum = 0.9)(x)
    x = layers.LeakyReLU(0.2)(x)
    x = layers.Dropout(0.3)(x)
    x = layers.Conv2D(
        512, kernel_size=4, strides=2, padding="same", use_bias = False
    )(x)
    x = layers.BatchNormalization(momentum = 0.9)(x)
    x = layers.LeakyReLU(0.2)(x)
    x = layers.Dropout(0.3)(x)
    x = layers.Conv2D(
        1,
        kernel_size=4,
        strides=1,
        padding="valid",
        use_bias = False,
        activation = 'sigmoid'
    )(x)
    discriminator_output = layers.Flatten()(x) 
    #Layer (type)	           Output shape	                 Param #
    #InputLayer                (None, 64, 64, 1)             0
    #Conv2D                    (None, 32, 32, 64)            1,024
    #LeakyReLU                 (None, 32, 32, 64)            0
    #Dropout                   (None, 32, 32, 64)            0
    #Conv2D                    (None, 16, 16, 128)           131,072
    #BatchNormalization        (None, 16, 16, 128)           512
    #LeakyReLU                 (None, 16, 16, 128)           0
    #Dropout                   (None, 16, 16, 128)           0
    #Conv2D                    (None, 8, 8, 256)             524,288
    #BatchNormalization        (None, 8, 8, 256)             1,024
    #LeakyReLU                 (None, 8, 8, 256)             0
    #Dropout                   (None, 8, 8, 256)             0
    #Conv2D                    (None, 4, 4, 512)             2,097,152
    #BatchNormalization        (None, 4, 4, 512)             2,048
    #LeakyReLU                 (None, 4, 4, 512)             0
    #Dropout                   (None, 4, 4, 512)             0
    #Conv2D                    (None, 1, 1, 1)               8,192
    #Flatten                   (None, 1)                     0
    #Total params                                            2,765,312
    #Trainable params                                        2,763,520
    #Non-trainable params                                    1,792

    discriminator = models.Model(discriminator_input, discriminator_output)
    ```
