# Stacked RNN

* We can stack RNN so that deeper features can be learned from the text
* The second layer uses the hidden state from the first layer as its input data
*

    <figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
*

    ```python
    text_in = layers.Input(shape = (None,))
    embedding = layers.Embedding(total_words, embedding_size)(text_in)
    x = layers.LSTM(n_units, return_sequences = True)(x)
    x = layers.LSTM(n_units, return_sequences = True)(x)
    probabilites = layers.Dense(total_words, activation = 'softmax')(x)
    model = models.Model(text_in, probabilites)
    #Layer (type)	                 Output shape	               Param #
    #InputLayer                      (None, None)                  0
    #Embedding                       (None, None, 100)             1,000,000
    #LSTM                            (None, None, 128)             117,248
    #LSTM                            (None, None, 128)             131,584
    #Dense                           (None, None, 10000)           1,290,000
    #Total params                                                  2,538,832
    #Trainable params                                              2,538,832
    #Non-trainable params                                          0
    ```
