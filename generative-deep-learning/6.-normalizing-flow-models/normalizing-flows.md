# Normalizing Flows

* The motivation is similar to that of VAE
* But in VAE the encoder and decoder are two completely distinct NN
* In a normalizing flow model, the <mark style="color:purple;background-color:purple;">**decoding function is designed to be the exact inverse of the encoding function**</mark>
* Neural networks are not by default invertible functions
* However, NN are not be default inversible functions
* For this we need to understand change of variables
