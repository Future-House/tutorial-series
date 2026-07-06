# Practical AI for Scientists — FutureHouse Tutorial Series

Interactive tutorials for scientists who want to use AI in research: core concepts, large language models in biology, and LLM agents. Content is written in Markdown and Jupyter notebooks and published with [Jupyter Book](https://jupyterbook.org/).

**Repository:** [github.com/Future-House/tutorial-series](https://github.com/Future-House/tutorial-series)

## View the book

After deployment, the site is served with GitHub Pages. Open:

**[https://future-house.github.io/tutorial-series/](https://future-house.github.io/tutorial-series/)**

If the URL differs (fork, custom domain), check **Settings → Pages** for the live address.

## Run notebooks in Google Colab

Coding tutorials can also be opened directly in Colab (replace `main` if you use another default branch). The published site also includes Colab and Binder launch buttons (🚀) in the notebook header via `_config.yml`.

| Notebook | Open in Colab |
|----------|----------------|
| LLMs for biology (2.2) | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_2/2.2.llms_for_biology.ipynb) |
| External databases (2.3) | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_2/2.3.external_databases.ipynb) |
| Aviary agent implementation (3.2) | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_3/3.2.aviary_agent_implementation.ipynb) |
| Ant agent implementation (3.3) | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_3/3.3.ant_agent_implementation.ipynb) |
| Agent MCP example (3.4) | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_3/3.4.agent_mcp_example.ipynb) |
| Python basics (4.2) | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/resources/4.2.python_basics.ipynb) |

Before running notebooks that call LLM APIs, set your keys in a `.env` file or Colab Secrets. See `index.md` for details.

## Build locally

Requires Python 3.11+ (CI uses 3.13).

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter-book build .
```

Output: `_build/html/`. Open `_build/html/index.html` in a browser to preview.

## Repository layout

| Path | Contents |
|------|----------|
| `_config.yml` | Book config, launch buttons (Colab/Binder), theme, analytics |
| `_toc.yml` | Table of contents |
| `index.md` | Landing page |
| `chapter_1/` | Introduction — background, AI models, LLMs in biology |
| `chapter_2/` | Applications in biology — background, LLM notebooks, external databases |
| `chapter_3/` | LLM agents — concepts, Aviary, Ant, and MCP examples |
| `resources/` | Glossary, Python basics notebook, submit-your-work page |
| `.github/workflows/deploy.yml` | Build and deploy to GitHub Pages on push to `main` |

## Table of contents

1. **Introduction** — evolution of AI, model overview, LLMs in biology
2. **Applications of AI in Biology** — LLM workflows and external database queries
3. **LLM Agents** — agent concepts, Aviary and Ant implementations, MCP tooling
4. **Resources** — glossary, Python basics, project submissions

## License and copyright

Copyright 2026 FutureHouse. See repository settings for license terms if applicable.
