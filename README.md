#  Item-Based Collaborative Filtering  (MovieLens 100K)

This repository presents a **complete reproduction of Item-Based Collaborative Filtering experiments** using the MovieLens 100K dataset, inspired by classical recommender system research (Sarwar et al., 2001).

---

#  Objective

The goal of this project is to:

* Implement Item-Based Collaborative Filtering (IBCF)
* Compare similarity measures
* Analyze performance under different configurations
* Reproduce experimental trends from research literature

---

#  Repository Structure

```
item-cf-repro/
│
├── data/
│   └── ml-100k/
│
├── documents/
│   └── paper14/
     └── rs_report/
├── src/
│   └── experiments.ipynb
│
├── results/
│   └── figures/
│
├── tests/
├── assets/
├── requirements.txt
└── README.md
```

---

#  Dataset Used

| Dataset        | Size            | Purpose                  |
| -------------- | --------------- | ------------------------ |
| MovieLens 100K | 100,000 ratings | Core recommendation data |

### Dataset Details:

* Users: 943
* Movies: 1682
* Sparsity: **93.7%**

---

#  Core Pipeline

```
MovieLens Dataset
        │
        ▼
User-Item Matrix Construction
        │
        ▼
Similarity Computation
(Cosine / Pearson / Adjusted Cosine)
        │
        ▼
Top-K Neighbour Selection
        │
        ▼
Weighted Rating Prediction
        │
        ▼
Evaluation (MAE)
```

---

#  Methodology

## 1. User-Item Matrix

* Rows → Users
* Columns → Movies
* Values → Ratings

---

## 2. Similarity Measures

* Cosine Similarity
* Pearson Correlation
* Adjusted Cosine

---

## 3. Prediction Formula

[
\hat{r}_{u,i} = \frac{\sum (similarity \times rating)}{\sum similarity}
]

---

##  Experimental Results

---

##  1. Similarity Comparison

| Method          | MAE        |
| --------------- | ---------- |
| Adjusted Cosine | **0.7561** |
| Cosine          | 0.8052     |
| Pearson         | 0.8051     |
##  1. Similarity Comparison

![Similarity Metrics](results/figures/similarity%20metrics%20comparisons.png)

###  Observation:

* Adjusted cosine performs best
* Matches theoretical expectations

---

##  2. Train/Test Ratio Impact

| Train % | MAE        |
| ------- | ---------- |
| 20%     | 0.8600     |
| 50%     | 0.7851     |
| 80%     | 0.7561     |
| 90%     | **0.7548** |

###  Observation:

* More training data → lower error

---

##  3. Neighbourhood Size (k)

| k   | MAE    |
| --- | ------ |
| 10  | 0.7848 |
| 30  | 0.7561 |
| 100 | 0.7528 |
| 200 | 0.7531 |

###  Insight:

* Optimal range: **30–100 neighbors**

---

##  4. User vs Item Comparison

| Method     | MAE        |
| ---------- | ---------- |
| User-Based | **0.7336** |
| Item-Based | 0.7506     |

###  Insight:

* User-based slightly outperforms item-based in this dataset

---

##  5. Model Size Analysis

| Model Size   | MAE        |
| ------------ | ---------- |
| Small (25)   | 0.9042     |
| Medium (100) | 0.8439     |
| Large (200)  | 0.7838     |
| Full Model   | **0.7561** |

###  Observation:

* Larger models improve accuracy

---

##  6. Cross Validation

* User-Based MAE: **0.7336 ± 0.0062**
* Item-Based MAE: **0.7506 ± 0.0064**

---

#  Key Observations

* Adjusted cosine similarity performs best
* Increasing data improves model accuracy
* Optimal neighbourhood size exists
* User-based CF slightly outperforms item-based
* Results align with research findings

---

#  Limitations

* Cold start problem
* Sparse dataset challenges
* High computational cost

---

#  How to Run

## 1. Install dependencies

```bash
pip install -r requirements.txt
```

## 2. Add dataset

Place file:

```
data/ml-100k/u.data
```

## 3. Run notebook

Open:

```
src/experiments.ipynb
```

---

#  Runtime

* Approx: 5–10 minutes depending on system

---

#  Conclusion

This project successfully reproduces item-based collaborative filtering experiments and validates key research findings. The system demonstrates strong performance and provides insights into similarity measures, neighborhood selection, and dataset size impact.

---

#  Future Work

* Matrix Factorization (SVD, SVD++)
* Hybrid Recommender Systems
* Deep Learning Models

---

#  Reference

Sarwar, B. et al. (2001)
"Item-Based Collaborative Filtering Recommendation Algorithms"
https://www.researchgate.net/publication/2369002_Item-based_Collaborative_Filtering_Recommendation_Algorithms
---

#  Author

Divyanshi
B.Tech AI & Data Science
