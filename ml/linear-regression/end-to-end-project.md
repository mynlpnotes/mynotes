# End to End Project

* housing.head() -> To look at the top 5 rows
*

    <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
* &#x20;Info -> To get a quick description of the data, in particular the total number of rows, each attribute’s type, and the number of non-null value
*

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
* &#x20;housing.describe()
*

    <figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
* &#x20;Stratified sampling:
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

Discover and Visualize the Data to Gain Insights:

*

    <figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Looking for Correlations:

*

    <figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
* The correlation coefficient ranges from –1 to 1
*

    <figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>
* Another way to check for correlation between attributes is to use the pandas scatter\_matrix() function, which plots every numerical attribute against every other numerical attribute.
*

    <figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>
* The main diagonal (top left to bottom right) would be full of straight lines if pandas plotted each variable against itself, which would not be very useful. So instead pandas displays a histogram of each attribute

**Handling missing values**

1. Get rid of the corresponding districts.
2. Get rid of the whole attribute.
3. Set the values to some value

* Scikit-Learn provides a handy class to take care of missing values: SimpleImputer
*

    <figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>
* Since the median can only be computed on numerical attributes, you need to create a copy of the data without the numerical attributes
*

    <figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
* The imputer has simply computed the median of each attribute and stored the result in its statistics\_ instance variable
*

    <figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
* The result is a plain NumPy array containing the transformed features. If you want to put it back into a pandas DataFrame, it’s simple:
*

    <figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

**Handling Text and Categorical Attributes:**

*

    <figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

Notice that the output is a SciPy sparse matrix, instead of a NumPy array

![](file:///C:/Users/hitesh.wankhede/AppData/Local/Packages/oice\_16\_974fa576\_32c1d314\_144c/AC/Temp/msohtmlclip1/01/clip\_image004.jpg)

You can get the list of categories using the encoder’s categories\_ instance variable:

![](file:///C:/Users/hitesh.wankhede/AppData/Local/Packages/oice\_16\_974fa576\_32c1d314\_144c/AC/Temp/msohtmlclip1/01/clip\_image006.jpg)

Custom Transformers:

Create a class and implement three methods: fit() (returning self), transform(), and fit\_transform()

![](file:///C:/Users/hitesh.wankhede/AppData/Local/Packages/oice\_16\_974fa576\_32c1d314\_144c/AC/Temp/msohtmlclip1/01/clip\_image008.jpg)
