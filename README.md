# IS507 Final Project

## Echo Chamber Analysis on Reddit

This notebook analyzes political echo chambers on Reddit, focusing on data collection, text preprocessing, sentiment analysis, topic modeling, network analysis, and SIR modeling. The analysis examines communities in Democratic and Republican subreddits during the 2024 U.S. presidential election.

## Prerequisites
- Python Libraries: praw, pandas, numpy, torch, transformers, networkx, matplotlib, seaborn, nltk, tqdm, vaderSentiment, community
- API Access: Reddit API credentials to use PRAW for data collection. [Please register an API on your own to avoid triggering traffic limitations due to public api.](https://praw.readthedocs.io/en/stable/getting_started/quick_start.html)

## Notebook Overview

### 1. Import Necessary Libraries

This block loads libraries for data manipulation, sentiment analysis, network analysis, and visualization. These are foundational libraries used throughout the notebook. No parameters to configure here.

### 2. Data Collection

Collects posts and comments from specified political subreddits using Reddit’s API (PRAW).

#### Configurable Parameters:
- **democrat_subreddits** and **republican_subreddits**: Specify lists of subreddit names to collect data from each political group.
- **start_date** and **end_date**: Define the data collection range.
- **MAX_RETRIES** and **RETRY_BACKOFF**: Retry logic to handle API rate limits.
- **limit**: Set the number of posts collected per subreddit.

### 3. Text Processing

Processes the text data to prepare it for sentiment and topic analysis. This includes lowercasing, removing special characters, and lemmatizing.

#### Configurable Parameters:
- **preprocess_text()**: Customizable for additional preprocessing steps or modified stopword lists.

### 4. Sentiment Analysis

Applies a sentiment analysis model (twitter-roberta-base-sentiment) to classify text polarity across Democratic and Republican mentions.

#### Configurable Parameters:
- **tokenizer** and **model**: Use AutoTokenizer and AutoModelForSequenceClassification to adjust model choices.
- **sentiment_analysis()**: Modify max_length in tokenization to handle longer or shorter text inputs.

### 5. Topic Analysis

Performs a simple keyword-based topic identification to categorize mentions of political candidates within Democratic and Republican texts.

#### Configurable Parameters:
- **democrat_candidates** and **republican_candidates**: Keyword lists for each political party. Customize these lists to track additional figures or topics.

### 6. Network Graph Construction

Builds and visualizes a network graph of Reddit users and interactions based on comment-reply relationships to analyze community structures and possible echo chambers.

#### Configurable Parameters:
- **community_louvain**: Set parameters in this function to adjust community detection sensitivity.

### 7. SIR Model (Susceptible-Infected-Recovered)

Simulates an SIR model on the network graph to examine the spread of opinions or influence within communities.

#### Configurable Parameters:
- **infection_rate**, **recovery_rate**: Parameters for SIR modeling. Adjust these to simulate different spread dynamics.
- **initial_infected_ratio**: Specifies the proportion of initial infected (influenced) nodes.
