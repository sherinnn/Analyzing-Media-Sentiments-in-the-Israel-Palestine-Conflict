# Analyzing-Media-Sentiments-in-the-Israel-Palestine-Conflict

## 📌 Overview
This project analyzes global news media coverage of the Israel–Palestine conflict using a combination of **sentiment analysis**, **topic modeling**, **text clustering**, **NER**, and **media-bias exploration**.  
The goal is to understand *how the conflict is represented across different countries and news outlets*, uncover underlying themes, detect sentiment trends, and assess possible media bias.

The pipeline uses news data collected from multiple sources (e.g., Qoshe, ECNS, TradeIndia, TheCritic, etc.), cleaned and enriched with excerpt and summary fields.  
It processes ~7,600+ articles from 2017–2023.

> Source data and processing details come from the notebook in this project. :contentReference[oaicite:0]{index=0}

---

## ✨ Key Features

### 🔹 **1. Data Collection**
- Uses **NewsCatcher API** to fetch articles related to:
  - *Israel*, *Palestine*, *Gaza*, *West Bank*, *Hamas*, *Fatah*, *Middle East conflict*
- Supports parameters such as:
  - Keyword search (`q`)
  - Date ranges
  - Pagination
  - Language and source ranking

### 🔹 **2. Data Cleaning & Preprocessing**
- Removed irrelevant fields (rank, relevancy, unused metadata).
- Added/cleaned fields:
  - `excerpt`
  - `summary`
  - `Summary2` (stemmed + stopword-removed cleaned text)
- Robust text normalization:
  - punctuation removal  
  - tokenization  
  - stopword filtering  
  - Snowball stemming  

### 🔹 **3. Exploratory Data Analysis**
- Top countries covering the conflict (US, Turkey, Canada)
- Distribution of article counts by media outlet
- Rank-based comparison of news sources
- Country-wise reporting patterns

### 🔹 **4. Topic Modeling & Clustering**
#### **TF-IDF + KMeans**
- Generated 5 clusters using TF-IDF vectors  
- Example top terms:
  - `israel`, `palestinian`, `gaza`, `iran`, `saudi`, `syria`
- Reveals geopolitical topic separation (Iran cluster, Syria cluster, legal/litigation cluster)

#### **Word2Vec + KMeans**
- Word2Vec embeddings (100-dim)
- Elbow method used to identify optimal clusters
- Captures deeper semantic structure across articles

### 🔹 **5. Sentiment Analysis**
Two methods experimented:
- **TextBlob** (lexicon-based)
- **BERT** (transformer-based classifier)

Outputs:
- Sentence-level polarity
- Document-level sentiment vector
- US media sentiment vs international media comparison (in progress)

### 🔹 **6. Named Entity Recognition (NER)**
- Extracts key entities such as:
  - Locations (Gaza, Jerusalem, West Bank)
  - Organizations (IDF, Hamas, PA)
  - Political actors (Biden, Netanyahu, Abbas)
- Used for:
  - Sentence extraction
  - Co-occurrence networks
  - Event detection

### 🔹 **7. Event & Temporal Analysis** *(planned/partially implemented)*
- Spike detection over time
- Mapping event clusters (wars, ceasefires, diplomatic talks)

---

## 🔧 Technologies Used

- **Python**
- **Pandas, NumPy**
- **NLTK, spaCy**
- **Scikit-Learn**
- **Gensim (Word2Vec)**
- **Transformers (BERT)**
- **Matplotlib, Seaborn**
- **NewsCatcher API**

---

## 🧠 Insights & Findings (So Far)

- Large volume of articles originate from **US-based media**.
- Cluster analysis suggests:
  - Some groups focus heavily on *Iran–Israel relations*.
  - Others cluster around *Gaza conflict reporting*.
  - Some outlets display legally-related or geopolitical framing.
- Sentiment varies significantly across countries and regions.
- Western media sometimes shows sentiment polarity differences compared to non-Western sources—an area for deeper bias evaluation.

---


