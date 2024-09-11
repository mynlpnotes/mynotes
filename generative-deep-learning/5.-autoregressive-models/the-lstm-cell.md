# The LSTM Cell

* The job of the LSTM cell is to output a new hidden state ht, given its previous hidden state ht-1, and the current word embedding xt
* The length of ht is equal to the number of units in the LSTM.&#x20;
* This is a parameter that is set when you define the layer and has nothing to do with the length of the sequence.
* An LSTM cell maintains a cell state Ct, which can be thought of as the cell’s internal beliefs about the current status of the sequence.&#x20;
* This is distinct from the hidden state ht , which is ultimately output by the cell after the final timestep.&#x20;
* The cell state is the same length as the hidden state
*



**Note:**

* do not confuse the term _cell_ with _unit_.&#x20;
* There is one cell in an LSTM layer that is defined by the number of units it contains
* We often draw a recurrent layer as a chain of cells unrolled, as it helps to visualize how the hidden state is updated at each timestep
