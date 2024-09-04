# Reparameterization Trick

* Rather than sample directly from a normal distribution with parameters z\_mean and z\_log\_var, we can sample epsilon from a standard normal and then manually adjust the sample to have the correct mean and variance.
* This is known as the reparameterization trick, and it’s important as it means gradients can backpropagate freely through the layer.&#x20;
* By keeping all of the randomness of the layer contained within the variable epsilon, the partial derivative of the layer output with respect to its input can be shown to be deterministic (i.e., independent of the random epsilon), which is essential for backpropagation through the layer to be possible.
