# Dall-E
Dall-E works in a 3-step process:
1. It encodes the user's text prompt;
2. It looks through its latent space to find an image's embedding similar to the user prompt embedding (similarity measured using Cosine Similarity, I guess);
3. Considering the found image embedding as the Prior, it generates probable images