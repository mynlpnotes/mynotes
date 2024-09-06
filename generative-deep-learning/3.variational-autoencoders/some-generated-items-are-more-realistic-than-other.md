# Some generated items are more realistic than other

Observations about the overall distribution of points in the latent space:

1. Some clothing <mark style="color:purple;background-color:purple;">**items are represented over a very small area and others over a much larger area.**</mark>
2. The distribution is not symmetrical about the point (0, 0), or bounded. For example, there are far more points with positive y-axis values than negative, and some points even extend to a y-axis value > 8.
3. There are <mark style="color:purple;background-color:purple;">**large gaps**</mark> between colors containing few points

Overlay the latent space with images of decoded points on a grid

*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

1. We can see that if we pick points uniformly in a bounded space that we define, we’re more likely to sample something that decodes to look like a bag (ID 8) than an ankle boot (ID 9) because the part of the latent space carved out for bags (orange) is larger than the ankle boot area (red)
2. It is not obvious how we should go about choosing a random point in the latent space, since the distribution of these points is undefined. Technically, we would be justified in choosing any point in the 2D plane! It’s not even guaranteed that points will be centered around (0, 0). This makes sampling from our latent space problematic
3. We can see holes in the latent space where none of the original images are encoded. For example, there are large white spaces at the edges of the domain—the autoencoder has no reason to ensure that points here are decoded to recognizable clothing items as very few images in the training set are encoded here

To solve this issues, we need to convert our autoencoder into a variational auto encoder
