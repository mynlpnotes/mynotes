# CelebA - Training

{% embed url="https://github.com/davidADSP/Generative_Deep_Learning_2nd_Edition/blob/main/notebooks/03_vae/03_vae_faces/vae_faces.ipynb" %}

* 3 input channels instead of 1, This means we need to change the number of channels in the final convolutional transpose layer of the decoder to 3.
* We shall be using a latent space with 200 dimensions instead of 2
* There are batch normalization layers after each convolutional layer to stabilize training. Even though each batch takes a longer time to run, the number of batches required to reach the same loss is greatly reduced
* We increase the factor for the KL divergence to 2,000. This is a parameter that requires tuning; for this dataset and architecture this value was found to generate good results

<pre class="language-python"><code class="lang-python">## Encoder:
#Layer (type)	           Output shape	         Param #	      Connected to
#InputLayer (input)        (None, 32, 32, 3)     0                  []
#Conv2D (conv2d_1)         (None, 16, 16, 128)   3,584              [input]
#BatchNormalization (bn_1) (None, 16, 16, 128)   512                [conv2d_1]
#LeakyReLU (lr_1)          (None, 16, 16, 128)   0                  [bn_1]
#Conv2D (conv2d_2)         (None, 8, 8, 128)     147,584            [lr_1]
#BatchNormalization (bn_2) (None, 8, 8, 128)     512                [conv2d_2]
#LeakyReLU (lr_2)          (None, 8, 8, 128)     0                  [bn_2]
#Conv2D (conv2d_3)         (None, 4, 4, 128)     147,584            [lr_2]
#BatchNormalization (bn_3) (None, 4, 4, 128)     512                [conv2d_3]
#LeakyReLU (lr_3)          (None, 4, 4, 128)     0                  [bn_3]
#Conv2D (conv2d_4)         (None, 2, 2, 128)     147,584            [lr_3]
#BatchNormalization (bn_4) (None, 2, 2, 128)     512                [conv2d_4]
#LeakyReLU (lr_4)          (None, 2, 2, 128)     0                  [bn_4]
#Flatten (flatten)         (None, 512)           0                  [lr_4]
#Dense (z_mean)            (None, 200)           102,600            [flatten]
#Dense (z_log_var)         (None, 200)           102,600            [flatten]
#Sampling (z)              (None, 200)           0                  [z_mean, z_log_var]
#Total params                                    653,584
#Trainable params                                652,560
#Non-trainable params                            1,024

## Decoder:
<strong>#Layer (type)	              Output shape	        Param #
</strong>#InputLayer                   (None, 200)               0
#Dense                        (None, 512)               102,912
#BatchNormalization           (None, 512)               2,048
#LeakyReLu                    (None, 512)               0
#Reshape                      (None, 2, 2, 128)         0
#Conv2DTranspose              (None, 4, 4, 128)         147,584
#BatchNormalization           (None, 4, 4, 128)         512
#LeakyReLU                    (None, 4, 4, 128)         0
#Conv2DTranspose              (None, 8, 8, 128)         147,584
#BatchNormalization           (None, 8, 8, 128)         512
#LeakyReLu                    (None, 8, 8, 128)         0
#Conv2DTranspose              (None, 16, 16, 128)       147,584
#BatchNormalization           (None, 16, 16, 128)       512
#LeakyReLU                    (None, 16, 16, 128)       0
#Conv2DTranspose              (None, 32, 32, 128)       147,584
#BatchNormalization           (None, 32, 32, 128)       512
#LeakyReLU                    (None, 32, 32, 128)       0
#Conv2DTranspose              (None, 32, 32, 3)         3,459
#Total params                                           700,803
#Trainable params                                       698,755
#Non-trainable params                                   2,048
</code></pre>
