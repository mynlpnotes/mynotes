# The MNIST Dataset

* Grayscale images of handwritten digits
*

    <figure><img src="../../.gitbook/assets/image (1).png" alt="" width="300"><figcaption></figcaption></figure>
*

    ```python
    from tensorflow.keras import datasets
    (x_train, _), (x_test, _) = datasets.mnist.load_data()
    ```
* We’ll scale the pixel values to the range \[-1, 1] and add some padding to make the images 32 × 32 pixels in size
*

    ```python
    def preprocess(imgs):
        imgs = (imgs.astype("float32") - 127.5) / 127.5
        imgs = np.pad(imgs , ((0,0), (2,2), (2,2)), constant_values= -1.0)
        imgs = np.expand_dims(imgs, -1)
        return imgs

    x_train = preprocess(x_train)
    x_test = preprocess(x_test)
    x_train = tf.data.Dataset.from_tensor_slices(x_train).batch(128)
    x_test = tf.data.Dataset.from_tensor_slices(x_test).batch(128)
    ```
