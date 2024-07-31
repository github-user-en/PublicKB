# Challenges in Semantic Remote Sensing Image Retrieval
1. It involves searching across image repositories on Peta Bytes/Zetta Bytes (PB/ZB) scale.
2. High dependence on supervised learning for accurate labelling.
3. Different instances of same feature... using different remote sensing techniques, and also, using different perspectives, etc.

# How I want to go about addressing these challenges
I will try to train/finetune a network which can learn the visual features from existing labelled datasets and be able to output embeddings which can be stored in databases.
Then, at retrieval time, the user query will be parsed by the same model to generate embeddings which will be matched with the image embeddings in the database.
> [!info]
> Once this model is trained, I'll be able to use it to generate image embeddings in an unsupervised manner, which I believe, is also the way Google's Image Search works. Unsupervised image labelling will allow us to address the issue of being able to label remote sensing images at scale.



