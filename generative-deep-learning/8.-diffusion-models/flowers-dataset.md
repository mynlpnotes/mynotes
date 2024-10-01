# Flowers Dataset

* 8,000 color images of a variety of flowers
* Resize the images to 64 × 64 pixels, and scale the pixel values to the range \[0, 1]
* ```bash
  bash scripts/download_kaggle_data.sh nunenuh pytorch-challange-flower-dataset
  ```
* ```python
  train_data = utils.image_dataset_from_directory(
      "/app/data/pytorch-challange-flower-dataset/dataset",
      labels=None,
      image_size=(64, 64),
      batch_size=None,
      shuffle=True,
      seed=42,
      interpolation="bilinear",
  ) 

  def preprocess(img):
      img = tf.cast(img, "float32") / 255.0
      return img

  train = train_data.map(lambda x: preprocess(x)) 
  train = train.repeat(5) 
  train = train.batch(64, drop_remainder=True)
  ```
* Repeat the dataset five times to increase the epoch length and batch the data into groups of 64 images
*

    <figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
