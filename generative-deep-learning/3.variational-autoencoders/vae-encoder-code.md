# VAE - Encoder - Code

* We create a new type of Sampling layer that will allow us to sample from the distribution defined by z\_mean and z\_log\_var
* z\_means and z\_log\_var layer learns to calculate mean and log of variance

```python
class Sampling(layers.Layer): 1
    def call(self, inputs):
        z_mean, z_log_var = inputs
        batch = tf.shape(z_mean)[0]
        dim = tf.shape(z_mean)[1]
        epsilon = K.random_normal(shape=(batch, dim))
        return z_mean + tf.exp(0.5 * z_log_var) * epsilon

encoder_input = layers.Input(
    shape=(32, 32, 1), name="encoder_input"
)
x = layers.Conv2D(32, (3, 3), strides=2, activation="relu", padding="same")(
    encoder_input
)
x = layers.Conv2D(64, (3, 3), strides=2, activation="relu", padding="same")(x)
x = layers.Conv2D(128, (3, 3), strides=2, activation="relu", padding="same")(x)
shape_before_flattening = K.int_shape(x)[1:]

x = layers.Flatten()(x)
z_mean = layers.Dense(2, name="z_mean")(x) 
z_log_var = layers.Dense(2, name="z_log_var")(x)
z = Sampling()([z_mean, z_log_var]) 

encoder = models.Model(encoder_input, [z_mean, z_log_var, z], name="encoder")
#Layer (type)	       Output shape        	Param #	       Connected to
#InputLayer (input)    (None, 32, 32, 1)        0              []
#Conv2D (conv2d_1)     (None, 16, 16, 32)       320            [input]
#Conv2D (conv2d_2)     (None, 8, 8, 64)         18,496         [conv2d_1]
#Conv2D (conv2d_3)     (None, 4, 4, 128)        73,856         [conv2d_2]
#Flatten (flatten)     (None, 2048)             0              [conv2d_3]
#Dense (z_mean)        (None, 2)                4,098          [flatten]
#Dense (z_log_var)     (None, 2)                4,098          [flatten]
#Sampling (z)          (None, 2)                0              [z_mean, z_log_var]
#Total params                                   100,868
#Trainable params                               100,868
#Non-trainable params                           0
```
