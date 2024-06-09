**Instruction Finetuning:** Involves subjecting the model to datasets with relevant instructions. 
- Some popular finetuning datasets back in the day were Stanford Alpaca, ShareGPT, etc.
	- **Alignment:** Instruction Finetuning also involves techniques to align the LLM output to human expectations. Some popular alignment techniques are RLHF, DPO, PPO, etc.

# Should I use a base model for my applications, or, should I use a finetuned model?
> [!info] Reference
> https://www.youtube.com/watch?v=oWXTWqsSos4


![[Pasted image 20240609122635.png]]
In most cases, you won't be creating models from scratch. The question would be whether you should finetune a base model, or a finetuned model.
Most companies pick up a base model and finetune it to their needs. Sometimes they release it for other companies.

| When to finetune a base model?                                                                                                                               | When to finetune a finetuned model?                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| When you can't come across any finetuned model relevant to your dataset's domain, you should pick a base model an instruction-finetune it over your dataset. | When you can find a finetuned model related to your dataset's domain, your should instruction-finetune it over your dataset. You could use techniques such as LORA, etc. here. |
|                                                                                                                                                              | Some experts believe that with this technique is able to impart domain expertise to these models, but it's contested.                                                          |

# Why do finetuning?
1. **When you want role-play + formatting.**
   Example includes: 
   ![[Pasted image 20240609123006.png]]
   Here, you are training the model to answer questions of the form `What is the capital of ____?`
2. 