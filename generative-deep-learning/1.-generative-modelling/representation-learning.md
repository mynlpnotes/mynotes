# Representation Learning

* To search for a person in a crowd, we wont be telling each pixel value, we will just descirbe in 5 to 10 sentences and the person should be able to search
* Here a basic assumption is that he knows how a person looks like
* We describe each observation in the training set using some lower-dimensional latent space and then learn a mapping function that can take a point in the latent space and map it to a point in the original domain
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Each tin box can be represented using width and height
* We can convert each image of a tin to a point in a latent space of just two dimensions, even though the training set of images is provided in high-dimensional pixel space
* So that means we can also apply new images by applying a suitable mapping function f to a new point in the latent space
* For a machine its not so easy, it first needs to learn that height and width are the two latent space dimensions that best describe the dataset and then learn the mapping function
