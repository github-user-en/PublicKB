> [!info] References
> - https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot

**TL;DR Since the beginning, we at Codeium have always strived to create the best code reasoning system so that our AI can generate the most useful suggestions. Here, we explore one facet of this - how we have built the most advanced code context collection and prompt building, leading to higher quality, fewer hallucinations, and more trust. We show how Codeium uses context to generate better suggestions than another industry leader, GitHub Copilot and CopilotX.**

# [](https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot#background-on-llm-context-awareness)Background on LLM Context Awareness

In the [previous post](https://codeium.com/blog/what-to-know-about-the-context-going-into-your-llm), we started setting the groundwork for a deeper dive into realtime context collection, especially in the space of AI coding assistants, our area of expertise. The short summary is that **all LLMs have some fixed maximum “context length” at inference time** (i.e. amount of information you can pass into the model to reason about), which is often significantly shorter than all of the context that could be relevant. For autocomplete, this limit is usually 2048 tokens (~150 lines of code, primarily for latency reasons), and even for something as powerful as GPT-4, it is only ~32k tokens (a few files of code). Couple this with recent research suggesting that increasing the maximum context length of a model does not necessarily result in better performance, and **it has become clear that the more fruitful path forward in improving LLM performance, at least when it comes to context, is to come up with methods to improve the quality of the context going into a model inference rather than increasing the quantity of said context by upping the model’s maximum context length.**

# [](https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot#context-aware-everything)Context Aware Everything

By Context Aware Everything, we mean building a generic system, ContextModule, that will be able to assemble this ideal context for any model or modality that respects the model’s context length limit. The “Everything” in Context Aware Everything is to highlight that we want to be building a reusable system that will help LLMs generically. For Codeium, we already have both an autocomplete model and a chat model, with different context length limits, but we would like them both to share the same logic to get the best context awareness.

The high-level architecture of the ContextModule is straightforward given how developers subconsciously think about what is relevant as they code:
![[Pasted image 20240714173450.png]]
The ContextModule takes in any inputs and state. For autocomplete, this can be the current file name and cursor position. For chat, this obviously includes the question, but you could also take in the state of the IDE, such as which file is currently active.

The first step is purely an engineering problem to extract all context that could potentially be relevant. This is the code in the current file, imported files, files in the same directory, etc. We could use embeddings to pull in code where similar “tasks” have been done (ex. for autocomplete, we might have some code in the existing file that suggests we are writing a unit test, so it would be useful to know how a fully-completed unit test looks like). This is generic, so we can add more “sources” in the future.

Now, this is way more context than can fit in a prompt, so the second step is reranking. This is where a lot of our magic sauce of using precomputed embeddings comes in to guess the relative importance of various contextual snippets. This logic can, and probably should, differ slightly based on the actual modality (ex. autocomplete vs chat).

Finally, we build up the prompt by adding in context snippets in ranked order until the particular model’s max context length is filled. There’s some other details to make sure the model understands these as different snippets of information, but once built, this is shipped to the model for inference.

All of these stages are generic and are not tied to a particular context source or model. There is a lot left to explore here, but the ContextModule sets us up for success. For example, on the source side, one thing we are actively thinking about is how to ingest non-code sources such as READMEs or design docs. On the reranking and prompt building side, we are exploring how to increase the diversity of context that is passed into the model. But these are all experiments and results for a future day - let’s see some results of the current ContextModule in action.

# [](https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot#experiments-codeium-vs-copilot)Experiments: Codeium vs Copilot

## [](https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot#experimental-setup)Experimental Setup

While it could be interesting to compare Codeium with ContextModule and Codeium without it, we always find it more interesting to compare with the only other AI coding tool that developers truly admire, according to the [most recent StackOverflow developer survey](https://survey.stackoverflow.co/2023/#section-admired-and-desired-ai-developer-tools): GitHub Copilot.