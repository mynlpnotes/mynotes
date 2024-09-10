# Analysis of the CGAN

* We can control the CGAN output by passing a particular one-hot encoded label into the input of the generator.&#x20;
* For example, to generate a face with nonblond hair, we pass in the vector \[1, 0].&#x20;
* To generate a face with blond hair, we pass in the vector \[0, 1]
* It is clear that the CGAN has learned to use the label vector to control only the hair color attribute of the images.&#x20;
* It is impressive that the rest of the image barely changes—this is proof that GANs are able to organize points in the latent space in such a way that individual features can be decoupled from each other
*

    <figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
* If labels are available for your dataset, it is generally a good idea to include them as input to your GAN even if you do not necessarily need to condition the generated output on the label, as they tend to improve the quality of images generated. You can think of the labels as just a highly informative extension to the pixel input.
