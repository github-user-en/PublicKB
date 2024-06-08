Over time, the capabilities of the Large Language Models have increased as follows:
1. LLMs as next token prediction systems.
2. LLMs as next token and masked token prediction systems.
3. LLMs - Question Answering (QA) systems.
	- These LLMs give answers based 
4. LLMs - Chatbots
	- These QA LLM systems with conversational history in short-term in-memory context
		- What is ***short-term in-memory context***? It means the the context vector is stored in the RAM. Hence, it's not persistent across sessions.
> [!info]
> From LLM Chatbots spawned two branches: LLM-RAG and LLM-Function Calling systems. These two branches later merge under LLM-Agents.

5. LLM-RAG 
	- These are LLM Chatbots access to ***external data***, in addition to their in-memory context.
	- The ***external data*** can be in the form of either a vector database or text database (text files, relational databases (since they are stored in textual files too), etc. )
6. LLM Function Calling systems
	- These are LLM Chatbots which are forced to give ***structured responses***; not plain-text unstructured text.
	- 

![[Pasted image 20240608221227.png]]