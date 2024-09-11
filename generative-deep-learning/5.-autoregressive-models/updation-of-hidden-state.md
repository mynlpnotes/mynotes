# Updation of hidden state

**Six steps:**

*

    <figure><img src="../../.gitbook/assets/image (7).png" alt="" width="450"><figcaption></figcaption></figure>

1. The hidden state of the previous timestep, ℎt-1, and the current word embedding, xt, are concatenated and passed through the _forget_ gate. This gate is simply a dense layer with a sigmoid activation function. The resulting vector, ft, has length equal to the number of units in the cell and contains values between 0 and 1 that determine how much of the previous cell state, Ct-1, should be retained
2. The concatenated vector is also passed through an _input_ gate that, like the forget gate, is a dense layer with weights matrix Wi, bias bi, and a sigmoid activation function. The output from this gate, It, has length equal to the number of units in the cell and contains values between 0 and 1 that determine how much new information will be added to the previous cell state, Ct-1.
3. The concatenated vector is passed through a dense layer with weights matrix Wc, bias bc, and a tanh activation function to generate a vector C˜t that contains the new information that the cell wants to consider keeping. It also has length equal to the number of units in the cell and contains values between –1 and 1.
4. ft and Ct-1 are multiplied element-wise and added to the element-wise multiplication of it and C˜t. This represents forgetting parts of the previous cell state and then adding new relevant information to produce the updated cell state Ct
5. The concatenated vector is passed through an _output_ gate: a dense layer with weights matrix Wo, bias bo, and a sigmoid activation. The resulting vector, Ot, has length equal to the number of units in the cell and stores values between 0 and 1 that determine how much of the updated cell state, Ct, to output from the cell
6. Ot is multiplied element-wise with the updated cell state, Ct , after a tanh activation has been applied to produce the new hidden state, ht
