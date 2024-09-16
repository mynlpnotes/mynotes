# Change of Variables

* Suppose we have a probability distribution p(x) defined over a rectangle X in x1, x2
*

    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>A probability distribution defined over two dimensions, shown in 2D (left) and 3D (right)</p></figcaption></figure>
* This function integrates to 1 over the domain of the distribution
*

    <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
* Let’s say that we want to <mark style="color:purple;background-color:purple;">**shift and scale this distribution**</mark> so that it is instead defined over a unit square Z.
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* This function is invertible
*

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
* If we want to transform our complex probability distribution over the data into a simpler distribution that we can sample from, we must ensure that it integrates to 1
* <mark style="color:purple;background-color:purple;">**We need to multiply the new probability distribution by a normalization factor that is equal to the relative change in area**</mark>



* <mark style="color:purple;background-color:purple;">Encoder learns the transformations like scaling, shifting, and other adjustments to map the data from the latent space (simple distribution) to the data space (complex distribution).</mark>
* <mark style="color:purple;background-color:purple;">Decoder learns the inverse transformations to bring the data back from the complex data space to the simpler latent space.</mark>
* <mark style="color:purple;background-color:purple;">Change of variables ensures that the probabilities are adjusted properly during these transformations, making sure the mapping between encoder and decoder remains mathematically valid.</mark>
