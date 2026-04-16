# 3.1 Theoretical Background

# 3.1.1 Overview
In the previous chapters we saw that with LLMs we can automate many research workflows. At first glance this is pretty amazing, mindblowing in fact. But is this enough? 

The limitation with LLMs is that while they can provide responses (ie. "think") they cannot "act". For example you can ask an LLM "What are common tumor suppressing proteins in humans?". The LLM will use its internal knowledge and provide an answer. 

But it can't take any actions beyond that. For example if you ask "Can you provide literature publications to support your answer?" it can't go to Google Scholar and find papers for you.

This is where AI agents come into play. Agents are **autonomous systems** which are simply LLMs integrated with external **tools**. Tools are added functionalities such as a calculator, web-surfing, etc.  

```{figure} ../figures/agent_definition.png
:alt: ai agent
:align: center
:figclass: caption-centered

Figure 3.1.1: The Anatomy of an LLM Agent. The LLM works here as the main "decision maker". Invoking the tools enables the LLM to have improved/specialized skills.  
```

>[!Tip]
> Agents = LLM + Tools

**Here are some example use cases of AI agents in science**
- Searching the literature - see section 2.2 for an example implementation

- Automating data analysis

- Generating hypotheses

- Evaluating models/agents

- Writing technical reports

In more detail, the modern idea of AI agents connects closely with **reinforcement learning (RL)**. In accepted modern practice RL provides the mathematical formulation to the AI agents that we will be using.

# 3.1.2 Definitions based on RL formulation

**Agents:**

In simplest terms an AI Agent is an LLM with externally incorporated tools. But by definition, an agent is an entity that interacts with an **environment**, perceives **states**, chooses **actions**, and receives **rewards**. This flow can be described with a **Markov Decision Process (MDP)**. This also means that the current state of an agent only depends on the state before that.

In other words, a single cell can be thought of as an agent: it senses chemical signals (current state), decides to move or release signals (action), and this all happens in its environment. That’s basically an agent acting in an environment!

There are different "types" of AI agents, eg: Simple Agents, ReAct Agent. Read more [here](https://www.notion.so/futurehouse/Simple-and-ReAct-24f3f583b6908087a8d7e3a79900da3c?source=copy_link)


**Environments:**

The agent observes or senses the environment — like how a biologist might observe cell behavior under a microscope. The environment is everything outside the agent that it can interact with. This could be:
- A virtual environment (like a game world or a simulation)

- The real world (a robot moving around a lab)

- A dataset or a web API

**States:**

The state is a snapshot of the agent’s current situation. ie. what the agent knows. It includes everything relevant to making a decision. For a cell agent, this might be the concentration of nutrients nearby. For a software agent, it might be data it has gathered. You can think of the state as the agent’s **memory or current understanding** of the environment.

**Tools**

An agent uses tools to improve its performance. Think of tools as **resources or specialized skills** the agent can call on. For example, an AI agent answering biology questions might use a database of research papers as a tool. A robot might have a microscope or a pipette as a physical tool. In software, tools might be APIs, calculators, or data analysis modules.


In the following sections let's see how to deploy an agent 

# 3.1.3 Let's recap
Key Concepts to Remember

| Concept | Plain English |
|---------|--------------|
| **Agent** | An AI that can use tools, not just answer questions |
| **Tool** | A Python function the AI can choose to call |
| **Tool schema** | The "label" on the tool so the AI knows what it does |
| **Agent loop** | The cycle of: think → call tool → observe → think again |
| **stop_reason** | How the AI tells us: "I need a tool" vs "I'm done" |


# 3.1.4 Additional Reading
- More mathematical explanations can be found in this paper: [Aviary: training language agents on challenging scientific tasks](https://arxiv.org/abs/2412.21154)
- [AI Agents - IBM tutorials](https://www.ibm.com/think/topics/ai-agents)