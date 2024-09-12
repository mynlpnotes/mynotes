# The Two Moons Dataset

* Part of make\_moons function of sklearn
*

    <figure><img src="../../.gitbook/assets/image (10).png" alt="" width="300"><figcaption></figcaption></figure>
*

    ```python
    data = datasets.make_moons(3000, noise=0.05)[0].astype("float32") 
    norm = layers.Normalization()
    norm.adapt(data)
    normalized_data = norm(data)
    ```
