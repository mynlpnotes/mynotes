# Passing data through a coupling layer

* The first d dimensions of the data are fed through to the first coupling layer—the remaining D - d  dimensions are completely masked
* In our simple example with D = 2 , choosing d = 1 means that instead of the coupling layer seeing two values, ( x1 , x2 ) , the layer sees ( x1 , 0 )
*

    <figure><img src="../../.gitbook/assets/image (6) (1).png" alt="" width="300"><figcaption></figcaption></figure>
*   Update Equations:

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
* Jacobian matrix of the equation:
*

    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
* The top-left dXd submatrix is simply the identity matrix, because Z1:d = X1:d . These elements are passed straight through without being updated.&#x20;
* The top-right submatrix is therefore 0, because is not dependent on xd+1:D.
* The bottom-left submatrix is complex, and we do not seek to simplify this. The bottom-right submatrix is simply a diagonal matrix, filled with the elements of exp(s(x1:d)) , because zd+1:D is linearly dependent on xd+1:D and the gradient is dependent only on the scaling factor(and not on the translation factor)
* There are no nonzero elements above the diagonal—for this reason, this matrix form is called lower triangular
* the determinant of a lower-triangular matrix is just equal to the product of the diagonal elements. In other words, the determinant is not dependent on any of the complex derivatives in the bottom-left submatrix
*

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt="" width="300"><figcaption></figcaption></figure>
* This is easily computable, which was one of the two original goals of building a normalizing flow model
* The other goal was that the function must be easily invertible
*

    <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (4) (1).png" alt="" width="300"><figcaption></figcaption></figure>
* how should we update the first d elements of the input? Currently they are left completely unchanged by the model
