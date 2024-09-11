# Analysis of the LSTM

Process to generate long strings:

1. Feed the network with an existing sequence of words and ask it to predict the following word.
2. Append this word to the existing sequence and repeat.

* temperature parameter to the sampling process to indicate how deterministic we would like the process to be
* A temperature close to 0 makes the sampling more deterministic (i.e., the word with the highest probability is very likely to be chosen), whereas a temperature of 1 means each word is chosen with the probability output by the model.
*

    ```python
    class TextGenerator(callbacks.Callback):
        def __init__(self, index_to_word, top_k=10):
            self.index_to_word = index_to_word
            self.word_to_index = {
                word: index for index, word in enumerate(index_to_word)
            } 

        def sample_from(self, probs, temperature): 
            probs = probs ** (1 / temperature)
            probs = probs / np.sum(probs)
            return np.random.choice(len(probs), p=probs), probs

        def generate(self, start_prompt, max_tokens, temperature):
            start_tokens = [
                self.word_to_index.get(x, 1) for x in start_prompt.split()
            ] 
            sample_token = None
            info = []
            while len(start_tokens) < max_tokens and sample_token != 0: 
                x = np.array([start_tokens])
                y = self.model.predict(x) 
                sample_token, probs = self.sample_from(y[0][-1], temperature) 
                info.append({'prompt': start_prompt , 'word_probs': probs})
                start_tokens.append(sample_token) 
                start_prompt = start_prompt + ' ' + self.index_to_word[sample_token]
            print(f"\ngenerated text:\n{start_prompt}\n")
            return info

        def on_epoch_end(self, epoch, logs=None):
            self.generate("recipe for", max_tokens = 100, temperature = 1.0)
    ```
* Create an inverse vocabulary mapping (from word to token)
* This function updates the probabilities with a `temperature` scaling factor
* The start prompt is a string of words that you would like to give the model to start the generation process (for example, _recipe for_). The words are first converted to a list of token
* The sequence is generated until it is `max_tokens` long or a stop token (0) is produced
* The model outputs the probabilities of each word being next in the sequence.
* The probabilities are passed through the sampler to output the next word, parameterized by `temperature`
* We append the new word to the prompt text, ready for the next iteration of the generative process.
* The model has some contextual understanding of the differences between recipes depending on their ingredients
* While our basic LSTM model is doing a great job at generating realistic text, it is clear that it still struggles to grasp some of the semantic meaning of the words that it is generating.&#x20;
* It introduces ingredients that are not likely to work well together
