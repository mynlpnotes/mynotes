# Tokenization

* Process of splitting the text up into individual units, such as words or characters.

**Work Tokens:**

* All words are tokenized to lowercase irrespective of whether it appears at start or in the middle of the statement
* Vocabulary can be very large with some words appearing only once, it may be wise to replace them with some other unknown word to reduce the size of the vocabulary
* Words can be stemmed
* Punctuation can either be tokenized or removed
* Models can never predict words outside the training vocabulary

**Character tokens:**

* The model may generate sequences of characters that form new words outside of the training vocabulary
* Capital letters can either be converted to their lowercase counterparts, or remain as separate tokens
* Capital letters can either be converted to their lowercase counterparts, or remain as separate tokens



```python
def pad_punctuation(s):
    s = re.sub(f"([{string.punctuation}])", r' \1 ', s)
    s = re.sub(' +', ' ', s)
    return s

text_data = [pad_punctuation(x) for x in filtered_data] 

text_ds = tf.data.Dataset.from_tensor_slices(text_data).batch(32).shuffle(1000) 

vectorize_layer = layers.TextVectorization( 
    standardize = 'lower',
    max_tokens = 10000,
    output_mode = "int",
    output_sequence_length = 200 + 1,
)

vectorize_layer.adapt(text_ds) 
vocab = vectorize_layer.get_vocabulary()
```

* Pad the punctuation marks, to treat them as separate words
* Create a Keras TextVectorization layer to convert text to lowercase, give the most prevalent 10,000 words a corresponding integer token, and trim or pad the sequence to 201 tokens long
* Apply the TextVectorization layer to the training data
* Apply the TextVectorization layer to the training data
* 0 - Stop token
* 1 - Unknown words that fall outside the vocabulary
*

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Recipe tokenized</p></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Vocabulary of the text vectorization layer</p></figcaption></figure>
