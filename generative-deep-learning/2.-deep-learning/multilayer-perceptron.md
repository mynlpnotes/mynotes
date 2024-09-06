# Multilayer Perceptron



{% @github-files/github-code-block url="https://github.com/davidADSP/Generative_Deep_Learning_2nd_Edition/blob/main/notebooks/02_deeplearning/01_mlp/mlp.ipynb" %}

* Multilayer perceptron is a Discriminative model&#x20;

**Dataset:**

* CIFAR-10 dataset
* 60,000 images of 32X32
* Classes - Airplane, Automobile, Bird, Cat, Deer, Dog....

```python
## Prepare the Data
# Scale the data
# One hot coding for the target value
# Shape of x_train will be [5000,32,32,3]
# Here 3 is no. of channels
x_train = x_train.astype("float32") / 255.0
x_test = x_test.astype("float32") / 255.0

y_train = utils.to_categorical(y_train, NUM_CLASSES)
y_test = utils.to_categorical(y_test, NUM_CLASSES)

## Building the model
from tensorflow.keras import layers, models

input_layer = layers.Input(shape=(32, 32, 3))
x = layers.Flatten()(input_layer)
x = layers.Dense(units=200, activation = 'relu')(x)
x = layers.Dense(units=150, activation = 'relu')(x)
output_layer = layers.Dense(units=10, activation = 'softmax')(x)
model = models.Model(input_layer, output_layer)

## Inspecting the model
model.summary()
#Layer (type)	Output shape    	Param #
#InputLayer     (None, 32, 32, 3)       0
#Flatten        (None, 3072)            0
#Dense          (None, 200)             614,600
#Dense          (None, 150)             30,150
#Dense          (None, 10)              1,510
#Total params                           646,260
#Trainable params                       646,260
#Non-trainable params                   0

## Compliling the model
from tensorflow.keras import optimizers

opt = optimizers.Adam(learning_rate=0.0005)
model.compile(loss='categorical_crossentropy', optimizer=opt,
              metrics=['accuracy'])

## Training the model
model.fit(x_train 1
          , y_train 2
          , batch_size = 32 3
          , epochs = 10 4
          , shuffle = True 5
          )
          
## Evaluating the model
model.evaluate(x_test, y_test)
```

* Batch size determines how many observations will be passed to the network at each training step
* epochs determine how many times the network will be shown the entire data
* shuffle = true -> batches will be drawn randomly without replacement from the training data at each step
* At each training step, one batch of images is passed through the network and the errors are backpropagated to update the weights
* Generally a batch size between 32 and 256 is used. It is also now recommended practice to increase the batch size as training progresses
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption><p>Diagram of the MLP Architecture</p></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption><p>Output from the fit method</p></figcaption></figure>
