# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository is a Japanese translation of Stanford's [CS231n: Deep Learning for Computer Vision](https://cs231n.stanford.edu/) course. It has two components:

1. **Assignment source code** (`src/`) — Python implementations of neural network components from the original Stanford assignments
2. **Lecture documentation** (`docs/`) — Japanese-translated lecture notes published as a static site via MkDocs

## Development Setup

Package management uses [uv](https://docs.astral.sh/uv/). Python version is pinned to 3.11 in `.python-version`.

```bash
uv sync                   # install all dependencies (includes dev group)
uv sync --only-group docs # install only docs dependencies
```

### Running Notebooks (Jupyter Lab)

```bash
uv sync
uv run ipython kernel install --user --env VIRTUAL_ENV $(pwd)/.venv --name=project
uv run --with jupyter jupyter lab
```

## Key Commands

### Pre-commit (required before every commit)

```bash
nbdev_clean       # strip notebook metadata/outputs
ruff format .     # format Python code
```

CI enforces both of these — PRs will fail if notebooks have unclean metadata or code is unformatted.

### Docs

```bash
uv run mkdocs serve   # local preview server
uv run mkdocs build   # build static site to site/
```

### Code Quality

```bash
uv run ruff format --check .   # check formatting without applying
```

## Architecture

### Assignment Code Structure

Both `src/assignment1/` and `src/assignment2/` follow the same layout:

- `cs231n/layers.py` — Core layer implementations as standalone functions. Each layer exports a `*_forward(inputs) -> (out, cache)` and `*_backward(dout, cache) -> grads` pair. The `cache` tuple holds everything needed for the backward pass.
- `cs231n/classifiers/` — Model classes (e.g., `fc_net.py`, `cnn.py`) that compose layers from `layers.py` and expose a `loss(X, y)` method returning `(loss, grads)`.
- `cs231n/solver.py` — Training loop (`Solver` class). Takes a model and data dict, handles SGD variants defined in `optim.py`, tracks train/val accuracy history.
- `cs231n/optim.py` — Update rules (sgd, sgd_momentum, rmsprop, adam) as pure functions with signature `(w, dw, config) -> (next_w, config)`.
- `*.ipynb` — Notebooks that import the cs231n package and contain the student exercises (marked with `# TODO` blocks between `# *****START OF YOUR CODE` and `# *****END OF YOUR CODE` delimiters).

Assignment 2 additionally has:
- `cs231n/fast_layers.py`, `cs231n/im2col.py`, `cs231n/im2col_cython.pyx` — Optimised convolution via im2col; the `.pyx` file requires Cython compilation via `cs231n/setup.py`.

### Docs Structure

`docs/` contains Markdown files organized by lecture (`lecture2/` through `lecture8/`). Each lecture folder has an `index.md` overview and one or more topic pages. MkDocs with the Material theme renders these; navigation is declared explicitly in `mkdocs.yml`.

Math is rendered via MathJax (configured in `docs/assets/js/mathjax.js`). Use `pymdownx.arithmatex` fenced blocks for inline and display math in Markdown.

### CI

- **CI workflow** (`.github/workflows/ci.yaml`) — runs `ruff format --check` and `nbdev_clean` (checking that notebooks have no dirty metadata after cleaning).
- **Docs workflow** (`.github/workflows/docs.yaml`) — builds and deploys the MkDocs site to GitHub Pages on pushes to `main` that touch `docs/`, `mkdocs.yml`, or related files.

## Dataset Download

Datasets are not committed. Download scripts live inside each assignment:

```bash
cd src/assignment1/cs231n/datasets && bash get_datasets.sh   # CIFAR-10
cd src/assignment2/cs231n/datasets && bash get_datasets.sh
```

## Language

All documentation in `docs/` is written in Japanese. Code comments in `layers.py` and similar files contain both English (original) and Japanese (translation) docstrings. Keep this bilingual pattern when modifying those files.
