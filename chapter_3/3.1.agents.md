# 3.1 Theoretical Background

## 3.1.1 Overview
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

:::{tip}
Agents = LLM + Tools
:::

**Here are some example use cases of AI agents in science**
- Searching the literature - see section 2.2 for an example implementation

- Automating data analysis

- Generating hypotheses

- Evaluating models/agents

- Writing technical reports

In more detail, the modern idea of AI agents connects closely with **reinforcement learning (RL)**. In accepted modern practice RL provides the mathematical formulation to the AI agents that we will be using.

## 3.1.2 Definitions based on RL formulation

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

**3.1.3 Let's recap**

Key Concepts to Remember

| Concept | Plain English |
|---------|--------------|
| **Agent** | An AI that can use tools, not just answer questions |
| **Tool** | A Python function the AI can choose to call |
| **Tool schema** | The "label" on the tool so the AI knows what it does |
| **Agent loop** | The cycle of: think → call tool → observe → think again |
| **stop_reason** | How the AI tells us: "I need a tool" vs "I'm done" |


## 3.1.3 FutureHouse Agents for Scientific Discovery

At FutureHouse, we're  seeking to accelerate scientific research with an AI agents designed to automate many of the critical steps on the path toward scientific progress. We have built a series of AI agents specialized for tasks including information retrieval, information synthesis, chemical synthesis design, and data analysis. 

As introduced in chapter 2, [PaperQA2](https://github.com/Future-House/paper-qa) is our scientific information retrieval system. Our data analysis agent is named [Finch](https://github.com/Future-House/finch). Finch is an AI agent framework designed to perform complex scientific data analysis tasks by iteratively working through Jupyter notebooks. This agent takes in datasets and prompts, then systematically explores, analyzes, and interprets the data to provide comprehensive answers and insights. Then we have [Robin](https://www.futurehouse.org/research-announcements/demonstrating-end-to-end-scientific-discovery-with-robin-a-multi-agent-system), our first multi-agent system for scientific discovery. We applied Robin to identify ripasudil, a Rho-kinase (ROCK) inhibitor clinically used to treat glaucoma, as a novel therapeutic candidate for dry age-related macular degeneration (dAMD), a leading cause of irreversible blindness worldwide. The second iteration of Robin, named [Kosmos](https://edisonscientific.com/articles/announcing-kosmos?gad_source=1&gad_campaignid=23563065812&gbraid=0AAAABB7BYdBNoPj2BU82YRgDuN7FLSbFp&gclid=CjwKCAjwwJzPBhBREiwAJfHRnZ_daxcLWR4IyY7swufHvUA5GBDm-dNoDpG-gSJng_9pe96pNd0ciBoCT7wQAvD_BwE), is our first AI scientist. The core innovation in Kosmos is the use of structured world models, which allow efficient incorporation of information extracted over hundreds of agent trajectories. This also allows the agent to maintain coherence towards a specific research objective over tens of millions of tokens. 


## 3.1.4 Limitations of AI Agents

AI agents are comparatively better at performing domain specific tasks than LLMs by themselves. However, this is does **not** mean they are free of limitations. Let's take a look some limitations AI agents face.

* **Context window constraints** LLMs have a finite context window. In multi-step agentic workflows, the accumulated message history — including tool calls, observations, and reasoning — can quickly approach or exceed this limit. When truncation occurs, the agent loses access to earlier reasoning, which can cause it to repeat steps, contradict itself, or fail entirely.

* **No memory across runs**  By default, agents have no memory between runs. Each new rollout starts from scratch. In other words, the `DemoEnvState` is ephemeral. Once a rollout ends, nothing persists. If we wanted the agent to learn from prior protein analyses, we'd need to add external memory (e.g., a vector store or a structured cache).

*  **Hallucination and unreliable tool outputs** LLMs can generate plausible-sounding but factually incorrect content, especially when answering questions outside their training data or when tool outputs are ambiguous. For example `handle_tool_exc=True` in `step()` method catches tool exceptions and converts them to messages rather than crashing. This is safe, but the agent may not recover gracefully. It might keep retrying a broken tool or hallucinate a result.

* **Error propagation across steps** Agents take sequential actions, so an early mistake; a wrong tool choice, a misinterpreted observation, or a malformed argument can cascade through subsequent steps and compound into a larger failure. Errors are not always recoverable, especially if the agent lacks explicit error-handling logic.

* **Incomplete or premature termination** Agents driven by a fixed step budget may terminate before completing a task, or may call a termination tool too early because the LLM misjudges task completion. Conversely, without a step limit, agents can loop indefinitely on unsolvable tasks.

*  **Limited generalization across tasks** Agents are sensitive to how tools are described and how prompts are framed. A system prompt or tool description that works well for one task may perform poorly on a slightly different one. Agents often lack the robustness to handle out-of-distribution inputs gracefully.

### Mitigations & Performance Improvements

| Limitation | Mitigation|
| --- | --- |
| Context overflow| Summarize or compress old messages; use sliding window memory; set output length limits on tool responses |
| No persistent memory |  memoryAdd a vector store or structured cache to persist and retrieve results across runs |
| Hallucination | Ground LLM outputs with retrieval (RAG); require citations; use tool outputs as the source of truth over model priors |
| Error propagation | Add explicit error handling and retry logic; validate tool inputs/outputs before passing them downstream |
| Premature/no termination | Check for termination signals after every step; set sensible step budgets based on task complexity|
| Poor generalization | Invest in prompt engineering and tool description clarity; test on diverse inputs; use few-shot examples in the system prompt |

### Evaluating agent performance 

This is as important as building the agent itself. Rather than just inspecting final outputs, consider:

- Trajectory analysis: did the agent take the most efficient path, or did it waste steps?
- Tool use accuracy: did it call the right tools with valid arguments?
- Failure mode logging: track when and why agents fail to complete tasks, to guide future improvements

Frameworks like LDP and Aviary are designed with evaluation in mind: trajectories are structured objects you can analyze programmatically, making it straightforward to build automated eval pipelines on top of your existing rollout infrastructure.

## 3.1.5 Additional Reading
- More mathematical explanations can be found in this paper: [Aviary: training language agents on challenging scientific tasks](https://arxiv.org/abs/2412.21154)
- [AI Agents - IBM tutorials](https://www.ibm.com/think/topics/ai-agents)

## Providing Feedback

We’d love to hear from you! Whether you run into issues, have ideas for improving the tutorials, or want to suggest new topics, feel free to reach out. 

Email us at: [tutorials@futurehouse.org](tutorials@futurehouse.org)