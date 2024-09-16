# Autoencoder Architecture

<mark style="color:purple;background-color:purple;">**Encoder:**</mark>&#x20;

* <mark style="color:purple;background-color:purple;">Network that compresses high-dimensional input data such as an image into a lower-dimensional embedding vector</mark>

<mark style="color:purple;background-color:purple;">**Decoder:**</mark>

* <mark style="color:purple;background-color:purple;">Network that decompresses a given embedding vector back to the original domain</mark>



* An input image is encoded to a latent embedding vector , which is then decoded back to the original pixel space
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* The autoencoder is trained to reconstruct an image, after it has passed through the encoder and back out through the decoder
* The embedding ( Z) is a compression of the original image into a lower-dimensional latent space
* In practice, the latent space of an autoencoder will usually have more than two dimensions in order to have more freedom to capture greater nuance in the images
