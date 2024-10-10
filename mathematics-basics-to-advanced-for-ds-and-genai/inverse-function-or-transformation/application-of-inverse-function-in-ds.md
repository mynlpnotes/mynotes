# Application of Inverse Function in DS

1. **Normalization and Standardization:**

* The magnitude is different for each features
* But if we scale down them to same scale then training the model will be easier
*

    <figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>
* Standardization:
* Means = 0 and standard deviation = 1
*

    <figure><img src="../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>
* **Normalization:**
*   Feature scaling with min max normalization

    <figure><img src="../../.gitbook/assets/image (17) (1).png" alt=""><figcaption></figcaption></figure>
* Distribution of data:
  * Logarithmic Distribution:
  * In financial data analysis, income or sales data often exhibit skewness.
  * Applying a log transformation can stabilize the variance and make patterns more visible
  * After model predictions, the inverse log transformations is applied to interpret the results on the original scale
  *

      <figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
