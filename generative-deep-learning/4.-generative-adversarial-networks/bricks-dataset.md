# Bricks Dataset

* 40,000 photographic images of 50 different toy bricks, taken from multiple angles
* The original data is scaled in the range \[0, 255] to denote the pixel intensity.&#x20;
* When training GANs we rescale the data to the range \[–1, 1] so that we can use the tanh activation function on the final layer of the generator, which tends to provide stronger gradients than the sigmoid function
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* ```bash
  bash scripts/download_kaggle_data.sh joosthazelzet lego-brick-images
  ```

```python
train_data = utils.image_dataset_from_directory(
    "/app/data/lego-brick-images/dataset/",
    labels=None,
    color_mode="grayscale",
    image_size=(64, 64),
    batch_size=128,
    shuffle=True,
    seed=42,
    interpolation="bilinear",
)
```

```python
def preprocess(img):
    img = (tf.cast(img, "float32") - 127.5) / 127.5
    return img

train = train_data.map(lambda x: preprocess(x))
```
