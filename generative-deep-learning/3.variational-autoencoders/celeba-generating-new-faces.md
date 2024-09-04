# CelebA - Generating New Faces

* &#x20;Sample 30 points from a standard multivariate normal distribution with 200 dimension
* Decode the sampled points
* Plot the images

```python
grid_width, grid_height = (10,3)
z_sample = np.random.normal(size=(grid_width * grid_height, 200)) 

reconstructions = decoder.predict(z_sample) 

fig = plt.figure(figsize=(18, 5))
fig.subplots_adjust(hspace=0.4, wspace=0.4)
for i in range(grid_width * grid_height):
    ax = fig.add_subplot(grid_height, grid_width, i + 1)
    ax.axis("off")
    ax.imshow(reconstructions[i, :, :])
```
