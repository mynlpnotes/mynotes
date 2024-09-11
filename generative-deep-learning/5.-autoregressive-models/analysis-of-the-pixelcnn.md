# Analysis of the PixelCNN

* We can train on Fashion-MNIST dataset
* To generate new images, we need to ask the model to predict the next pixel given all preceding pixels, one pixel at a time
* For a 32 × 32 grayscale image, we need to make 1,024 predictions sequentially using the model, compared to the single prediction that we need to make for a VAE.
* Thats why we use 16X16 to speed up the generation of new images
*

    ```python
    class ImageGenerator(callbacks.Callback):
        def __init__(self, num_img):
            self.num_img = num_img

        def sample_from(self, probs, temperature):
            probs = probs ** (1 / temperature)
            probs = probs / np.sum(probs)
            return np.random.choice(len(probs), p=probs)

        def generate(self, temperature):
            generated_images = np.zeros(
                shape=(self.num_img,) + (pixel_cnn.input_shape)[1:]
            ) 
            batch, rows, cols, channels = generated_images.shape

            for row in range(rows):
                for col in range(cols):
                    for channel in range(channels):
                        probs = self.model.predict(generated_images)[
                            :, row, col, :
                        ] 
                        generated_images[:, row, col, channel] = [
                            self.sample_from(x, temperature) for x in probs
                        ] 
                        generated_images[:, row, col, channel] /= 4 
            return generated_images

        def on_epoch_end(self, epoch, logs=None):
            generated_images = self.generate(temperature = 1.0)
            display(
                generated_images,
                save_to = "./output/generated_img_%03d.png" % (epoch)
            s)

    img_generator_callback = ImageGenerator(num_img=10)
    ```
* Start with a batch of empty images (all zeros)
* Loop over the rows, columns, and channels of the current image, predicting the distribution of the next pixel value
* Sample a pixel level from the predicted distribution (for our example, a level in the range \[0, 3])
* Convert the pixel level to the range \[0, 1] and overwrite the pixel value in the current image, ready for the next iteration of the loop
*

    <figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
