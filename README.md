# Atlas Auto-Embedding Notebook Setup

This project is prepared for a Jupyter notebook experiment using MongoDB Atlas and `pymongo`.

## Notebook overview

This repository includes two lab notebooks with different goals:

1. `atlas_auto_embedding_experiment.ipynb`
	- Intention: provide a quick end-to-end baseline for Atlas auto-embedding and vector search behavior.
	- Brief intro: this notebook connects to Atlas, creates a vector index with `autoEmbed`, and compares symmetric vs asymmetric query-time model usage for retrieval quality, latency, and estimated cost.

2. `atlas_auto_embedding_reembed_case.ipynb`
	- Intention: demonstrate how document updates trigger automatic re-embedding and affect ranking results.
	- Brief intro: this notebook seeds sample product data, performs pre-update retrieval checks, updates a target document, and then polls search results until the new intent is reflected by the index.

## 1) Create and activate virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 2) Install dependencies

```bash
pip install -r requirements.txt
```

## 3) Configure environment variables

```bash
cp .env.example .env
```

Then edit `.env` and set at least:

- `MONGODB_ATLAS_URI`
- `ATLAS_DB_NAME` (optional default exists)
- `ATLAS_COLLECTION_NAME` (optional default exists)
- `VOYAGE_API_KEY` (only if your model provider integration requires it)

## 4) Start notebook

```bash
jupyter notebook
```

Open `atlas_auto_embedding_experiment.ipynb` and run cells in order.

## 4.1) Re-embed case lab notebook

To run the re-embedding lab, open `atlas_auto_embedding_reembed_case.ipynb` and run cells in order.

Important: this lab includes placeholders that must be filled before execution.

You must replace all `<CODE_BLOCK*>` tokens in:

- Cell 7 (index definition)
- Cell 8 (vector search helper)

<details>
<summary>Suggested values (click to expand)</summary>

- `<CODE_BLOCK1>`: `autoEmbed`
- `<CODE_BLOCK2>`: `description`
- `<CODE_BLOCK3>`: `voyage-4-large`
- `<CODE_BLOCK4>`: `1024`
- `<CODE_BLOCK5>`: `INDEX_NAME`
- `<CODE_BLOCK6>`: `description`
- `<CODE_BLOCK7>`: `query_text`

</details>

Quick check before running the lab:

- In the notebook, search for `CODE_BLOCK` and confirm there are no remaining matches.
- Ensure `.env` has `MONGODB_ATLAS_URI` set.
- Optionally set `ATLAS_DB_NAME` and `ATLAS_CASE_COLLECTION_NAME` in `.env`.

If any `<CODE_BLOCK*>` placeholders remain, the lab will fail to run.

## 5) Optional kernel registration

If you want a dedicated kernel in Jupyter UI:

```bash
python -m ipykernel install --user --name atlas-auto-embedding-voyage --display-name "Python (atlas-auto-embedding-voyage)"
```
