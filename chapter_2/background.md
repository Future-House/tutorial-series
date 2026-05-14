# 2.1 Overview

This chapter focuses on **practical applications** of AI in biological research. The goal is to provide scientists with hands-on `python` examples that demonstrate how modern AI tools can be integrated into everyday research workflows.

These examples illustrate how large language models and related AI systems can accelerate tasks such as analyzing datasets, extracting information from scientific literature, and building intelligent research assistants.

These examples will teach you how to build AI systems that:

- Query and summarize scientific literature

- Build retrieval systems that search large collections of papers or data

- Extract structured information from online, open-source datasets

The accompanying `python notebooks` provide step-by-step implementations that readers can run and modify for their own research projects. These notebooks demonstrate techniques such as retrieval-augmented generation (RAG) for literature search and LLM model–based dataset parsing for biological data analysis.

:::{admonition} 🚀 How to run the notebooks

Tutorials can be launched using the rocket (🚀) button at the top of the page.

### Option 1 — Google Colab (**recommended**)
Opens the notebook in Google Colab with the fastest and most reliable experience.

Before running the tutorial, add your API keys using **either**:

- a `.env` file, or
- **Colab Secrets** (`🔑 Secrets` tab in the left sidebar)

Example `.env`:
```bash
OPENAI_API_KEY=your_key_here
ANTHROPIC_API_KEY=your_key_here
```

### Option 2 — MyBinder
Launches a temporary cloud Jupyter environment directly in your browser.

⚠️ Binder environments can take a few minutes to build and start.

After the notebook loads, create a `.env` file in the notebook directory containing your API keys:

```bash
OPENAI_API_KEY=your_key_here
ANTHROPIC_API_KEY=your_key_here
```

### Notes
- You only need API keys for the providers used in a given notebook.
- Never commit or publicly share your API keys.
- If a cell fails due to missing credentials, verify that your keys were loaded correctly before rerunning the cell.
:::

**Provide Feedback**

We’d love to hear from you! Whether you run into issues, have ideas for improving the tutorials, or want to suggest new topics, feel free to reach out. 

Email us at: [tutorials@futurehouse.org](tutorials@futurehouse.org)