# Applications of Linear Algebra

1. **Data Representation and Manipulations**

* We have a dataset and we want to create a model which will be able to predict
* Lets say the dataset is of House price prediction
* Independent/Input Features: Area, No. of rooms, Location.&#x20;
* Output Feature: Price
* So here we want to design a model which will take area, no. of rooms and location as input and predict price
* We know if area is more OR no. of rooms is more OR location is good then price will be more, But model does not understands this
* <mark style="color:purple;background-color:purple;">**This input data is represented in the form of vectors to the model**</mark>
* Based on this vector, our model will be able to quantify the relationship between area and price, it can also quantify relationship between all other features
* Quantify means concepts like covariance, correlation
* So here <mark style="color:purple;background-color:purple;">**linear algebra provides tools for representation and manipulating data in the form of vectors**</mark>
* Vector can be single dimension or multi dimension as well
* If we plot area vs price, then we see as area increases then price increases
* So each point on this plot will be of 2 dimension
* We can also plot 3 dimension using area, no. of rooms and price
* <mark style="color:purple;background-color:purple;">**Linear algebra works well with higher dimension data - Even if the data is in 5000 dimension still the kind of vector multiplication etc can be done, it will give very good resuls**</mark>
* <mark style="color:purple;background-color:purple;">**If there are 500 dimensions then using the linear algebra concepts used in dimensionality reduction, it will can even convert it into 2 dimension**</mark>
*

    <figure><img src="../../.gitbook/assets/image (14) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

2. **ML and AI:**

* In ML, we want to train our model
* <mark style="color:purple;background-color:purple;">**For model training, we rely on linear algebra**</mark>
* As for training we might have to do multiple matrix arithmetic operations
* And we will also be using linear equation -> example straight line -> ax + by + c = 0
* Also used in <mark style="color:purple;background-color:purple;">**dimensionality reduction -> PCA -> Eigen value and eigen vectors will be used here**</mark>
* Also used in Neural networks for <mark style="color:purple;background-color:purple;">**Forward propagation and backward propagation**</mark>
* In GPUs we have core and it is faster coz it perform all the vector operations parallelly
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

3. **Computer Graphics:**

* <mark style="color:purple;background-color:purple;">**To represent an image**</mark>, suppose RGB&#x20;
*   And if we want to perform some operations like <mark style="color:purple;background-color:purple;">**scaling, rotate or change it to black and white**</mark>, then it can be done using linear algebra using transformations

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

4. **Optimization:**

* In optimization we solve equations
* In regression, we will try to find a slope and intercept&#x20;
* We want a best fit line, so that it takes any input and gives price
* Using linear algebra we try to find the best fit line so that we have the right slope and intercept
* We will try to maximize the function and minimize the error
*   Here <mark style="color:purple;background-color:purple;">**gradient descent will get applied for optimization**</mark>

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
