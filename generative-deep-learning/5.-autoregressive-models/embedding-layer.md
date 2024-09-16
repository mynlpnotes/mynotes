# Embedding Layer

* An embedding layer is essentially a <mark style="color:purple;background-color:purple;">lookup table that converts each integer token into a vector of length embedding\_size</mark>
* The lookup vectors are learned by the model as weights. Therefore, the number of weights learned by this layer is equal to the size of the vocabulary multiplied by the dimension of the embedding vector (i.e., 10,000 × 100 = 1,000,000)
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
* We embed each integer token into a continuous vector because <mark style="color:purple;background-color:purple;">**it enables the model to learn a representation for each word that is able to be updated through backpropagation**</mark>
* The Input layer passes a tensor of integer sequences of shape \[batch\_size, seq\_length] to the Embedding layer, which outputs a tensor of shape \[batch\_size, seq\_length, embedding\_size]. This is then passed on to the LSTM layer
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
