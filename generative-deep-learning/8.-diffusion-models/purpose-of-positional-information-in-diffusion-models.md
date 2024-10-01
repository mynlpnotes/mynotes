# Purpose of Positional Information in Diffusion Models

* During forward and reverse infusion, the position of each features
* **U-Net architecture** is designed to capture both high-level and low-level image details. However, without explicit positional information, U-Net doesn’t know **where** features are in the image—only their features
* By adding **sinusoidal positional embeddings** to each pixel or feature, we give the model clear positional cues, helping it understand the **layout** of the image even after noisy transformations
