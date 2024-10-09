# Scalars and Vectors

**Scalar:**

* Single numerical value value
* It represents a magnitude or quantity and has no direction
* Example:
  * Car speed = 45km/hr. -> this value is magnitude, so its scalar
  * Temperature in Celsius -> this is also magnitude
* Application in Data science:
  * Dataset
    * Count of total number of records
    * Average of feature f1
  * Simple linear regression:&#x20;
    * y = mx + c
    * Here we can consider c as scalar, but m is not scalar

**Vectors:**

* Numerical value which has both magnitude and direction -> Def w.r.t physics
* A vector is an ordered list of numbers, it can represent a point in space or quantity with both magnitude and direction -> Def w.r.t DS
* Example:
  * Speed of the car is 45km/hr and moving towards east direction -> w.r.t Physics
  * Dataset of student marks
    * IQ        No. of study hours        Pass/Fail
    * If we consider only IQ and no. of study hours \[IQ   No. of study hours]
    * A vector representing person IQ and no. of study hours
  * A vector representing person weights over time
    * \[70, 72, 75, 73] -> This also represents vector w.r.t time -> 4 dimension
  * In DS context it does not necessarily have a physical direction
  * In DS, a vector represents a collection of values
  * A is of 2 dimension here, do see this in physics we define a coordinate system
  * We can calculate distance between origin and A using Pythagoras theorem
  * Similarly we can plot B
  * Similarly we can do for C using 3 dimensions
  *

      <figure><img src="../../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>



* Each record can be represented as a vector
* Lets plot the points with IQ and no. of hours
* If a point is below line y then it will be fail, if its above then it will be pass
* So every datapoint in dataset is represented as a vector
* We can do this for any no. of dimension
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
