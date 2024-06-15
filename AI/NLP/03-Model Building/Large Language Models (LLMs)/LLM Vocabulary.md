> [!info] References
> - https://www.youtube.com/watch?v=oWXTWqsSos4

![[Pasted image 20240609113442.png]]
- **Natural Language Processing (NLP)**: stemmed from the field of Information Retrieval where people wanted to search/retrieve data/information using Natural Language, instead of using SQL. The field grew to give birth to several sub-fields:
	- **Natural Language Understanding (NLU)**: aims at understanding human natural language input into machine understandable instructions.
	- **Natural Language Generation (NLG):** interested in making machines write like humans. This gave birth to generative models for next word/token prediction. 
		- **Statistical Models:** such as Markov Chain models.
		- **Deep Learning Models:** LLMs are an example of a Deep Learning model for NLG. Initial Language Models (such as T5) were encoder-decoder models. Today, most LLMs are decoder only models.
		 - **Base Model / Pre-trained Model:** These are essentially next word (or, next token) prediction systems, trained on pre-training data. However, these models aren't optimized for most downstream NLP tasks. They are usually best at either next token prediction or masked token prediction. `llama` is an examples of a base model,
		 - **Finetuned Model:** Based Models are subjected to **Instruction Fine Tuning** to result in Finetuned Models. *llama-instruct*, `llama-chat`, `codellama` etc. are examples of finetuned models. To understand how finetuning works, you should read about **Transfer Learning**.
			- **Downstream Tasks:** Downstream tasks refer to specific applications where you use pre-trained models. These tasks leverage the knowledge and abilities learned by the model from general-purpose training data and fine-tune them for a particular purpose. Examples include Text Classification, Chat/Question-Answering, Machine Translation, Text Summarization, Named Entity Recognition (NER), Text Generation (generating different creative text formats, like poems, code, scripts, musical pieces, emails, letters, etc.)
			- **Instruction Finetuning:** Involves subjecting the model to datasets with relevant instructions. 
				- Some popular finetuning datasets back in the day were Stanford Alpaca, ShareGPT, etc.
				- **Alignment:** Instruction Finetuning also involves techniques to align the LLM output to human expectations. Some popular alignment techniques are RLHF, DPO, PPO, etc.