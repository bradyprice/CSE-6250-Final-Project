
# SurfCon-Inspired Synonym Discovery

This project reproduces and extends components of the **SurfCon** paper for synonym discovery using both surface form and contextual information. It includes implementations for:

- CharNGram-based surface similarity
- GloVe/Word2Vec-based semantic similarity
- NPMI-based contextual similarity
- Hybrid models combining the above

Original paper repo link: https://github.com/yzabc007/SurfCon
---

## Project Structure

```
.
├── final_code.ipynb
├── 1_term_ID_to_string.txt
├── 2a_concept_ID_to_string.txt
├── 3_term_ID_to_concept_ID.txt
├── singlets_concepts_perBin_1d.txt
├── cofreqs_concepts_perBin_1d.txt
├── charNgram.txt
├── glove.6B.50d.txt
└── ...
```

---

## Setup Instructions

### Clone the Repository

```bash
git clone https://github.com/bradyprice/CSE-6250-Final-Project.git
cd surfcon-synonym-discovery
```

---

## Required Files

Place the following files in your working directory:

| File Name                         | Description |
|----------------------------------|-------------|
| `1_term_ID_to_string.txt`        | Maps term IDs to string forms |
| `2a_concept_ID_to_string.txt`    | Maps concept IDs to string forms |
| `3_term_ID_to_concept_ID.txt`    | Maps term IDs to concept IDs |
| `singlets_concepts_perBin_1d.txt`| Singleton frequencies of terms |
| `cofreqs_concepts_perBin_1d.txt` | Term co-occurrence frequencies |
| `charNgram.txt`                  | Pretrained char n-gram embeddings (download [here](https://github.com/hassyGo/charNgram2vec/releases)|
| `glove.6B.50d.txt`               | GloVe word vectors (download [here](https://nlp.stanford.edu/data/glove.6B.zip)) |

---

## Running the Notebook

Run `final_code.ipynb` from Context - top to bottom. It will:

1. Load all term/concept mappings and frequencies
2. Compute CharNGram-based surface embeddings
3. Load GloVe embeddings and compute semantic similarity
4. Construct a contextual similarity matrix using NPMI
5. Evaluate synonym suggestions using individual and hybrid models

You can modify the target term in the code (e.g., `"leukemia"`) to explore synonyms for different queries.

---

## Outputs

The notebook prints out:

- Top CharNGram-based synonyms
- Top GloVe-based synonyms
- Top NPMI-based contextual synonyms
- Top hybrid (combined) synonyms

Each output includes similarity scores to the query term.

---

## Evaluation

You may evaluate model quality using MAP (Mean Average Precision) against a gold standard set of synonym clusters (e.g., from UMLS MRCONSO.RRF).

---

## Notes

- This project adapts code to reduce memory footprint where possible.
- PMI computation is chunked and saved to disk to avoid OOM errors.

---

## Authors

- Brady Price
- Dinesh Sathanencheri Suresh
