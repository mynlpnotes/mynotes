# Coupling Layers

* <mark style="color:purple;background-color:purple;">**Produces a scale and translation factor for each element of its input.**</mark>&#x20;
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
* Since in moon dataset, every datapoint is of 2 dimension, so we using 2 here
* <mark style="color:purple;background-color:purple;">**If we had 1000 images of 32X32, then input\_dim will be 32X32 and each 1000 images will be mapped to a point on the normal distribution**</mark>
* The scaling stream is a stack of `Dense` layers of size 256.
* The final scaling layer is of size 2 and has `tanh` activation
* <mark style="color:purple;background-color:purple;">**The**</mark><mark style="color:purple;background-color:purple;">** **</mark><mark style="color:purple;background-color:purple;">**`tanh`**</mark><mark style="color:purple;background-color:purple;">** **</mark><mark style="color:purple;background-color:purple;">**activation function is used in the scaling function to ensure that the scaling factors are constrained within a specific range**</mark>
* The translation stream is a stack of `Dense` layers of size 256
* The final translation layer is of size 2 and has `linear` activation
* <mark style="color:purple;background-color:purple;">**The**</mark><mark style="color:purple;background-color:purple;">** **</mark><mark style="color:purple;background-color:purple;">**`linear`**</mark><mark style="color:purple;background-color:purple;">** **</mark><mark style="color:purple;background-color:purple;">**activation function is used in the translation function to allow the transformation to take any value, providing more flexibilit**</mark>
* The `Coupling` layer is constructed as a Keras `Model` with two outputs (the scaling and translation factors)
