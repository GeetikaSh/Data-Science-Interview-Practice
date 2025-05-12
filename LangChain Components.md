# Langchain Components

LangChain is a framework designed to simplify the development of applications powered by Large Language Models (LLMs).
It provides modular building blocks that allow developers to interact seamlessly with various LLMs and extend their capabilities.

There are six core components in LangChain:
1. Models
2. Prompts
3. Chains
4. Memory
5. Indexes
6. Agents

## Models
The Model component is one of the most fundamental parts of LangChain. It represents the core interface through which users interact with AI models.

### Why Models Matter
Previously, each LLM provider—such as OpenAI, Anthropic (Claude), Google (Gemini), and Cohere—had its own API style and message formatting.
This made it cumbersome for developers to switch or integrate multiple LLMs into their applications. LangChain addresses this by standardizing how developers interact with different LLMs.
Through unified interfaces, it abstracts away the low-level API differences, making it easier to switch between or combine models.

### Types of Models in LangChain
LangChain supports interaction with two primary types of models:
1. **Language Models (LLMs)**
* Input: Text
* Output: Text
* Use cases: Chatbots, content generation, question answering, summarization, etc.
* Examples: OpenAI's GPT models, Anthropic's Claude, Cohere’s Command models

2. **Embedding Models**
* Input: Text
* Output: Vector embeddings (high-dimensional numerical representations of text)
* Use cases: Semantic search, similarity matching, clustering, vector storage with tools like FAISS, Chroma, or Pinecone
* Examples: OpenAI's text-embedding-ada-002, Cohere’s embed-english-v3, etc.

## Prompts
Prompts are the input text (or messages) sent to a Large Language Model (LLM) to guide its response.
Crafting effective prompts is essential for controlling the behavior, tone, and accuracy of the model's output.

LangChain helps in managing and structuring prompts through reusable templates, variables, and prompt engineering techniques.

### Types of Prompting
1. **Few-Shot Prompting**
In this technique, the prompt includes a few examples (input-output pairs) to help the model understand the pattern or format expected in its response.

**Example:**
```vbnet
Q: What is the capital of France?  
A: Paris  
Q: What is the capital of Germany?  
A: Berlin  
Q: What is the capital of Italy?  
A:
```
The LLM will infer that the expected response is “Rome.”

2. **Dynamic and Reusable Prompts**
LangChain allows the use of prompt templates that include placeholders for dynamic values. These templates can be reused across different contexts or applications.

**Example in LangChain:**
```python

from langchain.prompts import PromptTemplate

prompt = PromptTemplate(
    input_variables=["topic"],
    template="Write a short story about {topic}."
)
```

3. **Role-Based Prompting**
Instructs the LLM to assume a specific persona or role while generating responses. Useful in scenarios like customer support, coding assistants, interview simulations, etc.

**Example:**
```less
You are a helpful and friendly customer support agent. Answer the following query politely and professionally:
Customer: I haven’t received my package yet.
```

LangChain enhances prompting by allowing:
* Use of prompt templates
* Composition of multi-part prompts
* Chaining of prompts with model outputs
