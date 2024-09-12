# Creating the Training Set

* Our LSTM will be trained to predict the next word in a sequence, given a sequence of words preceding this point
*

    ```python
    def prepare_inputs(text):
        text = tf.expand_dims(text, -1)
        tokenized_sentences = vectorize_layer(text)
        x = tokenized_sentences[:, :-1]
        y = tokenized_sentences[:, 1:]
        return x, y

    train_ds = text_ds.map(prepare_inputs)
    ```
* <mark style="color:purple;background-color:purple;">**Create the training set consisting of recipe tokens (the input) and the same vector shifted by one token (the target)**</mark>
