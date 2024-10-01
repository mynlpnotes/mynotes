# EMA

#### **Exponential Moving Average (EMA) in Neural Networks**

1. **What is EMA?**
   * A technique to maintain a running average of model parameters (weights) during training.
   * More importance is given to recent updates compared to older ones, hence "exponential."
2. **Why use EMA?**
   * It smooths out fluctuations in model weights caused by noisy updates.
   * Helps in stabilizing the model and improving generalization on unseen data.
3. **How does EMA update the weights?**
   * The update formula is: θEMA = α.θEMA + (1 - α) .θcurrent
   * α is the decay rate, typically between 0.999 and 0.9999, which controls the balance between past and current weights.
4. **Example**:
   * If the current weight updates from 1.0 to 1.2, 1.4, and 1.1, and ( \alpha = 0.9 ):
     * Step 1: θEMA = 1.02 )
     * Step 2: θEMA = 1.058 )
     * Step 3: θEMA = 1.0622 )
   * EMA stabilizes the weight values over time.
5. **When is EMA used?**
   * **During Training**: Both the model's current and EMA weights are updated.
   * **During Inference (Testing)**: The model uses the EMA weights for predictions due to their stability.
6. **EMA in Diffusion Models**:
   * EMA ensures the reverse diffusion process (denoising) is more reliable and stable.
   * Using EMA during inference in diffusion models helps generate better-quality samples.
