# Periods & Product vs. Identity World Analysis

This repository contains the data, notebooks, and models used for analyzing discussions of menstrual products, inclusivity, and gender identity across Reddit communities.

## Repository Structure

- `Data Ingestion, Inspection, and Initial EDA.ipynb`: Ingests and cleans Reddit comments and posts from the "Product World" (e.g., r/menstrualcups, r/Periods, r/WomensHealth) and "Identity World" (e.g., r/ftm, r/asktransgender). 
- `Text Preprocessing & Enhanced Lexicon Engineering.ipynb`: Performs feature engineering based on expert-derived lexicons. Text preprocessing was done using regular expressions and `scikit-learn` to remove punctuation, stopwords, and low/high-frequency terms (without using NLTK or lemmatization/stemming). Lexicons were built to categorize comments into inclusive vs. exclusive language and other thematic narratives.
- `In-Depth EDA & Answering Core Questions.ipynb`: Contains exploratory data analysis investigating the volume, timeframe, and correlations of the engineered lexicon features.
- `Advanced Modeling (Sentiment & Topic Modeling).ipynb`: 
  - **Sentiment Analysis**: Uses VADER to calculate compound sentiment scores for each comment.
  - **Topic Modeling**: Uses BERTopic with the `all-MiniLM-L6-v2` sentence-transformer model. Topic reduction was performed algorithmically to determine the optimal number of topics (resulting in 90 topics for the r/ftm corpus and 49 topics for the r/menstrualcups corpus). Topic labels were assigned via c-TF-IDF.
- `Reviewer_Responses.ipynb`: A supplementary notebook addressing specific review comments. It includes code to generate a random sample for manual lexicon validation, calculates Mann-Whitney U and Chi-Square statistical tests for sentiment and lexicon frequency, adds `n=` labels to visualization axes, and outputs absolute comment counts behind the 0.03% inclusive language proportion.

## Environment & Requirements

The scripts use Python 3. Key dependencies include:
- `pandas`
- `numpy`
- `matplotlib` & `seaborn`
- `scikit-learn`
- `scipy` (for statistical testing)
- `bertopic` & `sentence-transformers`
- `vaderSentiment`

## Data Sharing & Validation

For lexicon validation, we drew a random sample of 200 comments (100 from each "world"). These are available in `lexicon_validation_sample.csv` and can be manually coded to compute precision, recall, and F1 scores against our algorithmic categorizations.
