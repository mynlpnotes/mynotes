# Bidirectional Cells

* For prediction problems where the entire text is available to the model at inference time
* We can process the text in forward as well as backward direction
* 2 sets of hidden states are stored: one from forward direction and another from backward direction
* This way, the layer can learn infromation from both the directions
*

    ```python
    layer = layers.Bidirectional(layers.GRU(100))
    ```
