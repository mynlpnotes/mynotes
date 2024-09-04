# Training Auto Encoder - Fashion MNIST Example

{% embed url="https://github.com/davidADSP/Generative_Deep_Learning_2nd_Edition/blob/main/notebooks/03_vae/01_autoencoder/autoencoder.ipynb" %}

* 28X28 pixels
* In Encoder, we use a stride of 2 to halve the size of the output of each layer, while increasing the number of channels
* In Decoder, we use convolutional transpose layer
* We use mirror image of encoder
* By stacking these layers, we can gradually expand the size of each layer, using strides of 2, until we get back to the original image dimension of 32 × 32
* Model takes an image and passes it through the encoder and back out through the decoder to generate a reconstruction of the original image

```python
# Loading the data
from tensorflow.keras import datasets
(x_train,y_train), (x_test,y_test) = datasets.fashion_mnist.load_data()

# Preprocess the image
# 1. Add padding to make it 32X32
# 2. Scaling to convert pixel values from 0 to 255 -> 0 to 1
def preprocess(imgs):
    imgs = imgs.astype("float32") / 255.0
    imgs = np.pad(imgs, ((0, 0), (2, 2), (2, 2)), constant_values=0.0)
    imgs = np.expand_dims(imgs, -1)
    return imgs

x_train = preprocess(x_train)
x_test = preprocess(x_test)

# Encoder
encoder_input = layers.Input(
    shape=(IMAGE_SIZE, IMAGE_SIZE, CHANNELS), name="encoder_input"
)
x = layers.Conv2D(32, (3, 3), strides=2, activation="relu", padding="same")(
    encoder_input
)
x = layers.Conv2D(64, (3, 3), strides=2, activation="relu", padding="same")(x)
x = layers.Conv2D(128, (3, 3), strides=2, activation="relu", padding="same")(x)
shape_before_flattening = K.int_shape(x)[1:]  # the decoder will need this!

x = layers.Flatten()(x)
encoder_output = layers.Dense(EMBEDDING_DIM, name="encoder_output")(x)

encoder = models.Model(encoder_input, encoder_output)
encoder.summary()
#Layer (type)	Output shape	     Param #
#InputLayer     (None, 32, 32, 1)    0
#Conv2D         (None, 16, 16, 32)   320
#Conv2D         (None, 8, 8, 64)     18,496
#Conv2D         (None, 4, 4, 128)    73,856
#Flatten        (None, 2048)         0
#Dense          (None, 2)            4,098
#Total params                        96,770
#Trainable params                    96,770
#Non-trainable params                0

# Decoder
decoder_input = layers.Input(shape=(2,), name="decoder_input") 
x = layers.Dense(np.prod(shape_before_flattening))(decoder_input) 
x = layers.Reshape(shape_before_flattening)(x) 
x = layers.Conv2DTranspose(
    128, (3, 3), strides=2, activation = 'relu', padding="same"
)(x) 
x = layers.Conv2DTranspose(
    64, (3, 3), strides=2, activation = 'relu', padding="same"
)(x)
x = layers.Conv2DTranspose(
    32, (3, 3), strides=2, activation = 'relu', padding="same"
)(x)
decoder_output = layers.Conv2D(
    1,
    (3, 3),
    strides = 1,
    activation="sigmoid",
    padding="same",
    name="decoder_output"
)(x)
decoder = models.Model(decoder_input, decoder_output) 
#Layer (type)	  Output shape	    Param #  
#InputLayer       (None, 2)           0
#Dense            (None, 2048)        6,144
#Reshape          (None, 4, 4, 128)   0
#Conv2DTranspose  (None, 8, 8, 128)   147,584
#Conv2DTranspose  (None, 16, 16, 64)  73,792
#Conv2DTranspose  (None, 32, 32, 32)  18,464
#Conv2D           (None, 32, 32, 1)   289
#Total params                         246,273
#Trainable params                     246,273
#Non-trainable params                 0

# Joining the encoder with decoder
autoencoder = Model(encoder_input, decoder(encoder_output))

# Compile the autoencoder
autoencoder.compile(optimizer="adam", loss="binary_crossentropy")

# Training the autoencoder
autoencoder.fit(
    x_train,
    x_train,
    epochs=5,
    batch_size=100,
    shuffle=True,
    validation_data=(x_test, x_test),
)

# Reconstructing images
example_images = x_test[:5000]
predictions = autoencoder.predict(example_images)

```

*

    <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>Output of prediction</p></figcaption></figure>

