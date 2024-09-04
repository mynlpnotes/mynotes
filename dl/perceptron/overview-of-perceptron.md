# Overview of Perceptron

* It was invented by Frank Rosanblatt in 1957
* He had published paper – The perceptron of probabilistic model for information storage and organization in the brain
* Different from 1st neuron which we had seen
* In 1st neuron we used to take binary input, whereas here we can take real values
* Also known as:
* LTU – Linear threshold unit
* TLU – Threshold logic unit

Example:

* Task to make good cup of tea
* Binary classification problem (Tea can be good/bad)

Ingredients:

* 1 litre of Milk
* 1 kg of Tea
* 1 kg of Sugar
* If threshold is theta, so if it crosses theta then its good tea otherwise bad
* F is decision/activation function which helps to decide whether its good/bad tea
* This is forward pass
* If it’s a bad pass, then we need to update the weights using backpropagation
* Epoch = 1 forward + 1 back propagation
*

    <figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>
* Transfer function will multiply weights and input
* Output of transfer function will be passed to activation function which will give output based on threshold
