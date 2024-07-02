> [!info] Reference:
>- [Three things everyone should know about Vision Transformers](https://github.com/github-user-en/PublicKB/blob/9fbd47011ecb457d813efaf59b8488c7ee5c4ef3/AI/Computer%20Vision%20-%20Machine%20Vision/03-ModelBuilding/Computer%20Vision%20Models/Vision%20Transformer/Three%20things%20everyone%20should%20know%20about%20Vision%20Transformers.pdf)

1. The residual layers of vision transformers, which are usually processed sequentially, can to some extent be processed efficiently in parallel without noticeably affecting the accuracy.
2. Typically one would train a model at a lower resolution than the one employed at inference time. This not only saves resources, but also reduces the discrepancy of scale between train and test images that results from data augmentation
3. Fine-tuning the weights of the attention layers, while keeping the feedforward network (FFN) layers frozen, is usually sufficient to adapt vision transformers to a higher resolution and to other classification tasks. This saves compute, reduces the peak memory consumption at fine-tuning time, and allows sharing the majority of weights across tasks.
4. Adding MLP-based patch pre-processing layers improves Bert-like self-supervised training based on patch masking.