# 👥 Customer Segmentation with K-Means Clustering

An Unsupervised Machine Learning system that automatically discovers customer groups from raw data — **no labels needed**. Built to demonstrate real-world business impact of AI in marketing.

---

## 🎯 What It Does

Automatically segments customers into distinct groups based on behavior patterns, enabling targeted marketing strategies for each segment.

```
300 customers with Age + Monthly Spending data
              ↓
         K-Means Clustering
              ↓
3 Distinct Segments Discovered Automatically
```

---

## 📊 Discovered Segments

| Segment | Avg Age | Avg Spending | Size | Strategy |
|---------|---------|-------------|------|----------|
| 🏆 High Value | 45 yrs | 6,949 SAR | 120 | Real estate, cars, travel |
| 👴 Senior | 60 yrs | 1,954 SAR | 100 | Healthcare, insurance |
| 🎯 Young | 25 yrs | 3,070 SAR | 80 | Gaming, fashion, sports |

---

## 🏗️ Pipeline

```
Raw Customer Data (Age + Monthly Spending)
      ↓
Exploratory Data Analysis (scatter plots)
      ↓
StandardScaler Normalization
      ↓
Elbow Method → Find optimal k
      ↓
Silhouette Score → Validate k=3
      ↓
K-Means Clustering (3 segments)
      ↓
Segment Analysis + Business Recommendations
```

---

## 📈 How We Found k=3

**Elbow Method** — Find where inertia stops dropping sharply:
```
k=2: inertia drops significantly
k=3: inertia drops moderately  ← elbow point
k=4: inertia drops slightly
```

**Silhouette Score** — Validates cluster quality:
```
k=2: 0.61
k=3: 0.74  ← highest = best separation
k=4: 0.68
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Clustering | scikit-learn KMeans |
| Validation | Silhouette Score, Elbow Method |
| Normalization | StandardScaler |
| Visualization | Matplotlib |
| Language | Python 3.11 |

---

## 📦 Installation

```bash
git clone https://github.com/RashaAlorabi/customer-segmentation.git
cd customer-segmentation

python3 -m venv ai-env
source ai-env/bin/activate

pip install -r requirements.txt
```

---

## 🚀 Usage

```bash
jupyter notebook customer_segmentation.ipynb
```

Use on your own data:

```python
import pandas as pd
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

# Load your customer data
df = pd.read_csv('your_customers.csv')

# Scale and cluster
scaler = StandardScaler()
X_scaled = scaler.fit_transform(df[['age', 'monthly_spending']])

kmeans = KMeans(n_clusters=3, random_state=42, n_init=10)
df['segment'] = kmeans.fit_predict(X_scaled)

print(df.groupby('segment').mean())
```

---

## 🔑 Key Learnings

**Supervised vs Unsupervised:**
```
Supervised:   Data + Labels → Model learns
Unsupervised: Data only     → Model discovers
```

**Why StandardScaler is critical here:**
```
Without scaling:
  Age: 20-65 (range: 45)
  Spending: 1,000-9,000 (range: 8,000)
  → Spending dominates clustering completely

With scaling:
  Both features contribute equally → fair clustering
```

**Real Business Impact:**
- Before: Same generic email to all 300 customers
- After: 3 targeted campaigns → higher conversion rates

---

## 🧠 Concepts Demonstrated

```
Unsupervised Learning:  No labels needed
Elbow Method:           Find optimal number of clusters
Silhouette Score:       Validate cluster quality
Feature Scaling:        Critical for distance-based algorithms
Business Translation:   Convert data clusters to marketing strategy
```

---

## 📁 Project Structure

```
customer-segmentation/
├── customer_segmentation.ipynb   # Main notebook
├── data/
│   └── customers.csv            # Sample data
├── requirements.txt
├── .gitignore
└── README.md
```

---

## 📋 Requirements

```txt
scikit-learn
numpy
pandas
matplotlib
jupyter
```

---

## 💡 Real-World Applications

This approach is used by:
- **stc** — Segment subscribers for targeted plans
- **STC Pay** — Group users by spending behavior
- **Amazon** — Product recommendation clusters
- **Banks** — Customer risk profiling

---

## 🚧 Future Improvements

- [ ] Add more features (purchase history, location)
- [ ] Try DBSCAN for non-spherical clusters
- [ ] Build interactive dashboard with Streamlit
- [ ] Apply to real e-commerce dataset

---

## 👤 Author

**Rasha** — Senior Software Engineer → AI Solutions Engineer

