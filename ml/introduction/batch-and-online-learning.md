# Batch and Online Learning

Batch learning:

* Incapable of learning incrementally: it must be trained using all the available data
* Take a lot of time and computing resources, so it is typically done offline
*

    <figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

**Online learning:**

* You train the system incrementally by feeding it data instances sequentially, either individually or in small groups called mini-batches. Each learning step is fast and cheap, so the system can learn about new data on the fly, as it arrives
*   &#x20;&#x20;

    <figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>
* Online learning algorithms can also be used to train systems on huge datasets that cannot fit in one machine’s main memory
* One important parameter of online learning systems is how fast they should adapt to changing data: this is called the learning rate. If you set a high learning rate, then your system will rapidly adapt to new data, but it will also tend to quickly forget the old data (you don’t want a spam filter to flag only the latest kinds of spam it was shown). Conversely, if you set a low learning rate, the system will have more inertia; that is, it will learn more slowly, but it will also be less sensitive to noise in the new data or to sequences of nonrepresentative data points
*

    <figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>
