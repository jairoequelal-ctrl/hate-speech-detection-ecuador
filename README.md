# Hate Speech Detection during the 2022 Ecuador Strike

NLP and machine-learning project associated with a **peer-reviewed conference paper published by Springer**.

## Publication

**Hate Speech Detection on Twitter: A Machine Learning Approach to Identify Attacks on Indigenous People During the 2022 Ecuador Strike**

Saire Conejo, Jairo Quelal, Silvana Escobar, Alexandra Jima-González, Erick Cuenca, and José Ángel Alcántara.

Published in *Applied Engineering and Innovative Technologies (AENIT 2023)*, Lecture Notes in Networks and Systems, vol. 1134, Springer, 2024.

**DOI:** `10.1007/978-3-031-70760-5_25`

**Official publication:** https://link.springer.com/chapter/10.1007/978-3-031-70760-5_25

## Research problem

The study analyzes hate speech directed at Indigenous people and communities on Twitter during Ecuador's June 2022 national strike. The research pipeline combines human annotation, exploratory data analysis, natural language processing, and probabilistic text classification.

The published study reports **33,512 tweets**, including **29,782 No Hate** and **3,730 Hate** labels before balancing.

## Machine-learning pipeline

The supplied implementation demonstrates:

1. Loading and inspecting the annotated Twitter dataset.
2. Exploratory analysis of class distribution and temporal activity.
3. Random undersampling of the majority class to create a balanced dataset.
4. An 80/20 train/test split.
5. TF-IDF text vectorization.
6. Multinomial Naive Bayes classification.
7. Spanish-language text preprocessing.
8. Evaluation with precision, recall, F1-score, accuracy, and a confusion matrix.

## Results reproduced in the supplied notebook

### Baseline text model

The saved notebook output reports:

| Metric | Value |
|---|---:|
| Accuracy | **84.79%** |
| Weighted Precision | 0.85 |
| Weighted Recall | 0.85 |
| Weighted F1-score | 0.85 |

Class-level results:

| Class | Precision | Recall | F1 |
|---|---:|---:|---:|
| No Hate (0) | 0.88 | 0.79 | 0.83 |
| Hate (1) | 0.82 | 0.90 | 0.86 |

### Model after text preprocessing

The saved notebook reports an accuracy of **84.32%**, with weighted precision, recall, and F1 around **0.85, 0.84, and 0.84**, respectively.

These values are consistent with the published paper's principal experiment, which reports approximately **84% accuracy**.

## Perspective API experiment

The published paper includes a second experiment in which manually labeled hate tweets were cross-checked using Google Perspective API's **Identity Attack** score with a threshold of 0.5.

The paper reports that this filtering reduced the hate subset from **3,730 to 213 tweets**. A balanced dataset of 426 tweets was then used for the second experiment, for which the paper reports approximately **89.5% accuracy**.

The supplied notebook does **not** contain the Perspective API implementation. For that reason, this repository documents those figures as **published-paper results**, rather than claiming that the included notebook reproduces that experiment.

## Tech stack

`Python` · `Pandas` · `scikit-learn` · `NLTK` · `TF-IDF` · `Multinomial Naive Bayes` · `NLP` · `Matplotlib` · `Seaborn` · `WordCloud`

## Repository structure

```text
hate-speech-detection-ecuador/
├── data/
│   └── README.md
├── docs/
│   └── README.md
├── notebooks/
│   └── hate_speech_detection.ipynb
├── src/
│   └── README.md
├── .gitignore
├── README.md
└── requirements.txt
```

## Data and ethics

The repository intentionally does not redistribute the original tweet-level dataset. The study concerns hate speech targeting a marginalized community, and raw posts may contain abusive language, usernames, identifiers, or other contextual information that is unnecessary for demonstrating the technical workflow.

Only use tweet data when you have the appropriate authorization and comply with the applicable platform/data-use requirements.

## Reproducibility

To rerun the notebook, place an authorized copy of the dataset at:

```text
data/hate_speech_tweets.csv
```

The expected data include the tweet text, creation date, and hate-speech label used by the original analysis.

Install the Python dependencies with:

```bash
pip install -r requirements.txt
```

## Citation

```bibtex
@inproceedings{conejo2024hatespeech,
  title={Hate Speech Detection on Twitter: A Machine Learning Approach to Identify Attacks on Indigenous People During the 2022 Ecuador Strike},
  author={Conejo, Saire and Quelal, Jairo and Escobar, Silvana and Jima-Gonz{\'a}lez, Alexandra and Cuenca, Erick and Alc{\'a}ntara, Jos{\'e} {\'A}ngel},
  booktitle={Applied Engineering and Innovative Technologies},
  series={Lecture Notes in Networks and Systems},
  volume={1134},
  pages={267--275},
  year={2024},
  publisher={Springer},
  doi={10.1007/978-3-031-70760-5_25}
}
```

## Portfolio highlights

This project demonstrates an end-to-end applied NLP workflow and, importantly, connects the implementation to a published research output: **data preparation → EDA → text preprocessing → feature extraction → classification → evaluation → scientific communication**.
