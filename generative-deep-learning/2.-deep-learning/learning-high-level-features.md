# Learning High-Level Features

* NN learns from input without human intervention
* They do not need feature engineering

For example, a trained model might work as below:

*

    <figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
* Unit A receives the value for an individual channel of an input pixel.
* Unit B combines its input values so that it fires strongest when a particular low-level feature such as an edge is present.
* Unit C combines the low-level features so that it fires strongest when a higher-level feature such as teeth are seen in the image.
* Unit D combines the high-level features so that it fires strongest when the person in the original image is smiling.
