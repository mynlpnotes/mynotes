# Morphing Between Faces

* Imagine two points in the latent space, A and B, that represent two images.&#x20;
* If you started at point A and walked toward point B in a straight line, decoding each point on the line as you went, you would see a gradual transition from the starting face to the end face
* ```
  z_new = z_A * (1- alpha) + z_B * alpha
  ```
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
