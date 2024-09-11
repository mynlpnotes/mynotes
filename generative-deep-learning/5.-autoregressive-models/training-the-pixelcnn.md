# Training the PixelCNN

*

    ```python
    inputs = layers.Input(shape=(16, 16, 1)) 
    x = MaskedConv2D(mask_type="A"
                       , filters=128
                       , kernel_size=7
                       , activation="relu"
                       , padding="same")(inputs)

    for _ in range(5):
        x = ResidualBlock(filters=128)(x) 

    for _ in range(2):
        x = MaskedConv2D(
            mask_type="B",
            filters=128,
            kernel_size=1,
            strides=1,
            activation="relu",
            padding="valid",
        )(x) 

    out = layers.Conv2D(
        filters=4, kernel_size=1, strides=1, activation="softmax", padding="valid"
    )(x) 

    pixel_cnn = models.Model(inputs, out) 

    adam = optimizers.Adam(learning_rate=0.0005)
    pixel_cnn.compile(optimizer=adam, loss="sparse_categorical_crossentropy")

    pixel_cnn.fit(
        input_data
        , output_data
        , batch_size=128
        , epochs=150
    )
    ```
* The model Input is a grayscale image of size 16 × 16 × 1, with inputs scaled between 0 and 1
* The first Type A MaskedConv2D layer with a kernel size of 7 uses information from 24 pixels—21 pixels in the three rows above the focus pixel and 3 to the left (the focus pixel itself is not used
* Five ResidualBlock layer groups are stacked sequentially
* Two Type B MaskedConv2D layers with a kernel size of 1 act as Dense layers across the number of channels for each pixel
* The final Conv2D layer reduces the number of channels to four—the number of pixel levels for this example
* The Model is built to accept an image and output an image of the same dimensions
* Fit the model—input\_data is scaled in the range \[0, 1] (floats); output\_data is scaled in the range \[0, 3] (integers)
