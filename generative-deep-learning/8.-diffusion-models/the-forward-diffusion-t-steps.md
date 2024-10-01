# The Forward Diffusion - t steps

* **Forward Diffusion Process**:&#x20;
  * The goal is to gradually add noise to the original data ( x\_0 ) over ( T ) time steps.
* **Mathematical Representation**:
  * At each step ( t ), the data is transformed as:  $$x_t = \sqrt{\alpha_t} x_0 + \sqrt{1 - \alpha_t} \epsilon$$&#x20;
  * Here, $$( \epsilon )$$ is Gaussian noise sampled from $$( \mathcal{N}(0, I) )$$.
* **Defining  Values**:
  * Using a linear schedule for ( T = 3 ):
    * $$( \alpha_0 = 1 )$$
    * $$( \alpha_1 = 1 - \frac{1}{3} \approx 0.67 )$$
    * $$( \alpha_2 = 1 - \frac{2}{3} \approx 0.33 )$$
    * $$( \alpha_3 = 1 - \frac{3}{3} = 0 )$$
* **Noise Addition for Each Step**:
  * **Step 0 (t = 0)**:
    * $$( x_0 = x_0 )$$ (No noise added yet)
  * **Step 1 (t = 1)**:
    * Noise is added: $$[ x_1 = \sqrt{0.67} x_0 + \sqrt{0.33} \epsilon_1 ]$$
  * **Step 2 (t = 2)**:
    * More noise is added: $$[ x_2 = \sqrt{0.33} x_0 + \sqrt{0.67} \epsilon_2 ]$$
  * **Step 3 (t = 3)**:
    * The data is now completely transformed into noise: $$[ x_3 = 0 \cdot x_0 + \sqrt{1} \epsilon_3 = \epsilon_3 ]$$
* **Summary of Noise Addition**:
  * At each step, the contribution of $$( x_0 )$$ decreases while the contribution of the Gaussian noise $$( \epsilon )$$ increases.
  * By the final step, the data has been completely converted into noise.
