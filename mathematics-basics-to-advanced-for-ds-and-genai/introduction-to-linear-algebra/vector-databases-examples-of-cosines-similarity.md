# Vector Databases - Examples of Cosines Similarity

* We design a RAG system using vector database
* We have huge book of 500 pages
* We want to create a chatbot
* This should be able to answer any question from this book
* <mark style="color:purple;background-color:purple;">**Entire text in the book is converted into vectors**</mark>
* <mark style="color:purple;background-color:purple;">**We save this vectors inside a vector DB**</mark>
* <mark style="color:purple;background-color:purple;">**Query from user will be converted into vector**</mark>
* <mark style="color:purple;background-color:purple;">**Next step is using this vector we will query the DB**</mark>
* <mark style="color:purple;background-color:purple;">**Inside the DB there will be a cosine similarity search**</mark>
* <mark style="color:purple;background-color:purple;">**The vector which had the highest similarity will be converted into text**</mark>
*   And information will be displayed

    <figure><img src="../../.gitbook/assets/image (11) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
