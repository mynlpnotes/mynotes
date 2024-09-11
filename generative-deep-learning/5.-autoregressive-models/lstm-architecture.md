# LSTM Architecture

* The input to the model is a sequence of integer tokens and the output is the probability of each word in the 10,000-word vocabulary appearing next in the sequence

```
Layer (type)	            Output shape	   Param #
InputLayer                  (None, None)           0
Embedding                   (None, None, 100)      1,000,000
LSTM                        (None, None, 128)      117,248
Dense                       (None, None, 10000)    1,290,000
Total params                                       2,407,248
Trainable params                                   2,407,248
Non-trainable params                               0
```

* Notice that the Input layer does not need us to specify the sequence length in advance. Both the batch size and the sequence length are flexible (hence the (None, None) shape). This is because all downstream layers are agnostic to the length of the sequence being passed through
