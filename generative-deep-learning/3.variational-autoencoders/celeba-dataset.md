# CelebA - Dataset

* 2,00,000 colour images of celebrity faces each annotated with various labels
* Dataset is available on kaggle
* bash scripts/download\_kaggle\_data.sh jessicali9530 celeba-dataset
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

    **image\_dataset\_from\_directory:**
* We use the Keras function image\_dataset\_from\_directory to create a TensorFlow Dataset pointed at the directory where the images are stored
* This allows us to read batches of images into memory only when required (e.g., during training), so that we can work with large datasets and not worry about having to fit the entire dataset into memory.&#x20;
* It also resizes the images to 32 × 32, interpolating between pixel values

```python
train_data = utils.image_dataset_from_directory(
    "/app/data/celeba-dataset/img_align_celeba/img_align_celeba",
    labels=None,
    color_mode="rgb",
    image_size=(32, 32),
    batch_size=128,
    shuffle=True,
    seed=42,
    interpolation="bilinear",
)
```

**Pre-processing:**

```python
def preprocess(img):
    img = tf.cast(img, "float32") / 255.0
    return img

train = train_data.map(lambda x: preprocess(x))
```
