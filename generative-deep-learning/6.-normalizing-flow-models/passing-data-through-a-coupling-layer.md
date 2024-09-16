# Passing data through a coupling layer

* The first d dimensions of the data are fed through to the first coupling layer—the remaining D - d  dimensions are completely masked
* In our simple example with D = 2 , choosing d = 1 means that instead of the coupling layer seeing two values, ( x1 , x2 ) , the layer sees ( x1 , 0 )
*
*

    <figure><img src="../../.gitbook/assets/image.png" alt="" width="300"><figcaption></figcaption></figure>
