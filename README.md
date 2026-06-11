# Atlas Auto-Embedding Notebook Setup

This project is prepared for a Jupyter notebook experiment using MongoDB Atlas and `pymongo`.

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

## 5) Optional kernel registration

If you want a dedicated kernel in Jupyter UI:

```bash
python -m ipykernel install --user --name atlas-auto-embedding-voyage --display-name "Python (atlas-auto-embedding-voyage)"
```
