# 🎯 RedRob Hackathon — Intelligent Candidate Recovery

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-DataFrames-150458?logo=pandas&logoColor=white)
![SentenceTransformers](https://img.shields.io/badge/SentenceTransformers-MiniLM--L6-orange)
![BM25](https://img.shields.io/badge/Retrieval-BM25-green)
![Runtime](https://img.shields.io/badge/Runtime-5--7%20min%20(CPU)-yellow)
![Status](https://img.shields.io/badge/Status-Submitted-success)

A retrieval + scoring pipeline that ranks **~100,000 candidate profiles** against a job description — fast, explainable, and resistant to gamed/honeypot profiles.

---

## 🚀 What it does
- Filters out irrelevant (Tier-D) roles & honeypot profiles **before** embedding — cuts corpus 40–60%
- Embeds candidates once using `all-MiniLM-L6-v2`
- Hybrid retrieval: **semantic (cosine similarity) + lexical (BM25)**
- Scores shortlist on a weighted composite: Role Fit, Experience, Skills, Location, Education, GitHub
- Applies an **availability multiplier** (recency, notice period, response/interview rates)
- Outputs Top 100 ranked candidates with auto-generated reasoning

## 🧱 Tech Stack
| Component | Purpose |
|---|---|
| Python, Pandas, NumPy | Data processing & vectorized scoring |
| sentence-transformers (MiniLM-L6-v2) | Semantic embeddings |
| rank-bm25 | Lexical keyword retrieval |
| scikit-learn / regex | Role classification, concept matching |
| PyArrow / Feather | Fast dataframe caching |
| python-docx | Parsing JD & spec docs |
| Google Colab + Drive | Execution environment |

## ⚙️ How to run
```bash
pip install sentence-transformers rank-bm25 numpy pandas tqdm scikit-learn python-docx pyarrow
```
1. Place `candidates.jsonl`, `job_description`, `redrob_signals_doc`, `submission_spec` in your data folder
2. Update `folder` path in Cell 2
3. Run all cells → `submission.csv` generated with `candidate_id, rank, score, reasoning`

## 📊 Output
- **Runtime:** 5–7 min on CPU
- **Format:** `submission.csv` — Top 100 ranked, scored & explained candidates

## 👥 Team
**Amit Sharma** · **Keshav Varshney**

---
📄 Full approach & architecture in [`RedRob_Intelligent_Candidate_Recovery.pdf`](./RedRob_Intelligent_Candidate_Recovery.pdf)
