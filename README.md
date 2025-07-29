# BERTopic Interdisciplinary Mapping Project

This project applies BERTopic to uncover and track **AI research topics** and their trend over time across disciplines using arXiv metadata. The pipeline includes:

1. Data Preprocessing  
2. Topic Modeling with BERTopic  
3. Temporal Trend Analysis  
4. Interdisciplinary Mapping

---

## Repository Structure

```text
01_data_preprocessing/
├── arxiv_ai.csv                                      # Raw dataset obtained from Kaggle (pre-cleaning)
├── EDA_and_Data_Preparation_FINAL_RESECTIONED.ipynb  # Notebook for cleaning and preparation
├── arxiv_ai_cleaned_ready.csv                         # Cleaned titles and abstracts

02_bertopic/
├── bertopic_model_trial_8/                            # Full BERTopic model (fine-grained)
├── bertopic_model_trial_8_reduced/                    # Reduced BERTopic model (broader topics)
├── embeddings.npy                                     # Precomputed document embeddings
├── Topic Modeling_v1.0.ipynb                          # BERTopic modeling
├── Reduced_model_v1.0.ipynb                           # Topic reduction process
├── Topic model visualisations and comparison_v1.0.ipynb # Visual analysis
├── arxiv_ai_with_original_and_reduced_topics.csv      # Dataset with full + reduced topic labels
├── arxiv_ai_with_original_and_reduced_topics_labeled.csv   # Dataset with validated and manually assigned topic labels

03_temporal_trend_analysis/
├── Temporal Trend Analysis_Finalised_v1.0.ipynb       # Final trend analysis
├── Relative Frequency Clustering_v1.0.ipynb           # Frequency trend clustering
├── Slope and Volume Clustering_v1.0.ipynb             # Rate-of-change clustering
├── smoothed_relative_frequencies.csv                  # Smoothed topic frequency (yearly)
├── topic_summary_with_slope_and_volume.csv            # Slope and volume for each topic
├── relative_frequency_cluster_labels.csv              # Frequency-based trend cluster result for each topic
├── slope_volume_cluster_labels.csv                    # Slope & volume cluster label result for each topic
├── trajectory_clustered_topics.csv                    # Relative frequency per yer for each topic

04_interdisciplinary_mapping/
├── Top 50 category codes.csv                          # Top 50 mapped arXiv categories
├── Interdisciplinary Mapping_v2.0.ipynb               # Topic-discipline mapping

```
---

## Reproducibility & Usage

All notebooks in this repository are self-contained and reproducible using the data and models provided. Below are examples for loading key components.

### Environment Setup
pip install -r requirements.txt

### Load BERTopic Models

The full BERTopic models (too large for GitHub) are available via OneDrive:
[Download the models](https://universityofexeteruk-my.sharepoint.com/:f:/g/personal/ss1781_exeter_ac_uk/Em-B2bTRTqZChbay3NIISDUB6E8iCrbjGfVqxW9ogVSJ_Q?e=ZkLPVl)

```python
from bertopic import BERTopic

# Load full topic model (fine-grained)
topic_model = BERTopic.load("02_bertopic/bertopic_model_trial_8")

# Load reduced topic model (broader categories)
reduced_model = BERTopic.load("02_bertopic/bertopic_model_trial_8_reduced")

### Load Precomputed Embeddings
import numpy as np

# Load document embeddings used for training and visualization
embeddings = np.load("02_bertopic/embeddings.npy")
```
---

## Citation
  _arXiv (n.d.). https://info.arxiv.org/about/index.html_
  _Kaggle. (2023, July 2). Arxiv.org AI Research Papers Dataset. Kaggle. https://www.kaggle.com/datasets/yasirabdaali/arxivorg-ai-research-papers-dataset/data._

---

## Authors & Contact

**[Sorawis Sridhanabutr]**  
[ss1781@exeter.ac.uk]

---

## License

- The original dataset is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

---