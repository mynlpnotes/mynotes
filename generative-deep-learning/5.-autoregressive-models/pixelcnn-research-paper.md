# PixelCNN Research Paper

**Motivation:**

* Generate images pixel-by-pixel, capturing the complex dependencies between pixels
* Unlike traditional generative models that try to generate the entire image at once, PixelCNN models the conditional distribution of each pixel based on previously generated pixels.

**Model Architecture:**

* PixelCNN uses a stack of **convolutional layers** with **masked convolutions** to generate images one pixel at a time

**Masked Convolutions:**

* To ensure that the network only uses past and present pixel values

**Pixel Prediction:**

* PixelCNN generates an image by predicting each pixel’s value as a probability distribution over possible pixel values (e.g., different colors or intensities).
* For each pixel, the model produces a probability distribution across all possible values.
* A pixel value is then sampled from this distribution to form the image progressively.

Training:

* During training, PixelCNN learns to generate images by predicting each pixel’s value conditioned on previously seen pixels.
* **Training Process:** The model is trained on real images where it learns to predict each pixel’s value from the pixels that have been generated before it.
* **Objective Function:** The model aims to maximize the likelihood of the true pixel values in the training images, meaning it tries to adjust its parameters so that the predicted pixel values closely match the actual values.
* **Loss Function:** The loss function used is typically the **negative log-likelihood** of the pixel values, which measures how well the predicted probabilities match the actual pixel values.

