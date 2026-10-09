# UAE Visa Q&A: RAG Project (Week 1: Semantic Search)

A step-by-step build of a Retrieval-Augmented Generation (RAG) assistant that answers questions about UAE visas and cites its sources. This repo is a learning log, and the plan runs for six weeks.

**Status:** Week 1 of 6 complete (embeddings and similarity search).

## What Week 1 does

The notebook `01_embeddings_similarity_search.ipynb` shows how to search text by *meaning* instead of exact words:

1. Load a small free embedding model (`all-MiniLM-L6-v2`, from Hugging Face).
2. Turn sentences and a question into embeddings (lists of numbers).
3. Rank the sentences by cosine similarity to the question and print the top 3.

## Results

| Question | Best score | What happened |
|---|---|---|
| How long is a skilled worker's residence valid? | 0.83 | Correct sentence ranked first |
| How early birds start chirping in morning? (nothing relevant in the data) | 0.16 | All scores low, a signal there is no good match |
| I have MS robotics and AI degree, can I get the visa? | 0.83 | Found the degree-requirement sentence |
| I got AED 20,000 salary job, will I get visa? | 0.75 | Found the salary sentence, but search alone can't say yes or no |

## What I learned

- Search by meaning works even with typos in the question.
- A low top score means "no good answer here". The app needs a minimum-score cutoff.
- Retrieval finds the relevant text but does not reason over it. A language model is needed for the final answer (Week 3).
- Answers are only as good as the source text. Official, dated documents are required.

## Disclaimer

The visa sentences in the notebook are practice text, not verified official rules. This is not legal or immigration advice. Visa rules change often, so check ICP, GDRFA and MOHRE for current requirements.

## Run it

Open the notebook in Kaggle or Colab (internet on), run the cells in order. Requires `sentence-transformers`.

## Roadmap

- [x] Week 1: embeddings and similarity search
- [ ] Week 2: ingest official PDFs, chunking, store in Chroma
- [ ] Week 3: retrieve and answer with an LLM, with citations
- [ ] Week 4: evaluation (test questions, retrieval hit rate)
- [ ] Week 5: FastAPI, UI, Docker
- [ ] Week 6: deployment and demo
