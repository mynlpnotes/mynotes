# CGAN Architecture

* Here we want to explicitly whether we want to generate an image with blond hair or not
*   This label is explicitly provided in dataset

    <figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>
* The key difference between a standard GAN and a CGAN is that in a CGAN we pass in extra information to the generator and critic relating to the label.&#x20;
* In the generator, this is simply appended to the latent space sample as a one-hot encoded vector.
* In the critic, we add the label information as extra channels to the RGB image. We do this by repeating the one-hot encoded vector to fill the same shape as the input images
* CGANs work because the critic now has access to extra information regarding the content of the image, so the generator must ensure that its output agrees with the provided label, in order to keep fooling the critic.&#x20;
* If the generator produced perfect images that disagreed with the image label the critic would be able to tell that they were fake simply because the images and labels did not match
*

    ```python
    critic_input = layers.Input(shape=(64, 64, 3)) 
    label_input = layers.Input(shape=(64, 64, 2))
    x = layers.Concatenate(axis = -1)([critic_input, label_input])
    ...
    generator_input = layers.Input(shape=(32,)) 
    label_input = layers.Input(shape=(2,))
    x = layers.Concatenate(axis = -1)([generator_input, label_input])
    x = layers.Reshape((1,1, 34))(x)
    ```
