# Feature Scaling

* Scaling the target values is generally not required.
* There are two common ways to get all attributes to have the same scale: min-max scaling and standardization.

**Min-max scaling:**

* 0 to 1
* Subtracting the min value and dividing by the max minus the min

**MinMaxScaler:**

* First it subtracts the mean value, and then it divides by the standard deviation
* Does not bound values to a specific range

**StandardScaler:**
