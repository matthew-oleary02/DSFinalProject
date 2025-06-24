# Data Science Final Project: Twitter Sentiment Analysis of ChatGPT Discussions

## Project Overview

This project performs a comprehensive sentiment analysis on tweets related to ChatGPT and AI topics. Using a Kaggle dataset, we explored user opinions, extracted topics, analyzed trends across geography, time, and user groups, and performed clustering and topic modeling on the data.

---

## Dataset

- **Source:** [Kaggle - ChatGPT-4 Tweets Analysis Dataset](https://www.kaggle.com/code/praveensaik/chatgpt-4-tweets-analysis-eda/notebook)
- **Size:** ~500,000+ tweets  
- **Fields:** Username, text, user metadata (location, followers, favorites, verified), tweet date, hashtags, and source.

---

## Project Workflow

### 1️⃣ Data Collection & Cleaning

- Loaded `tweets.csv` dataset.
- Removed rows with missing text.
- Cleaned text via:
  - Lowercasing
  - URL removal
  - Stopword removal
  - Punctuation & digit removal
  - Lemmatization (NLTK)
  - Removal of Twitter-specific words ("tweet", "retweet", etc.)

### 2️⃣ Sentiment Labeling

- Applied combined sentiment analysis using:
  - **VADER** (rule-based)
  - **TextBlob** (polarity score)
- Classified each tweet as: `positive`, `neutral`, or `negative`.
- Encoded sentiment labels for further analysis.

---

## Feature Engineering

- Extracted additional features:
  - Text length
  - Hashtag count
  - Mention count
  - Uppercase count
  - Exclamation count
- Created factor-based keyword flags for:
  - **Ethics**, **Economics**, **Education**, **Employment**
- Extracted AI-specific keywords (ChatGPT, GPT, AI, LLM, etc.).

---

## Exploratory Data Analysis (EDA)

### Sentiment Distribution

- Most tweets were overwhelmingly **positive**.
- Generated sentiment-wise word clouds and hashtag frequency plots.
- Top hashtags:  
  - `#ChatGPT`, `#AI`, `#OpenAI`, `#GPT4`, `#MachineLearning`

### Geographic & Demographic Patterns

- Top locations: India, United States, London, Global.
- Verified accounts represented a small fraction but showed higher engagement.
- Top users (by followers) were major media accounts and influencers.

### Platform Sources

- Majority of tweets originated from:
  - `Twitter Web App`, `Twitter for iPhone`, `Twitter for Android`, and automation tools like `Zapier`, `Buffer`, `IFTTT`.

### Likes & Engagement

- Most liked tweets surpassed 1 million likes.
- Positive sentiment tweets had the highest average number of likes.

### Time Trends

- Visualized tweet activity and sentiment trends over time.
- Ethics, economics, education, and employment mentions showed varied temporal patterns.

---

## Unsupervised Modeling & Advanced Analysis

### 1️⃣ Clustering (TF-IDF + KMeans)

- Used TF-IDF vectors (top 1000 terms).
- Applied **KMeans clustering** (n=3 clusters).
- Visualized clusters using PCA and t-SNE dimensionality reduction.
- Silhouette Score: **0.0083** (indicates poor natural clustering structure due to complexity of social media text).

### 2️⃣ Topic Modeling (LDA)

- Extracted 5 latent topics:
  - ChatGPT / AI art / Machine Learning
  - AI tools & models
  - Google/Bing chatbots
  - AI writing/answering questions
  - NFTs, Web3, Crypto-related

- Analyzed dominant topic per tweet and sentiment distribution by topic.

### 3️⃣ N-gram Analysis

- Extracted common bigrams/trigrams.
- Top examples:
  - `"chatgpt ai"`, `"ai chatgpt"`, `"chatgpt openai"`, `"artificial intelligence"`, `"using chatgpt"`

### 4️⃣ Correlation Analysis

- Examined numeric features for relationships between tweet length, hashtags, mentions, favorites, and followers.

---

## Key Findings

- **Sentiment:** The public sentiment surrounding ChatGPT is predominantly positive.
- **Geography:** India and the US lead in volume of discussion.
- **Verified vs Non-Verified Users:** Verified users account for a small but highly engaged segment.
- **Trends:** Ethics and employment themes appear frequently alongside positive and negative sentiments.
- **Topic Modeling:** ChatGPT discussions often center around AI tools, chatbots, productivity, and financial applications.
- **Clustering & Topics:** Clustering showed limited separation in short tweet text, but LDA provided useful thematic groupings.

---

## Technologies Used

- Python  
- pandas, numpy, matplotlib, seaborn, plotly, squarify  
- scikit-learn (KMeans, PCA, t-SNE, LDA, Silhouette Score)  
- TextBlob, NLTK, VaderSentiment  
- wordcloud  
- Kaggle data platform

---

## Limitations

- Tweets are short, noisy, and often ambiguous — limiting clustering effectiveness.
- Sentiment detection could be improved by:
  - Using transformer-based models (e.g. BERT, RoBERTa)
  - Incorporating context beyond tweet text.
