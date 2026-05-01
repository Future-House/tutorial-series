# Practical AI for Scientists — FutureHouse Tutorial Series

Interactive tutorials for scientists who want to use AI in research: core concepts, large language models in biology, and LLM agents. Content is written in Markdown and Jupyter notebooks and published with [MyST](https://mystmd.org/).

**Repository:** [github.com/Future-House/tutorial-series](https://github.com/Future-House/tutorial-series)

## View the book

After deployment, the site is served with GitHub Pages (path `/tutorial-series` in CI). Open:

**[https://future-house.github.io/tutorial-series/](https://future-house.github.io/tutorial-series/)**

If the URL differs (fork, custom domain), check **Settings → Pages** for the live address.

## Run notebooks in Google Colab

Colab opens notebooks from this repo using the `.ipynb` paths below (replace `main` if you use another default branch):

| Notebook | Open in Colab |
|----------|----------------|
| LLMs for biology | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_2/llms_for_biology.ipynb) |
| UniProt example | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_2/uniprot_example.ipynb) |
| Agent implementation | [Colab](https://colab.research.google.com/github/Future-House/tutorial-series/blob/main/chapter_3/agent_implementation.ipynb) |

The published site also includes Colab links in the header navigation (`myst.yml`).

## Build locally

Requires Python 3.11+ (same as CI).

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install mystmd jupyter-book
myst build --html
```

Output: `_build/html/`. To match GitHub Pages base path when testing:

```bash
BASE_URL=/tutorial-series myst build --html
```

## Repository layout

| Path | Contents |
|------|----------|
| `myst.yml` | Project config, table of contents, site theme, Colab nav links |
| `index.md` | Landing page |
| `chapter_1/` | Introduction (background, models, LLMs for biology) |
| `chapter_2/` | Applications in biology; interactive notebooks |
| `chapter_3/` | LLM agents; `agents.md` and `agent_implementation.ipynb`, `avairy_agent_implementation.ipynb`|
| `resources/` | Glossary |
| `.github/workflows/deploy.yml` | Build and deploy to GitHub Pages on push to `main` |

## License and copyright

Copyright 2026 FutureHouse. See repository settings for license terms if applicable.
