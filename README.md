# 🎬 Netflix Recommendation System

> **SVD Matrix Factorization + Item-Based Collaborative Filtering + Hybrid System**  
> Open Projects 2026 | Geophysical Technology

---

## 👥 Authors
- **Jaideep Attri**
- **Jinesh Kumar Vimal**

---

## 📊 Results Summary

| Metric | SVD | Item-CF | Winner |
|--------|-----|---------|--------|
| RMSE | **0.9414** | 1.0481 | ✅ SVD |
| MAE | **0.7354** | 0.8211 | ✅ SVD |
| MAP@10 | **0.0015** | 0.0003 | ✅ SVD (5×) |

---

## 📁 Repository Structure

```
netflix-recommendation-system/
├── finalprojectcode.ipynb   ← Main notebook (all pipelines)
├── requirements.txt         ← Dependencies
└── README.md                ← This file
```

### What's inside the notebook:

| Cell | Pipeline | Description |
|------|----------|-------------|
| Cell 0 | Setup | Install dependencies (scikit-surprise, gradio) |
| Cell 1 | Data Processing | Load dataset from Google Drive, parquet files |
| Cell 2 | Data Overview | Train/test split info |
| Cell 3-4 | EDA | 4 visualizations — ratings, users, movies, sparsity |
| Cell 5 | SVD Evaluation | RMSE: 0.9414, MAE: 0.7354 |
| Cell 6 | Item-CF Evaluation | RMSE: 1.0481, MAE: 0.8211 |
| Cell 7 | MAP@10 | SVD: 0.0015, Item-CF: 0.0003 |
| Cell 8 | Model Comparison | Final comparison table + bar chart |
| Cell 9 | Recommendations | Top-K recommendations for 5 users |
| Cell 10 | Quality Plots | Predicted rating distribution |
| Cell 11 | Explainability (Task A) | User history → recommendation rationale |
| Cell 12 | Cold Start (Task B) | 3-tier strategy for new users/movies |
| Cell 14 | Dashboard (Task C) | Netflix-style Gradio UI |
| Cell 15-16 | Hybrid System (Task D) | SVD + Popularity adaptive blending |

---

## 🗃️ Dataset

**Netflix Prize Dataset (MovieLens 10M version)**

| Attribute | Value |
|-----------|-------|
| Total Ratings | 10,000,000 |
| Unique Users | 458,341 |
| Unique Movies | 14,596 |
| Rating Scale | 1.0 – 5.0 |
| Train Split | 8,000,000 (80%) |
| Test Split | 2,000,000 (20%) |
| Matrix Sparsity | 99.85% |

> ⚠️ Dataset is NOT included in this repo due to size.  
> Download from: [MovieLens 10M](https://grouplens.org/datasets/movielens/10m/)

---

## ⚙️ How to Reproduce Results

### Step 1 — Open in Google Colab
Click below to open the notebook directly:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Jinesh283/netflix-recommendation-system/blob/main/finalprojectcode.ipynb)

### Step 2 — Setup Google Drive
Make sure your Google Drive has this folder structure:
```
MyDrive/
└── Recommendation_System_Project/
    ├── Dataset/
    │   └── processed/
    │       ├── ratings_10m_clean.parquet
    │       ├── movies.parquet
    │       ├── train.parquet
    │       └── test.parquet
    └── models/
        ├── svd_model.pkl
        ├── movie_idx.pkl
        ├── idx_movie.pkl
        └── item_sim_matrix.npz
```

### Step 3 — Run Cells in Order
```
Cell 0  → Install dependencies
Cell 1  → Mount Drive + Load data
Cell 2+ → Run sequentially (all models pre-trained, no retraining needed)
```

> ✅ **No retraining required** — pre-trained models load directly from Drive.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Core language |
| scikit-surprise | SVD matrix factorization |
| pandas / numpy | Data processing |
| scipy (sparse) | Item-CF similarity matrix |
| matplotlib / seaborn | Visualizations |
| gradio | Interactive dashboard |
| Google Colab | Execution environment |
| Google Drive | Model & data storage |

---

## 🧠 Models

### Model 1 — SVD (Matrix Factorization)
- Decomposes user-item matrix into latent factors
- Parameters: `n_factors=50`, `n_epochs=20`, `lr=0.005`, `reg=0.02`
- Predicted rating: `R(u,i) = μ + b_u + b_i + q_i · p_u`

### Model 2 — Item-Based CF
- Cosine similarity between movies
- Sparse CSR matrix storage
- Similarity-weighted average of user's past ratings

### Model 3 — Hybrid System
```
final_score = α × SVD_score + (1-α) × popularity_score
```
| User Type | Ratings | Alpha |
|-----------|---------|-------|
| New User | < 10 | 0.2 (popularity-heavy) |
| Sparse User | 10–50 | 0.5 (balanced) |
| Active User | > 50 | 0.7 (SVD-heavy) |

---

## 📋 Tasks Completed

- [x] **Task A** — Explainable Recommendations (Cell 11)
- [x] **Task B** — Cold Start Strategy (Cell 12)
- [x] **Task C** — Interactive Dashboard — Gradio (Cell 14)
- [x] **Task D** — Hybrid Recommendation System (Cell 15-16)
- [ ] **Task E** — Deployment (Hugging Face Spaces — in progress)

---

## 📈 Evaluation Criteria Coverage

| Criterion | Weight | Our Approach |
|-----------|--------|-------------|
| Data Understanding & EDA | 15% | 4 visualizations + statistical analysis |
| Recommendation Model Dev | 30% | SVD + Item-CF + Hybrid (3 models) |
| RMSE & MAP@10 Performance | 20% | SVD RMSE: 0.9414, MAP@10: 0.0015 |
| Recommendation Quality | 20% | Top-K + Explainability + Cold Start |
| Innovation & Creativity | 10% | Hybrid adaptive system + Netflix dashboard |
| Presentation & Docs | 5% | 10-page report + 8-slide PPT |

---

*Netflix Recommendation System — Open Projects 2026*
