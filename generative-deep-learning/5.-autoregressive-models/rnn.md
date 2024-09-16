# RNN

Working of RNN:

* A recurrent layer has the special property of being able to process sequential input data x1, x2,....xn . It consists of a cell that updates its hidden state, ℎt, as each element of the sequence xt is passed through it, one timestep at a time
* The hidden state is a vector with length equal to the number of units in the cell—it can be thought of as the cell’s current understanding of the sequence
* At timestep t, the cell uses the previous value of the hidden state ht-1, together with the data from the current timestep xt to produce an updated hidden state vector ht
* This recurrent process continues until the end of the sequence. Once the sequence is finished, the layer outputs the final hidden state of the cell hn, which is then passed on to the next layer of the network.
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt="" width="198"><figcaption></figcaption></figure>
* It’s important to remember that all of the cells in this diagram share the same weights (as they are really the same cell)
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>
