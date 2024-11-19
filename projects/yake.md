# Yake

1. Purpose of YAKE:\
   YAKE is a <mark style="color:purple;background-color:purple;">**keyword extraction**</mark> method designed to identify important keywords from a text document without relying on any external resources like dictionaries or pre-trained models. It's designed to be a lightweight, language-independent, and efficient approach for keyword extraction.
2. Statistical Features:\
   YAKE leverages several statistical features to determine the importance of each word in a document. The key features are:
   * <mark style="color:purple;background-color:purple;">**Frequency:**</mark> How often a word appears in the document.
   * <mark style="color:purple;background-color:purple;">**Position:**</mark> The location of the word in the document, with higher importance given to words appearing earlier or in certain sentence positions.
   * <mark style="color:purple;background-color:purple;">**Degree:**</mark> How often the word co-occurs with other significant words.
   * <mark style="color:purple;background-color:purple;">**Keyword Coherence:**</mark> How similar or related the word is to other words that have high importance.
   * <mark style="color:purple;background-color:purple;">**Length of the Word:**</mark> Longer words often carry more specific meaning and are considered more important.
3. Scoring Mechanism:\
   <mark style="color:purple;background-color:purple;">**Each word in the document is assigned a score based on these features. YAKE combines them into a single formula to determine which words are most likely to be keywords.**</mark> The algorithm computes a score for each word using these features, and higher scores indicate higher relevance as a keyword.
4. Language Independence:\
   YAKE does not require pre-training on a corpus of labeled data. It uses statistical properties, which makes it useful for different languages and domains without additional fine-tuning.
5. Application:\
   YAKE works well for short-text keyword extraction and is particularly suited for extracting keywords from single documents (e.g., resumes, scientific papers, news articles).
6. Efficient:\
   The algorithm is lightweight and computationally efficient, making it suitable for real-time applications or large-scale document processing.
