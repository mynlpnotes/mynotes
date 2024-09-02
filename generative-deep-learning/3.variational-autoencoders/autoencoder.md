# Autoencoder

* **Encoding:** Moving each to a location in the wardrobe
* **Decoder:** Taking a location in the wardrobe and attempting to re-create the item
*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
* Each location in the wardrobe is represented by two numbers (i.e., a 2D vector). For example, the trousers in Figure 3-2 are encoded to the point \[6.3, –0.9].&#x20;
* This vector is also known as an embedding because the encoder attempts to embed as much information into it as possible, so that the decoder can produce an accurate reconstruction.
* An autoencoder is simply a neural network that is trained to perform the task of encoding and decoding an item, such that the output from this process is as close to the original item as possible.&#x20;
* Crucially, it can be used as a generative model, because we can decode any point in the 2D space that we want (in particular, those that are not embeddings of original items) to produce a novel item
