# The Change of Variables Equation

* Single equation that describes the process for changing variables between and Z
*

    <figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
* But there are 2 major issues

1. <mark style="color:purple;background-color:purple;">Calculating the determinant of a high-dimensional matrix is computationally extremely expensive.</mark> This is completely impractical to implement in practice, as even small 32 × 32–pixel grayscale images have 1,024 dimensions
2. <mark style="color:purple;background-color:purple;">How we should go about calculating the invertible function f(x)</mark>. We could use a neural network to find some function f(x) but we cannot necessarily invert this network—neural networks only work in one direction
