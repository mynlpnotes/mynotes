# Activation Functions

**ReLU:**

* Rectified linear unit
* Output will be 0 if input is negative otherwise its equal to input
* In leaky ReLU it outputs a small negative proportional to the input for -ve inputs
* ReLU units sometimes die if they always give output as 0, so their gradient will be 0 and their weights wont be updated
* Leaky ReLU fixes this by ensuring that there always is some output

**Sigmoid:**

* Useful if output of layer is to be scaled between 0 and 1
* For binary classification OR multilabel classification

**Softmax:**

* Useful if you want total sum of outputs from a layer to be 1
* Used in output layer
*

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
* Activation function can be defined within a layer OR as a separate layer

```python
x = layers.Dense(units=200, activation = 'relu')(x)

x = layers.Dense(units=200)(x)
x = layers.Activation('relu')(x)
```

*
