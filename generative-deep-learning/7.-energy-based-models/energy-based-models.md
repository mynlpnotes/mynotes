# Energy-Based Models

* Energy-based models attempt to model the true data-generating distribution using a Boltzmann distribution where E(x) is know as the energy function (or score) of an observation x
*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
* In practice, this amounts to training a neural network E(x) to output low scores for likely observations (so px is close to 1) and high scores for unlikely observations (so px is close to 0)

Challenges:

1. It is not clear how we should use our model for sampling new observations—we can use it to generate a score given an observation, but how do we generate an observation that has a low score
2. The normalizing denominator contains an integral that is intractable for all but the simplest of problems. If we cannot calculate this integral, then we cannot use maximum likelihood estimation to train the model, as this requires that p𝐱 is a valid probability distribution

* The key idea behind an energy-based model is that we can use approximation techniques to ensure we never need to calculate the intractable denominator.
* We sidestep the tricky intractable denominator problem by using a technique called contrastive divergence (for training) and a technique called Langevin dynamics (for sampling)
