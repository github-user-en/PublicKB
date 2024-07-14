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
![[Pasted image 20240714175954.png]]
While of course we will pit the two autocomplete capabilities against each other, this post has great timing because GitHub finally released their Chat capability as part of CopilotX into beta, over four months after they announced it. This means we can compare the chat products against each other, and since CopilotX has presumably been working on Chat for longer than the capability has been released on Codeium, we should expect it to be pretty good.

In terms of the task, we will work on a project using Langchain. Langchain is an exciting open source project building a framework for prompt engineering LLM agents to do sophisticated tasks, layering multiple actions (Tools) with an LLM Agent that can plan for the Tools in use.

Let’s experiment with a simple task where we are working with Langchain and we want to add a simple `StacktraceDebugger` agent to simulate what a software engineer would do when faced with an issue. Just like any engineer, the debugger looks at a stacktrace, analyzes it, and decides what to do: if it doesn’t know what’s going on, it might Google the problem or open up the file to take a look.

## [](https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot#autocomplete)Autocomplete

Let’s assume we’ve started working on our `StacktraceDebugger`, and we have the start of a class here:
```python
import langchain.agents.mrkl.base as mrkl

from langchain.utilities.serpapi import SerpAPIWrapper
from langchain.tools.file_management import ReadFileTool

from langchain.llms import OpenAI

class StacktraceDebugger():
   """
   Create an agent that uses MRKL chain as a basic agent to use tools to read
   files to analyze a stacktrace and explain the issue.
   """

   # Initialize debugger with search and readfile tools

```
How will the ContextModule help with autocomplete?

### [](https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot#task-1-declaring-chainconfigs)Task 1: Declaring ChainConfigs

If you’re not already familiar, the `ChainConfig` class (below) describes the Tools that the Langchain MRKL (Modular Reasoning, Knowledge and Language) implementation has access to.

```python
class ChainConfig(NamedTuple):
   """Configuration for chain to use in MRKL system.

   Args:
       action_name: Name of the action.
       action: Action function to call.
       action_description: Description of the action.
   """
```

So, a critical part of initializing the agent is assembling the right list of `ChainConfig`s for the Tools that we want: a websearch Tool, and a file reading Tool.

Let’s see how Codeium with ContextModule does here:
.
.
.
`skipped the intervening writeup... the jist was that Github CoPilot was a standalone llm, while Codeium uses a RAG architecture, allowing for contextual answers... Codeium keeps creating embeddings of your codebase for its RAG to work.`
.
.
.
Again, the lack of context is unfortunately glaringly obvious. It has no idea what MRKL is but just makes up something assuming that MRKL is some kind of debugging keyword extractor. Worse, when pushed for more details on implementation, it simply hallucinates a class and a method that simply do not exist.

# [](https://codeium.com/blog/context-aware-everything-more-advanced-realtime-context-than-github-copilot#final-thoughts-on-context-awareness)Final Thoughts on Context Awareness

**At Codeium, we have built the industry’s most advanced context awareness engine, which we call the ContextModule, to dramatically improve the quality and usefulness of suggestions across all of our modalities, including Autocomplete and Chat.** This is the latest of a list of technical achievements that have put Codeium in front of other industry leaders, following improvements like [inline Fill-in-the-Middle](https://codeium.com/blog/inline-fim-code-suggestions) and [model fine-tuning](https://codeium.com/blog/what-github-copilot-lacks-finetuning-on-your-private-code). We know that others will continue to try to catch up to Codeium’s capabilities, so we are excited to keep researching and developing to push the boundaries.

In the next post of this series, we will discuss a number of interesting considerations as we productionized this system so that it is something that any developer and any company can use and trust.

And if you want to see ContextModule in action yourself, just try Codeium out - it’s free!