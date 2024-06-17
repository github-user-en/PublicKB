All classification AI models can be visualized into two abstract blocks:

| Block-1: The embedding creation block                                                                                                      | Block-2: The MLP-based classification block                                                                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| In this block, the objective is to come up with the best embedding representation one can, of the input blob (be it text / video / audio). | This is almost always a combination of: (a) a few linear feed-forward layers interleaved by non-linear activation layers; (b) followed by a softmax to convert the logits to probabilities. The number of outputs of this layer is equal to the the number of classes at hand. |

# Applying this framework to modern classification AI models
Modern classification AI models are all Transformer based. In the Transformer too, you'll essentially observe these two abstract blocks:
1. **Block-1: The embedding creation block**
	- In this block, we create the embedding step-by-step, layer-by-layer.
		1. It begins with tokenization and the patch embeddings;
		2. You add position information by concatenating to them the positional embeddings;
		3. Then, the transformer's normalization layer normalizes them for faster computation;
		4. The attention layer then enriches these embeddings with additional information about relations between the tokens.
			- In this layer, using Masked attention adds only 