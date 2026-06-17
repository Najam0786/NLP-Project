<<<<<<< HEAD
# Trustpilot Review Analysis: Lakeland

## NLP-Based Sentiment & Topic Modeling | Home & Garden Sector

---

## Project Overview

This project analyzes **100 Trustpilot reviews** for **Lakeland** (www.lakeland.co.uk) using Natural Language Processing (NLP) techniques. The analysis addresses four key business questions about customer sentiment, topic identification, competitive benchmarking, and strategic recommendations.

**Why NLP?** The dataset contains exactly 20 reviews per star level (1★–5★), creating an artificial balance that masks true customer sentiment. Star ratings alone are misleading—this analysis uses text-based sentiment analysis to uncover the real picture.

---

## Business Questions Addressed

| Question | Objective |
|----------|-----------|
| **Q1** | Is overall sentiment positive or negative? How does Lakeland compare to competitors? |
| **Q2** | What topics do customers write about? Are competitors writing about the same topics? |
| **Q3** | For each topic, what is the predominant sentiment? Where does Lakeland over- or underperform? |
| **Q4** | What are the specific areas for improvement with business impact? |

---

## Dataset

- **Primary Dataset**: `trustpilot-reviews-123k.csv` (123,181 reviews across 1,680 companies)
- **Target Company**: Lakeland (100 reviews)
- **Competitors**: ProCook, Dunelm, Emma Bridgewater (100 reviews each)
- **Sector**: Home & Garden (6,138 reviews used for LDA training)

---

## Methodology

### 1. Sentiment Analysis (Q1)
- **Model**: `distilbert-base-uncased-finetuned-sst-2-english` (DistilBERT)
- **Approach**: Binary classification (POSITIVE/NEGATIVE)
- **Why**: Proven English sentiment model, fast inference, reliable for customer reviews

### 2. Topic Modeling (Q2)
- **Algorithm**: LDA (Latent Dirichlet Allocation)
- **Training**: Full Home & Garden sector (6,138 reviews from 74 companies)
- **Topics**: 6 themes identified
- **Why**: Sector-wide training ensures comparable topic space for competitive analysis

### 3. Topic-Sentiment Analysis (Q3)
- Cross-tabulation of sentiment by topic
- Priority matrix: Volume vs Negativity
- Competitive comparison on same topics

### 4. Strategic Recommendations (Q4)
- Actionable priorities based on high-volume, high-negativity topics
- Business impact quantification
- Timeline and resource allocation

---

## Key Findings

### Q1: Overall Sentiment

**Lakeland**: 30% Positive, 70% Negative

| Company | Positive % | vs Lakeland |
|---------|-----------|-------------|
| Emma Bridgewater | 34% | +4 pp |
| Dunelm | 34% | +4 pp |
| **Lakeland** | **30%** | baseline |
| ProCook | 29% | -1 pp |

**Gap**: Lakeland trails sector leaders by 4 percentage points.

**Star Rating Bias**: 95% of 3-star reviews are NEGATIVE in text—proving that star averages hide significant dissatisfaction.

---

### Q2 & Q3: Topics Identified

| Topic | Volume | Negative % | Keywords | Priority |
|-------|--------|------------|----------|----------|
| **T5** | **37%** | **91.9%** | order, customer, service, received | **CRITICAL** |
| T4 | 17% | 76.5% | quality, bought, just, shed | FIX NEEDED |
| T2 | 16% | 18.8% | service, helpful, kitchen, great | **STRENGTH** |
| T1 | 12% | 75.0% | delivery, tree, delivered | FIX NEEDED |
| T0 | 9% | 77.8% | delivery, day, told, order | FIX NEEDED |
| T3 | 9% | 44.4% | good, quality, great, service | MONITOR |

**Critical Finding**: T5 (Order/Service) dominates at 37% volume with 91.9% negativity—this is the primary driver of customer dissatisfaction.

---

### Competitive Analysis (Topic 5 - Order/Service)

| Company | T5 Share | vs Lakeland |
|---------|----------|-------------|
| **Lakeland** | **37%** | baseline |
| Dunelm | 29% | -8% |
| ProCook | 28% | -9% |
| Emma Bridgewater | 21% | **-16%** |

**Key Insight**: Lakeland has 25-75% more customers complaining about order/service issues than competitors. While sentiment negativity is similar (~91.9% vs ~94%), the volume difference is the controllable lever.

---

### Gap Analysis (Lakeland vs Competitor Average)

| Topic | Lakeland | Comp Avg | Gap | Assessment |
|-------|----------|----------|-----|------------|
| T5 | 91.9% | 94.2% | -2.3% | Similar (industry-wide problem) |
| T1 | 75.0% | 66.9% | **+8.1%** | **Lakeland WORSE on delivery** |
| T2 | 18.8% | 23.0% | -4.3% | **Lakeland BETTER on kitchen/service** |
| T3 | 44.4% | 35.8% | +8.6% | Lakeland somewhat worse |
| T4 | 76.5% | 82.2% | -5.7% | Lakeland better |

---

## Q4: Strategic Recommendations

### Priority 1: Fix Order/Service (T5) — CRITICAL
- **Stats**: 37% of reviews, 91.9% negative
- **Actions**:
  - Proactive order confirmation emails
  - Real-time delivery tracking SMS
  - Fast escalation paths for issues
- **Expected Impact**: Reduce T5 review share from 37% → ~25%
- **Timeline**: 0-3 months

### Priority 2: Improve Delivery (T1) — HIGH
- **Stats**: 12% of reviews, 75% negative, +8.1% gap vs competitors
- **Actions**:
  - Review courier partnerships
  - Offer premium/tracked delivery options
  - Improve packaging
- **Expected Impact**: Close 8 percentage point delivery gap
- **Timeline**: 0-3 months

### Priority 3: Leverage Strength (T2) — STRATEGIC
- **Stats**: 16% of reviews, only 18.8% negative
- **Actions**:
  - Showcase in-store experience in marketing
  - Build brand positioning around quality service
  - Differentiate from mass-market competitors
- **Expected Impact**: Competitive advantage in crowded market
- **Timeline**: 3-6 months

---

## Business Impact Summary

| Metric | Current | Target (6 months) | Path |
|--------|---------|-------------------|------|
| Overall positive sentiment | 30% | 36-38% | Reduce T5 volume + close T1 gap |
| T5 review share | 37% | ~25% | Fewer customers needing to complain |
| T1 negativity gap vs competitors | +8.1 pp | 0 pp | Match competitor delivery performance |
| vs sector leaders (Dunelm/Emma B) | -4 pp | On par | Combined T5 + T1 improvements |

---

## Repository Structure

```
NLP Project/
├── NLP_Analysis_Lakeland.ipynb      # Main analysis notebook (10 sections)
├── Lakeland_NLP_Presentation.pptx   # 6-slide executive presentation
├── trustpilot-reviews-123k.csv      # Dataset (123K reviews)
├── emp_100_reviews.xlsx             # Competitor reference data
├── lakeland_analysis.png            # 4-panel visualization
├── sentiment_analysis.png           # Sentiment distribution chart
├── sentiment_comparison.png         # Star vs NLP sentiment heatmap
├── requirements.txt                 # Python dependencies
└── README.md                        # This file
```

---

## Installation & Usage

### Prerequisites
- Python 3.10+
- pip package manager

### Setup
```bash
# Create virtual environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Run Notebook
```bash
jupyter notebook NLP_Analysis_Lakeland.ipynb
```

### Notebook Sections
1. Environment Setup & Data Loading
2. Demonstrating Star Rating Bias
3. Topic Modeling (LDA)
4. Applying Topics to Lakeland
5. Sentiment by Topic (Priority Matrix)
6. Competitor Benchmarking: Overall Sentiment
7. Competitor Benchmarking: Topic Distribution
8. Competitor Benchmarking: Sentiment per Topic
9. Summary Visualizations
10. Conclusions & Recommendations

---

## Dependencies

```
pandas==2.0.3
numpy==1.24.3
matplotlib==3.7.2
seaborn==0.12.2
scikit-learn==1.3.0
nltk==3.8.1
transformers==4.31.0
torch==2.0.1
sentence-transformers==2.2.2
jupyter==1.0.0
ipykernel==6.25.0
```

---

## Technical Notes

### Sentiment Model Selection
- **Chosen**: `distilbert-base-uncased-finetuned-sst-2-english`
- **Rationale**: 
  - Proven on English text
  - Binary classification (POSITIVE/NEGATIVE) matches business need
  - Faster inference than full BERT
  - Reliable on customer review domain

### LDA Training Strategy
- **Sector-wide training** (6,138 reviews) vs company-only (100 reviews)
- **Benefits**:
  - Richer vocabulary → more stable topics
  - Shared topic space → comparable competitive analysis
  - Better generalization to unseen reviews

### Data Preprocessing
- Lowercase conversion
- Non-alphabetic character removal
- Stopword removal (English)
- min_df=5, max_df=0.95 (CountVectorizer)

---

## Limitations

1. **Sample Size**: 100 reviews per company limits statistical power
2. **English Only**: Model may miss nuances in non-standard English
3. **Binary Sentiment**: Neutral reviews forced into POSITIVE/NEGATIVE
4. **Static Analysis**: Cross-sectional data, not longitudinal trends

---

## Future Work

- **Longitudinal Analysis**: Track sentiment trends over time
- **Aspect-Based Sentiment**: Finer-grained sentiment (price, quality, service)
- **Review Response Analysis**: Impact of company responses on sentiment
- **Predictive Modeling**: Identify at-risk customers before negative review

---

## Author

Nazmul Farooquee  
June 2026

---

## License

This project is for educational and analytical purposes. Dataset usage subject to Trustpilot terms of service.
=======
# NLP-Project
NLP Project
>>>>>>> 247fa586d420f806c75cf381369d95dcf23d4e57
