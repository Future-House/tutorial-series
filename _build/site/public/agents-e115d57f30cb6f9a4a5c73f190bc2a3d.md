# 3.1 Theoretical Background

In the previous chapters we saw that with LLMs we can automate many research workflows. At first glance this is pretty amazing, mindblowing in fact. But is this enough? 

The limitation with LLMs is that while they can provide responses (ie. "think") they cannot "act". For example you can ask ChatGPT "What are common tumor suppressing proteins in humans?". LLM will use its internal knowledge and provide an answer. 

But it can't take any actions beyond that. For example if you ask "Can you provide literature publications to support your answer?" it can't go to Google Scholar and find papers for you.

This is where AI agents come into play. Agents are **autonomous systems** which are simply LLMs integrated with external **tools**. Tools are added functionalities such as a calculator, web-surfing, etc.  

>[!Note]Not
> Agents = LLM + Tools

In more detail, the modern idea of **AI agents** connect closely with reinforcement learning (RL) but it actually runs deeper than that. Read more on *cybernetics* and *classical AI* if you're interested.

However, RL provide the mathematical formulation to the AI agents that we will be using.

## Few definitions

**Agents:**

In simplest terms an AI Agent is an LLM with externally incorporated tools. But by definition, an agent is an entity that interacts with an **environment**, perceives **states**, chooses **actions**, and receives **rewards**. This flow can be described with a **Markov Decision Process (MDP)**. This also means that the current state of an agent only depends on the state before that.

$s_t \rightarrow A_t \rightarrow R_{t+1},S_{t+1}$

In other words, a single cell can be thought of as an agent: it senses chemicals around it (input), decides to move or release signals (action), and this all happens in its environment. That’s basically an agent acting in an environment!

There are different "types" of AI agents, eg: Simple Agents, ReAct Agent. Read more [here](https://www.notion.so/futurehouse/Simple-and-ReAct-24f3f583b6908087a8d7e3a79900da3c?source=copy_link)


**Environments:**

The agent observes or senses the environment — like how a biologist might observe cell behavior under a microscope. The environment is everything outside the agent that it can interact with. This could be:
- A virtual environment (like a game world or a simulation)

- The real world (a robot moving around a lab)

- A dataset or a web API

**States:**

The state is a snapshot of the agent’s current situation. ie. what the agent knows. It includes everything relevant to making a decision. For a cell agent, this might be the concentration of nutrients nearby. For a software agent, it might be data it has gathered. You can think of the state as the agent’s **memory or current understanding** of the environment.

**Tools**

Agents use tools to improve its performance. Think of tools as **resources or specialized skills** the agent can call on. For example, an AI agent answering biology questions might use a database of research papers as a tool. A robot might have a microscope or a pipette as physical tools. In software, tools might be APIs, calculators, or data analysis modules.


**A few examples of how to use agents in research:**

- Literature search

- Automating data analysis

- Hypothesis generation

- Evaluating models,agents

- Write technical reports



## <font color="purple"> Standard approaches to deploying agents </font>

Anthtopic has released an open-source protocol known as Model Context Protocol (MCP) to standardize the these practices. Read more [here](https://www.anthropic.com/news/model-context-protocol).

MCP can be used to connect "AI assistants to the systems where data lives, including content repositories, business tools, and development environments." There are many off-the-shelf tools and code snippets to build your own agents.

Here are some useful resources:

- [what is an MCP?](https://www.youtube.com/watch?v=eur8dUO9mvE)
- [MCP vs API](https://www.youtube.com/watch?v=7j1t3UZA1TY)
- [Concepts of MCP](https://modelcontextprotocol.io/docs/learn/architecture)

## <font color="blue"> AI Safety </font>

AI safety is about ensuring that AI systems:

- Do what we intend them to do
- Do not cause harm (to individuals, society, or science)
- Remain reliable and controllable as they become more capable

AI systems are increasingly used in high-stakes domains (medicine, science, hiring, policy), used autonomously or semi-autonomously. This creates many  risks such as:

- Incorrect but confident outputs (hallucinations)
- Bias and unfair outputs
- Misuse or unintended consequences

Therefore, we have to ensure that we take safety measures during and post training. The commercial LLMs usually go through alignment and red teaming efforts before they release their models. But still it is not uncommon to jailbreak these models.

References:
- https://ai.google/safety/
- https://safe.ai/
- https://www.aisi.gov.uk/

**Why this matters for scientists?**

Reproducibility and trusworthiness in data is cruitial in science. For example, in most cases we work with sensitive data or proprietory. eg: virus data, business information. Or in other cases errors can propagate into publications. Therefore, using AI responsibly is part of scientific rigor.