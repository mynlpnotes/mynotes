# Decoder in Diffusion Models

1. **Input to the Decoder**:
   * The decoder receives the **final noisy image** ( x\_T ), which is generated after the forward diffusion process (i.e., after several steps of adding noise).
2. **Reverse Diffusion Process**:
   * The decoder works in **reverse**, progressively denoising the image step by step:
     * Starting with ( x\_T ) (final noisy image), it predicts the noise ( $$epsilon_T$$ε  ) that was added at step ( T ).
     * This predicted noise is subtracted from ( x\_T ), resulting in ( x\_{T-1} ), which is a slightly less noisy image.
     * This process continues for ( T -> T-1 -> T-2 .... -> x\_0 ) until a denoised image is obtained.
3. **Noise Prediction**:
   * The decoder is trained to **predict the noise** added at each step, rather than directly outputting the denoised image.
   * For each step ( t ), the model predicts the noise ( εt ), which is subtracted from the noisy image to recover a less noisy version of the image from step ( t-1 ).
4. **Step-by-Step Denoising**:
   * At each step, the model only removes **a small amount of noise**.
   * This makes the denoising task easier and more stable for the model because removing small amounts of noise is more manageable than removing all noise at once.
5. **Final Output**:
   * After multiple reverse steps, the model produces ( x\_0 ), which is the final denoised image that should resemble the original image.
