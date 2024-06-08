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
	- These are LLM systems which are empowered to interact with external ***tools*** (which may be python functions or APIs).
	- Since functions and APIs can only understand and can only output structured responses, to facilitate these interactions, LLM Chatbots are forced to give ***structured responses***.
	- The format of the ***structured response*** in the LLM space is almost universally that of a JSON object. The only exception to this rule is Anthropic's LLM systems which use the XML format. 
> [!info]
> As stated earlier, the capabilities of LLM-RAG and LLM-Function Calling Systems, when put together, lead us to LLM Agent systems.

7. LLM Agents
	- ![[Pasted image 20240608224008.png]]The above picture demonstrates how LLM Agents were leveraged to create [BabyAGI](https://babyagi.org/).
	- LLM Agents are able to leverage both RAG and Tool calling capabilities.

![[Pasted image 20240608221227.png]]