# Diffusion Schedules

* Different βt at each timestep
* How this value changes with t is known as diffusion schedule
* Linear diffusion schedule for βt—that is, βt increases linearly with t, from β1= 0.0001 to β2= 0.02
* This ensures that in the early stages of the noising process we take smaller noising steps than in the later stages, when the image is already very noisy
* ```python
  def linear_diffusion_schedule(diffusion_times):
      min_rate = 0.0001
      max_rate = 0.02
      betas = min_rate + tf.convert_to_tensor(diffusion_times) * (max_rate - min_rate)
      alphas = 1 - betas
      alpha_bars = tf.math.cumprod(alphas)
      signal_rates = alpha_bars
      noise_rates = 1 - alpha_bars
      return noise_rates, signal_rates

  T = 1000
  diffusion_times = [x/T for x in range(T)] 
  linear_noise_rates, linear_signal_rates = linear_diffusion_schedule(
      diffusion_times
  )
  ```
* There are other schedules also like cosine schedule
