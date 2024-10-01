# Encoder Decoder

#### 1. **No Encoder-Decoder Training in the Traditional Sense**:

* In diffusion models, there’s no explicit encoder-decoder structure like in autoencoders.
* <mark style="color:purple;background-color:purple;">**Encoding: The process of adding noise to the data step-by-step (forward diffusion) doesn’t involve training. It’s a predefined noise-adding process that gradually corrupts the data.**</mark>
* **Decoding**: The reverse process (denoising) is where the model, typically a neural network, is trained. The model learns to predict and remove the noise at each step, ultimately reconstructing the original data from the noisy version.

#### 2. **Training the Neural Network to Predict Noise**:

* <mark style="color:purple;background-color:purple;">**During the reverse process (decoding), the model’s task is to predict the noise added in each step of the forward diffusion process.**</mark>
* <mark style="color:purple;background-color:purple;">**The neural network is trained to minimize the difference between the predicted noise and the actual noise added at each step.**</mark>
* This effectively "denoises" the noisy image, step by step, to recover the original data.
