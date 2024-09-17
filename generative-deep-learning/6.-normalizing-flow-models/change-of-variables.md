# Change of Variables

* Suppose we have a probability distribution p(x) defined over a rectangle X in x1, x2
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>A probability distribution defined over two dimensions, shown in 2D (left) and 3D (right)</p></figcaption></figure>
* This function integrates to 1 over the domain of the distribution
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Let’s say that we want to <mark style="color:purple;background-color:purple;">**shift and scale this distribution**</mark> so that it is instead defined over a unit square Z.
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* This function is invertible
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
* If we want to transform our complex probability distribution over the data into a simpler distribution that we can sample from, we must ensure that it integrates to 1
* <mark style="color:purple;background-color:purple;">**We need to multiply the new probability distribution by a normalization factor that is equal to the relative change in area**</mark>
