# Tokenization

* Process of splitting the text up into individual units, such as words or characters.

**Work Tokens:**

* All words are tokenized to lowercase irrespective of whether it appears at start or in the middle of the statement
* <mark style="color:purple;background-color:purple;">**Vocabulary can be very large with some words appearing only once, it may be wise to replace them with some other unknown word to reduce the size of the vocabulary**</mark>
* Words can be stemmed
* Punctuation can either be tokenized or removed
* <mark style="color:purple;background-color:purple;">**Models can never predict words outside the training vocabulary**</mark>

**Character tokens:**

* <mark style="color:purple;background-color:purple;">**The model may generate sequences of characters that form new words outside of the training vocabulary**</mark>
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
* <mark style="color:purple;background-color:purple;">**Padding function: Hello, world! How are you? -> Hello , world ! How are you ?**</mark>
* <mark style="color:purple;background-color:purple;">**Batches:**</mark>
* <mark style="color:purple;background-color:purple;">**100 records loaded**</mark> <mark style="color:purple;background-color:purple;"></mark><mark style="color:purple;background-color:purple;">→ shuffled.</mark>
* <mark style="color:purple;background-color:purple;">**32 records taken from buffer → passed to the neural network.**</mark>
* <mark style="color:purple;background-color:purple;">**32 new records added to buffer (to maintain buffer size of 100).**</mark>
* <mark style="color:purple;background-color:purple;">**Shuffling again within the buffer.**</mark>
* <mark style="color:purple;background-color:purple;">**Repeat until all 1000 records are processed.**</mark>
* Create a Keras TextVectorization layer to convert text to lowercase, give the most prevalent 10,000 words a corresponding integer token, and trim or pad the sequence to 201 tokens long
* <mark style="color:purple;background-color:purple;">**If the sentence lenght is 150 then it will be padded, if its lenght is 250 then it will be truncated**</mark>
* Apply the TextVectorization layer to the training data
* 0 - Stop token
* 1 - Unknown words that fall outside the vocabulary
*

    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Recipe tokenized</p></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>Vocabulary of the text vectorization layer</p></figcaption></figure>
