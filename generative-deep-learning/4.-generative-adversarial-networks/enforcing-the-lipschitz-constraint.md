# Enforcing the Lipschitz Constraint

* In the original WGAN paper, the authors show how it is possible to enforce the Lipschitz constraint by clipping the weights of the critic to lie within a small range, \[–0.01, 0.01], after each training batch.
* One of the criticisms of this approach is that the capacity of the critic to learn is greatly diminished, since we are clipping its weights
