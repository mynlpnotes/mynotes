# Types of Models

**Sequential Model:**&#x20;

* Defining a linear stack of layers (Where one layer follows on directly from previous layer without any branching)

```python
from tensorflow.keras import layers, models

model = models.Sequential([
    layers.Flatten(input_shape=(32, 32, 3)),
    layers.Dense(200, activation = 'relu'),
    layers.Dense(150, activation = 'relu'),
    layers.Dense(10, activation = 'softmax'),
])
```

**Functional Model:**

* Output from a layer is passed to multiple subsequent layers, or conversely, that a layer receives input from multiple preceding layers
* Better for complex architecture
