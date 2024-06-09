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
   Here, you are training the model to:
	   1. Play the role of a helpful assistant in response to User prompts.
	   2. Answer questions of the form `What is the capital of ____?` in a specific format such as `The capital of ____ is ____.`
2. **Steerability:** refers to the ability to guide or control the behavior and output of an AI system according to human intentions or specific objectives.
	- Some techniques used to improve the steerability of AI systems are:
		- **Fine-tuning:** involves further training an existing AI model on new data that represents the desired behaviors and outputs.
		- **Human-in-the-loop systems:** These systems combine human oversight with AI capabilities, allowing humans to guide the AI's actions.
	- Examples of steerability in AI systems are:
		- **1. Search Engines:**
			- **Problem:** Although search engines prioritize the most relevant results based on their algorithms, but these results might not always align with the user's specific intent.
			- **Steerability in Action:** Some search engines allow users to refine their searches using filters or adding specific keywords. This steers the search results towards what the user is truly looking for.
		- **2. Recommendation Systems:**
			- **Problem:** Recommendation systems suggest products, movies, or content based on a user's past behavior. However, these recommendations might not always reflect the user's current mood or evolving preferences.
			- **Steerability in Action:** Many recommendation systems allow users to explicitly "like" or "dislike" suggestions. This feedback loop steers the system towards providing recommendations that better align with the user's taste. Additionally, some systems allow users to temporarily change their preferences based on their current mood (e.g., "show me something funny today").
		- **3. Text Summarization Systems:**
			- **Problem:** Text summarization systems automatically create summaries of longer pieces of text. However, depending on the summarization algorithm, the summary might focus on different aspects of the original text.
			- **Steerability in Action:** Some summarization systems allow users to specify the desired length or focus area (e.g., key points, main arguments) for the summary. This steers the system to generate a summary that aligns with the user's needs.
		- **4. Dialogue Systems (Chatbots):**
			- **Problem:** Chatbots are computer programs designed to simulate conversation with humans. However, their responses might not always be on point or address the user's specific questions.
		    - **Steerability in Action:** Some chatbots allow users to correct or refine their responses. Additionally, developers can steer the chatbot's conversation flow by designing decision trees or using prompts that guide the chatbot towards providing helpful and relevant information.
		- **5. Content Creation Tools:**
			- **Problem:** AI-powered content creation tools can generate different creative text formats, but the style or tone might not always be what the user desires.
		    - **Steerability in Action:** Some content creation tools (such as Grammarly) allow users to specify the desired tone (e.g., formal, informal, humorous) or style (e.g., narrative, persuasive) for the generated content. This steers the AI model to create content that aligns with the user's preferences.