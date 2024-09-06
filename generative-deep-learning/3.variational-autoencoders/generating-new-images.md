# Generating New Images

* We can generate novel images by sampling some points in the latent space and using the decoder to convert these back into pixel space

```python
mins, maxs = np.min(embeddings, axis=0), np.max(embeddings, axis=0)
sample = np.random.uniform(mins, maxs, size=(18, 2))
reconstructions = decoder.predict(sample)
```

*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption><p>Generated Images</p></figcaption></figure>

