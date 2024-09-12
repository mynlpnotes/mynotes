# Training the LSTM

```python
inputs = layers.Input(shape=(None,), dtype="int32") 
x = layers.Embedding(10000, 100)(inputs) 
x = layers.LSTM(128, return_sequences=True)(x) 
outputs = layers.Dense(10000, activation = 'softmax')(x) 
lstm = models.Model(inputs, outputs) 

loss_fn = losses.SparseCategoricalCrossentropy()
lstm.compile("adam", loss_fn) 
lstm.fit(train_ds, epochs=25)
```

* The `Embedding` layer requires two parameters, the size of the vocabulary (10,000 tokens) and the dimensionality of the embedding vector (100)
*

    <figure><img src="../../.gitbook/assets/image (8) (1).png" alt="" width="300"><figcaption></figcaption></figure>

