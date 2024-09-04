# β-VAE

* Includes a factor that weights the KL divergence to ensure that it is well balanced with the reconstruction loss
* If we weight the reconstruction loss too heavily, the KL loss will not have the desired regulatory effect and we will see the same problems that we experienced with the plain autoencoder
* If the KL divergence term is weighted too heavily, the KL divergence loss will dominate and the reconstructed images will be poor
* This weighting term is one of the parameters to tune when you’re training your VAE
