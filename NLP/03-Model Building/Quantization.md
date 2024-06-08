It refers to the use of less precise 8-bit or 4-bit integer weights instead of 32-bit or 16-bit floating point numbers. Techniques include:

It's done for two reasons:
1. Edge devices (mobiles, laptops, smart watches) lack the RAM to be able to load the language model. A 1B FP32 LLM would required ~3GB RAM.
2. Edge devices (mobiles, laptops, smart watches) lack the energy supplies to support the energy-intensive matrix multiplication of floating point LLMs.

1-bit LLMs are a way forward, when used with ternary parameters.
- [The Era of 1-bit LLMs: All Large Language Models are in 1.58 Bits](https://arxiv.org/pdf/2402.17764)
- https://thegenerality.com/agi/
- https://www.youtube.com/watch?v=ZpxQec_3t38
- https://www.youtube.com/watch?v=wN07Wwtp6LE

