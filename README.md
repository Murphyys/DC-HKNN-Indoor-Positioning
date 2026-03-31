# 📡 DC-Hierarchical KNN: Indoor Positioning System Using WiFi Fingerprinting

<div align="center">

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)
![License](https://img.shields.io/badge/License-Academic-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

**Capstone Project · King Mongkut's Institute of Technology Ladkrabang**

[📊 Results](#-results) · [🚀 Quick Start](#-quick-start) · [📋 Manual & Guideline](#-manual--guideline)

</div>

---

## 📦 Project Assets

| Assets | Link |
|:---|:---|
| 💻 Source Code | [All_Algorithm.ipynb](https://github.com/Murphyys/DC-HKNN-Indoor-Positioning/blob/main/All_Algorithm.ipynb) |
| 📂 Collected Data From Experiment | [Data/](https://github.com/Murphyys/DC-HKNN-Indoor-Positioning/tree/main/Data) |
| 📋 Manual & Guideline | [README.md — Manual & Guideline Section](#-manual--guideline) |
| 🎨 Presentation Slides | [View on Canva](https://www.canva.com/design/DAG3bIMg2SU/PU8sDXirqSADwuDewsEDkA/view?utm_content=DAG3bIMg2SU&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h647c090082) · [Download .pptx](https://github.com/Murphyys/DC-HKNN-Indoor-Positioning/blob/main/docs/Capstone%20Presentation.pptx) |
| 🎬 Demonstration Video | [Presentation](https://youtu.be/Pe4oRkFEL8o) · [Full Demo](https://youtu.be/0kAYL6_LzPU) · [Short Demo](https://youtu.be/WNaIaUSxqow) |
| 📄 Report | [PDF](https://github.com/Murphyys/DC-HKNN-Indoor-Positioning/blob/main/docs/Capstone%20Report.pdf) · [Word](https://github.com/Murphyys/DC-HKNN-Indoor-Positioning/blob/main/docs/Capstone%20Report.docx) |

---

## 📌 Overview

This project develops an indoor positioning system using **WiFi signal fingerprinting** and machine learning. The core contribution is the **DC-Hierarchical KNN (Dual-Cluster Hierarchical K-Nearest Neighbors)** model, which localizes users within a building by comparing real-time WiFi RSSI signals against a pre-collected radio map.

The system operates in **3 sequential stages**:

```
WiFi Signal (RSSI) → [1] Floor Detection → [2] Dual-layer Filter → [3] Coordinate Estimation → (X, Y) Position
```

DC-Hierarchical KNN is benchmarked against 4 baseline algorithms: Standard KNN, Hierarchical KNN, Random Forest, and XGBoost.

---

## 📊 Results

| Algorithm | Floor Accuracy (%) | MDE (m) | Training Time (s) | Prediction Time (s) | Memory (MB) |
|:---|:---:|:---:|:---:|:---:|:---:|
| KNN | 98.72 | 3.814 | 4.55 | 0.000046 | 2.7 |
| Hierarchical KNN | 99.64 | 3.656 | 38.72 | 0.000395 | 18.53 |
| Random Forest | 99.82 | 3.774 | 1502.45 | 0.000256 | 5.69 |
| XGBoost | 99.82 | 3.279 | 49.69 | 0.000151 | 43.44 |
| **Proposed (DC-HKNN)** | **100.00** | **2.225** | 332.28 | 0.003014 | 38.61 |

> **MDE** = Mean Distance Error (lower is better)  
> The proposed DC-HKNN achieves the **lowest MDE (2.225 m)** and **perfect floor accuracy (100%)**

---

## 🗂️ Repository Structure

```
📦 DC-HKNN-Indoor-Positioning/
│
├── All_Algorithm.ipynb           # ← Main notebook — run this to reproduce all results
├── README.md
│
├── 📁 Data/
│   ├── Train_Data_1.csv          # Training data (WiFi RSSI fingerprint map)
│   └── Test_Data_1.csv           # Test data (held-out, never used during training)
│
├── 📁 docs/
│   ├── Capstone Report.pdf       # Full research report
│   ├── Capstone Report.docx      # Editable version of the report
│   └── Capstone Presentation.pptx
│
└── 📁 result/                    # Auto-created when notebook runs — do not commit
    ├── Proposed_Hierarchical_KNN.xlsx
    ├── Hierarchical_KNN.xlsx
    ├── KNN.xlsx
    ├── RandomForest_Result.xlsx
    ├── XG_Boost.xlsx
    ├── comparison_table.xlsx
    ├── CDF_Graph.png
    ├── training_time_comparison.png
    └── memory_vs_mde_scatter.png
```

> ⚠️ The `result/` folder is auto-created when you run the notebook. No need to create it manually, and no need to commit it to GitHub.

---

## 🛠️ Requirements

### Python Version
```
Python 3.9+
```

### Required Libraries

| Library | Version | Purpose |
|---------|---------|---------|
| `numpy` | ≥ 1.23 | Array operations, distance calculation |
| `pandas` | ≥ 1.5 | Data loading and DataFrame management |
| `scikit-learn` | ≥ 1.2 | KNN, Random Forest, GridSearchCV, StandardScaler |
| `xgboost` | ≥ 1.7 | XGBoost classifier and per-floor regressors |
| `scipy` | ≥ 1.9 | Euclidean distance matrix (`cdist`) for Hierarchical KNN |
| `matplotlib` | ≥ 3.6 | CDF curves and graph plotting |
| `seaborn` | ≥ 0.12 | Bar charts and scatter plots |
| `openpyxl` | ≥ 3.0 | Reading and writing `.xlsx` result files |
| `IPython` | ≥ 8.0 | Styled comparison table display in Jupyter |
| `tracemalloc` | built-in | Peak memory usage measurement |
| `time` | built-in | Training and prediction time measurement |
| `os` | built-in | Path management and folder creation |

### Install all at once

```bash
pip install numpy pandas scikit-learn xgboost scipy matplotlib seaborn openpyxl ipython
```

---

## 🚀 Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/Murphyys/DC-HKNN-Indoor-Positioning.git
cd DC-HKNN-Indoor-Positioning
```

### 2. Install dependencies

```bash
pip install numpy pandas scikit-learn xgboost scipy matplotlib seaborn openpyxl ipython
```

### 3. Verify data files are in place

```
Data/
├── Train_Data_1.csv   ✅
└── Test_Data_1.csv    ✅
```

### 4. Open and run the notebook

```bash
jupyter notebook All_Algorithm.ipynb
```

Run cells **top to bottom** in order:

| Step | Cell | What it does |
|------|------|---|
| 1 | **Initial Start** | Sets paths, creates `result/` folder, initializes `all_results` — **must run first** |
| 2 | **Proposed Method (DC-HKNN)** | Trains and evaluates the proposed model |
| 3 | **Hierarchical KNN** | Trains and evaluates baseline |
| 4 | **KNN** | Trains and evaluates baseline |
| 5 | **Random Forest** | Trains and evaluates baseline |
| 6 | **XGBoost** | Trains and evaluates baseline |
| 7 | **Comparison Table** | Auto-generates table from all results — no manual input needed |
| 8 | **CDF Graph** | Plots cumulative error distribution |
| 9 | **Other Graphs** | Training time bar chart, memory vs. MDE scatter plot |

---

## ⚙️ Configuration

All file paths are set in **Cell 1 (Initial Start) only**. If you change the dataset, edit only here — no other cell needs to be touched.

```python
# ── Cell 1: Edit here to change data paths ──────────────────
TRAIN_PATH  = os.path.join("Data", "Train_Data_1.csv")
TEST_PATH   = os.path.join("Data", "Test_Data_1.csv")
RESULT_PATH = "result"
```

---

## 📐 Model Architecture

### Proposed Method: DC-Hierarchical KNN

The model processes each location query through **3 sequential blocks**:

**Block 1 — Floor Detection**
- KNN classification on raw RSSI vectors
- Predicts which floor (Z) the user is on
- Trained on full training set with stratified split (to balance floor distribution)

**Block 2 — Dual-layer Filter**
- Restricts candidate neighbors to the predicted floor only
- Applies a **radius-based cluster filter** (percentile-based) to remove spatial outliers
- Uses a **confidence threshold** on RSSI distances to decide whether to accept the cluster

**Block 3 — Coordinate Estimation**
- Inverse-distance weighted average of accepted neighbors
- Points with closer RSSI signatures contribute more to the final (X, Y) estimate

**Hyperparameter Tuning:**  
`K_FLOOR`, `K_POS`, `RADIUS`, `CONF_THRESHOLD` are tuned via Grid Search on a held-out **validation set (20% of training data)**. The final model is then retrained on the full training set and evaluated once on the **test set**.

---

## 📋 Manual & Guideline

### How to reproduce the exact results

1. Make sure `Data/Train_Data_1.csv` and `Data/Test_Data_1.csv` are present
2. Run `All_Algorithm.ipynb` from top to bottom
3. All output files are saved automatically to `result/`
4. The comparison table is displayed in the Comparison cell and exported as `result/comparison_table.xlsx`

### How to use with a new dataset

1. Place your new CSV files in the `Data/` folder
2. Update the filenames in **Cell 1** only:
   ```python
   TRAIN_PATH = os.path.join("Data", "your_train_file.csv")
   TEST_PATH  = os.path.join("Data", "your_test_file.csv")
   ```
3. Make sure your CSV follows this format:

| Column | Description |
|--------|-------------|
| Columns 1–18 (RSSI) | WiFi RSSI values from 18 APs (dBm). Use `100` if no signal. |
| `X` | Ground truth X coordinate (meters) |
| `Y` | Ground truth Y coordinate (meters) |
| `Z` | Floor number (integer, e.g. `1`, `2`, `3`) |

> ⚠️ The code identifies **features** by column position (`iloc[:, 1:19]`) and **labels** by column name (`X`, `Y`, `Z`). If your dataset uses different column names or positions, the code will need to be updated accordingly.

4. Re-run all cells from top to bottom

### Running only one model

Any single model cell can be run independently as long as **Cell 1 (Initial Start) has been run first** in the current kernel session. Cell 1 initializes the shared variables `TRAIN_PATH`, `TEST_PATH`, `RESULT_PATH`, and `all_results`.

### Understanding the output files

| File | Description |
|------|-------------|
| `Proposed_Hierarchical_KNN.xlsx` | Per-sample predictions and errors from DC-HKNN |
| `Hierarchical_KNN.xlsx` | Per-sample predictions from Hierarchical KNN |
| `KNN.xlsx` | Per-sample predictions from Standard KNN |
| `RandomForest_Result.xlsx` | Per-sample predictions from Random Forest |
| `XG_Boost.xlsx` | Per-sample predictions from XGBoost |
| `comparison_table.xlsx` | Summary table of all 5 algorithms |
| `CDF_Graph.png` | CDF of 2D positioning error across all models |
| `training_time_comparison.png` | Bar chart of training times (sorted low → high) |
| `memory_vs_mde_scatter.png` | Trade-off: memory usage vs. mean distance error |

---

## 📍 Data Collection

WiFi RSSI fingerprint data was collected at **KMITL Lifelong Learning Center** using a mobile device scanning signals from **18 Access Points (APs)**. Survey points were marked at fixed intervals across multiple floors.

- Signal value `100` = no signal detected from that AP → replaced with `-90 dBm` during preprocessing
- Labels (X, Y, Z) represent the physical coordinates of each survey point in meters

---

## 👩‍💻 Author

**Bordin Pantdej** · King Mongkut's Institute of Technology Ladkrabang <br>
**Wasan Boonsong** · King Mongkut's Institute of Technology Ladkrabang

Academic Research Project

---

## 📄 License

This project is submitted for academic purposes at King Mongkut's Institute of Technology Ladkrabang.
