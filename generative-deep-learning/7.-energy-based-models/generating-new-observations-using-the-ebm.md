# Generating new observations using the EBM

* Generating new samples from the EBM is simply a case of running the Langevin sampler for a large number of steps, from a standing start (random noise)
*

    ```python
    start_imgs = np.random.uniform(size = (10, 32, 32, 1)) * 2 - 1
    gen_img = generate_samples(
        ebm.model,
        start_imgs,
        steps=1000,
        step_size=10,
        noise = 0.005,
        return_img_per_step=True,
    )
    ```
*

    <figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption><p>Examples produced by the Langevin sampler using the EBM model to direct the gradient descent</p></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption><p>Snapshots of an observation at different steps of the Langevin sampling process</p></figcaption></figure>
