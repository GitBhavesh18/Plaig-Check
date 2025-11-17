# PlaigCheck

Small, example plagiarism checker using TF-IDF and cosine similarity.

## Overview

This is a simple teaching/example project that:
- Loads all `.txt` files from the working directory
- Vectorizes documents using `TfidfVectorizer` from scikit-learn
- Computes pairwise cosine similarity between document vectors
- Prints tuples `(fileA, fileB, score)` for each pair

Primary implementation is in `app.py`.

## Requirements

- Python 3.8+
- Install pinned dependency:

```powershell
pip install -r requirements.txt
```

`requirements.txt` currently pins:

- `scikit_learn==0.24.2`

## Running

Place your `.txt` documents in the same directory as `app.py` and run:

```powershell
python .\app.py
```

Example output (sample files included):

```
('john.txt', 'juma.txt', 0.5465972177348937)
('fatma.txt', 'john.txt', 0.14806887549598566)
('fatma.txt', 'juma.txt', 0.18643448370323362)
```

## Notes for contributors and AI agents

- The vectorizer in `app.py` calls `.toarray()` which converts sparse TF-IDF results into dense arrays — this can use a lot of memory for many/large files. Consider returning sparse matrices instead and applying `cosine_similarity` to sparse inputs when scaling.
- `app.py` reads all `.txt` files from the current working directory and uses UTF-8 encoding; preserve that behavior unless explicitly changing the CLI.
- When changing output format, update this `README.md` with usage examples.

## Suggested next steps

- Add an optional CLI flag to specify a directory (`--dir`) and a threshold filter (`--threshold`) to only show scores above a threshold.
- Add tests for `vectorize` and `check_plagiarism` functions.

---
If you want, I can commit this file to the repo and push it to `origin/main` for you. Tell me to proceed and I'll run the git commands.
