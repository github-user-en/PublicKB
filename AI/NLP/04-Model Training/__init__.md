**Generalization** in machine learning refers to a model's ability to perform well on new, unseen data that was not part of the training dataset. It is a crucial property indicating that the model has learned the underlying patterns and relationships within the training data, rather than merely memorizing the training examples.

**Grokking** refers to the surprising phenomenon of delayed generalization where neural networks, generalize on certain learning problems, long after overfitting their training set. 
![[Pasted image 20240609134918.png]]
- Since Grokking requires extended model training, it runs contrary to the traditional Machine Learning belief that we need to stop model training early to prevent overfitting.
- Grokking can occur not only on algorithmic datasets (such as in case of linear regression), but also on mainstream benchmark dataset requiring non-linear thinking (such as MNIST image classification).  ![[Pasted image 20240609141243.png]]
- The emergence of embedding patterns after grokking indicates that the embeddings are not random but instead, have a structured relationship that reflects the underlying mathematical operations the model is learning.
- Furthermore, it's been demonstrate that for a challenging reasoning task with a large search space, GPT-4-Turbo and Gemini-I .5-Pro based on non-parametric memory fail badly regardless of prompting styles or retrieval augmentation, while a fully grokked transformer can achieve near-perfect accuracy, showcasing the power of parametric memory for complex reasoning.
> [!info] Grokking references:
> https://www.youtube.com/watch?v=QgOeWbW0jeA

Grokking 