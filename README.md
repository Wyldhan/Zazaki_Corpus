# 📜 Vate Corpus Metadata: A Diachronic Dataset of the Kirmanckî (Zazakî) Kurdish Dialect

This repository contains the structured metadata for the **Vate Corpus**, a comprehensive collection of texts extracted from **Vate Magazine**. Spanning 75 issues, this dataset offers a granular view of literary and non-literary production in **Kirmanckî (Zazakî)**, a dialect of the Kurdish language (Indo-Iranian language family).

This dataset serves as a critical resource for **Low-Resource Language (LRL)** processing, enabling researchers to perform quantitative analysis, genre classification, and sociolinguistic profiling on an under-represented linguistic variety.

---

## 📊 Dataset Statistics

- **Total Records:** 1,397 unique entries  
- **Temporal Span:** Issues Vate-01 through Vate-75  
- **Token Volume:** Aggregated token counts are provided per entry (total corpus size exceeds 1M+ tokens based on cumulative density).  
- **Primary Modality:** Written Text  
- **Format:** Comma-Separated Values (CSV)  

---

## 🗄️ Data Schema & Annotation Standards

The dataset is serialized in `.csv` format with the following feature columns:

| Feature Label   | Data Type     | Description                          | Natural Language Processing (NLP) Relevance                         |
|----------------|---------------|--------------------------------------|---------------------------------------------------------------------|
| `No`           | Integer       | Unique Identifier (UID)              | Indexing and retrieval                                              |
| `Issue`        | String/Cat    | Publication Issue ID                 | Diachronic / temporal analysis segments                             |
| `Title`        | String        | Document Header                      | Topic modeling, Named Entity Recognition (NER)                      |
| `Author_Gender`| Categorical   | Gender (Male/Female/Collective)      | Sociolinguistic bias analysis; stylometric profiling                |
| `Author`       | String        | Entity Name                          | Author attribution, stylometry                                      |
| `Pagination`   | String        | Physical location in source          | Reference validation                                                |
| `Genre`        | Categorical   | Text taxonomy (e.g., Poetry, Article, Memoir) | Document classification, domain adaptation training       |
| `Token_Count`  | Integer       | Length magnitude                     | Normalization, frequency distribution analysis                      |

---

## 🧬 Linguistic and NLP Applications

### 1. Corpus Construction & Curation

- **Balanced Sub-sampling:** Use `Genre` and `Token_Count` to create balanced training/validation/test splits for language models (LMs).  
- **Low-Resource Benchmarking:** Provides a structured index for gathering raw text data to train embeddings (Word2Vec, GloVe, BERT variants) for Zazakî.

### 2. Stylometry & Author Attribution

The `Author` and `Author_Gender` features allow for supervised learning tasks in authorship attribution and the analysis of gendered lexical variation.

### 3. Genre Classification

The dataset includes diverse discourse types (`Editorial`, `Poetry`, `Interview`, `Scientific Article`, `Folklore Review`). This richness supports the training of text classifiers to distinguish between narrative, expository, and lyrical structures in Kurdish.

### 4. Diachronic Analysis

By tracking `Token_Count` and `Genre` distribution across `Issue` (Vate-01 to Vate-75), researchers can analyze the lexical expansion and standardization of the Zazakî dialect over time.

---

## 📈 Distribution Highlights

Based on the metadata, the corpus exhibits a “long tail” distribution common in literary magazines:

- **High Frequency Genres:** Poetry, Articles, and Short Stories  
- **Specific Domain Entities:** Interviews and Folklore Reviews (essential for oral history and dialectological studies)

---

## 💻 Usage

Example of loading the dataset using Python and Pandas for preliminary Exploratory Data Analysis (EDA):

import pandas as pd

# Load the metadata
df = pd.read_csv("Vate_75_Corpus.csv")

# Inspect genre distribution
print(df["Genre"].value_counts())

# Calculate total token count estimate
total_tokens = df["Token_Count"].sum()
print(f"Total Corpus Token Count: {total_tokens}")

# Filter for specific linguistic analysis (e.g., Interviews only)
interviews = df[df["Genre"].str.contains("Interview", case=False, na=False)]---

## ⚠️ Limitations & Ethical Considerations

- **Metadata Only:** This repository contains **metadata** and token counts, not the full raw text content.  
- **Dialect Variation:** While primarily Kirmanckî (Zazakî), titles or specific entries may contain code-switching with Kurmanjî or Turkish, reflecting the sociolinguistic reality of the region.  
- **Bias:** `Author_Gender` is manually annotated and may reflect historical publishing biases (e.g., class imbalance between male/female authors).

---

## 📝 Citation

If you utilize this metadata for computational linguistics research, please cite the source:
tex
@misc{vate_corpus_metadata,
  title     = {Vate Magazine Metadata: A Zazakî Kurdish Dialect Corpus Resource},
  year      = {2025},
  publisher = {Veysel Yıldızhan},
  note      = {Data extracted from Vate Issues 1–75}
}
