# Neural Network

* Series of stacked layers
* Units connected to previous layers units through a set of weights
* Different types of layers - Fully connected is the most common one
* NN where all layers are connected is known as Multi layer perceptron
*

    <figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
* In forward pass, each unit applies a non linear transformation to the weighted sum of its inputs and passes it through to the subsequent layer
* In the final layer, we will have a single unit, that outputs a probability of which category the image belongs to
* The process of finding weights is known as training
* In backpropagation, the error is propagated backward throught the network adjust weights by a small amount in the direction which will improve the prediction

