# The Energy Function

* The energy function is a neural network with parameters that can transform an input image into a scalar value
* We use swish activation function
* The network is a set of stacked `Conv2D` layers that gradually reduce the size of the image while increasing the number of channels.&#x20;
* The final layer is a single fully connected unit with linear activation, so the network can output values in the range (-∞, ∞)
*

    ```python
    ebm_input = layers.Input(shape=(32, 32, 1))
    x = layers.Conv2D(
        16, kernel_size=5, strides=2, padding="same", activation = activations.swish
    )(ebm_input) 
    x = layers.Conv2D(
        32, kernel_size=3, strides=2, padding="same", activation = activations.swish
    )(x)
    x = layers.Conv2D(
        64, kernel_size=3, strides=2, padding="same", activation = activations.swish
    )(x)
    x = layers.Conv2D(
        64, kernel_size=3, strides=2, padding="same", activation = activations.swish
    )(x)
    x = layers.Flatten()(x)
    x = layers.Dense(64, activation = activations.swish)(x)
    ebm_output = layers.Dense(1)(x) 
    model = models.Model(ebm_input, ebm_output)
    ```
