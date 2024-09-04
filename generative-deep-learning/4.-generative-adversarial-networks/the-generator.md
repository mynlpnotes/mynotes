# The Generator

* The input to the generator will be a vector drawn from a multivariate standard normal distribution
* The output is an image of the same size as an image in the original training data
*

    ```python
    generator_input = layers.Input(shape=(100,)) 
    x = layers.Reshape((1, 1, 100))(generator_input) 
    x = layers.Conv2DTranspose(
        512, kernel_size=4, strides=1, padding="valid", use_bias = False
    )(x) 
    x = layers.BatchNormalization(momentum=0.9)(x)
    x = layers.LeakyReLU(0.2)(x)
    x = layers.Conv2DTranspose(
        256, kernel_size=4, strides=2, padding="same", use_bias = False
    )(x)
    x = layers.BatchNormalization(momentum=0.9)(x)
    x = layers.LeakyReLU(0.2)(x)
    x = layers.Conv2DTranspose(
        128, kernel_size=4, strides=2, padding="same", use_bias = False
    )(x)
    x = layers.BatchNormalization(momentum=0.9)(x)
    x = layers.LeakyReLU(0.2)(x)
    x = layers.Conv2DTranspose(
        64, kernel_size=4, strides=2, padding="same", use_bias = False
    )(x)
    x = layers.BatchNormalization(momentum=0.9)(x)
    x = layers.LeakyReLU(0.2)(x)
    generator_output = layers.Conv2DTranspose(
        1,
        kernel_size=4,
        strides=2,
        padding="same",
        use_bias = False,
        activation = 'tanh'
    )(x) 
    generator = models.Model(generator_input, generator_output)
    #Layer (type)	            Output shape	       Param #
    #InputLayer                 (None, 100)                0
    #Reshape                    (None, 1, 1, 100)          0
    #Conv2DTranspose            (None, 4, 4, 512)          819,200
    #BatchNormalization         (None, 4, 4, 512)          2,048
    #ReLU                       (None, 4, 4, 512)          0
    #Conv2DTranspose            (None, 8, 8, 256)          2,097,152
    #BatchNormalization         (None, 8, 8, 256)          1,024
    #ReLU                       (None, 8, 8, 256)          0
    #Conv2DTranspose            (None, 16, 16, 128)        524,288
    #BatchNormalization         (None, 16, 16, 128)        512
    #ReLU                       (None, 16, 16, 128)        0
    #Conv2DTranspose            (None, 32, 32, 64)         131,072
    #BatchNormalization         (None, 32, 32, 64)         256
    #ReLU                       (None, 32, 32, 64)         0
    #Conv2DTranspose            (None, 64, 64, 1)          1,024
    #Total params                                          3,576,576
    #Trainable params                                      3,574,656
    #Non-trainable params                                  1,920
    ```

