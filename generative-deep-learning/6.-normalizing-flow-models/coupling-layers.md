# Coupling Layers

* Produces a scale and translation factor for each element of its input.&#x20;
* In other words, it produces two tensors that are exactly the same size as the input, one for the scale factor and one for the translation factor
*

    <figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>
* To build a custom `Coupling` layer, we can stack `Dense` layers to create the scale output and a different set of `Dense` layers to create the translation output
*

    ```python
    def Coupling():
        input_layer = layers.Input(shape=2) 

        s_layer_1 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(input_layer) 
        s_layer_2 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(s_layer_1)
        s_layer_3 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(s_layer_2)
        s_layer_4 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(s_layer_3)
        s_layer_5 = layers.Dense(
            2, activation="tanh", kernel_regularizer=regularizers.l2(0.01)
        )(s_layer_4) 

        t_layer_1 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(input_layer) 
        t_layer_2 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(t_layer_1)
        t_layer_3 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(t_layer_2)
        t_layer_4 = layers.Dense(
            256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
        )(t_layer_3)
        t_layer_5 = layers.Dense(
            2, activation="linear", kernel_regularizer=regularizers.l2(0.01)
        )(t_layer_4) 

        return models.Model(inputs=input_layer, outputs=[s_layer_5, t_layer_5])
    ```
* The input to the `Coupling` layer block in our example has two dimensions.
* The scaling stream is a stack of `Dense` layers of size 256.
* The final scaling layer is of size 2 and has `tanh` activation
* The translation stream is a stack of `Dense` layers of size 256
* The final translation layer is of size 2 and has `linear` activation
* The `Coupling` layer is constructed as a Keras `Model` with two outputs (the scaling and translation factors)
