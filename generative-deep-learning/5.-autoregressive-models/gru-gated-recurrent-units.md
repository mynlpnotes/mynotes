# GRU - Gated Recurrent Units

Key differences from LSTM:

1. The forget and input gates are replaced by reset and update gates.
2. There is no cell state or output gate, only a hidden state that is output from the cell

**Updation of hidden state:**

<figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>



1. The hidden state of the previous timestep, ℎt-1, and the current word embedding, xt, are concatenated and used to create the _reset_ gate. This gate is a dense layer with a sigmoid activation function. The resulting vector, rt, has length equal to the number of units in the cell and stores values between 0 and 1 that determine how much of the previous hidden state, ℎt-1, should be carried forward into the calculation for the new beliefs of the cell.
2. The reset gate is applied to the hidden state, ℎt-1, and concatenated with the current word embedding, xt. This vector is then fed to a dense layer with a tanh activation function to generate a vector, ℎ˜t, that stores the new beliefs of the cell. It has length equal to the number of units in the cell and stores values between –1 and 1.
3. The concatenation of the hidden state of the previous timestep, ℎt-1, and the current word embedding, xt, are also used to create the _update_ gate. This gate is a dense layer with a sigmoid activation. The resulting vector, Zt, has length equal to the number of units in the cell and stores values between 0 and 1, which are used to determine how much of the new beliefs, ℎ˜�, to blend into the current hidden state, ℎt-1.
4. The new beliefs of the cell, ℎ˜t, and the current hidden state, ℎt-1, are blended in a proportion determined by the update gate, Zt, to produce the updated hidden state, ℎt, that is output from the cell.
