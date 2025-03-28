# Sentiment Analysis of Women's Clothing Reviews

## Overview
This project performs **sentiment analysis** on customer reviews from a women's clothing e-commerce dataset using **VADER (Valence Aware Dictionary and sEntiment Reasoner)** from the **NLTK library**. The analysis classifies reviews as **Positive, Negative, or Neutral** based on sentiment scores.

## Features
- Uses **VADER sentiment analysis** to classify customer reviews.
- Cleans dataset by removing missing reviews.
- Saves the sentiment-labeled dataset as a CSV file.

## Prerequisites
Ensure you have **Python** installed along with the required libraries:

### Install Dependencies
Run the following command to install the necessary libraries:
```sh
pip install pandas nltk
```

## Installation
Clone the repository and navigate to the project directory:
```sh
git clone https://github.com/yourusername/sentiment-analysis.git
cd sentiment-analysis
```

## Usage
### Example Code
```python
import pandas as pd
import nltk
from nltk.sentiment import SentimentIntensityAnalyzer

# Ensure NLTK resources are downloaded
nltk.download('vader_lexicon')

# Load dataset
df = pd.read_csv("Womens Clothing E-Commerce Reviews.csv")

# Drop rows with missing reviews
df = df.dropna(subset=['Review Text'])

# Initialize sentiment analyzer
sia = SentimentIntensityAnalyzer()

def get_sentiment(text):
    """Classify sentiment based on VADER scores."""
    score = sia.polarity_scores(text)['compound']
    if score >= 0.05:
        return "Positive"
    elif score <= -0.05:
        return "Negative"
    else:
        return "Neutral"

# Apply sentiment analysis
df['Sentiment'] = df['Review Text'].apply(get_sentiment)

# Display sample results
print(df[['Review Text', 'Sentiment']].head())

# Save results
df.to_csv("sentiment_analysis_results.csv", index=False)
print("Sentiment analysis completed. Results saved.")
```

### Expected Output (Sample)
```
                                      Review Text  Sentiment
0  Absolutely wonderful - silky and sexy and f...  Positive
1  Love this dress!  it's sooo pretty.  I happ...  Positive
2  I had such high hopes for this dress and re...  Negative
3  I love, love, love this jumpsuit. it's fun,...  Positive
4  I love this dress. it's so pretty. I happil...  Positive
```

## How It Works
1. **Loads the dataset** from a CSV file.
2. **Drops missing reviews** to avoid errors.
3. **Initializes** the VADER SentimentIntensityAnalyzer.
4. **Applies sentiment analysis**:
   - **Positive**: Score >= 0.05
   - **Negative**: Score <= -0.05
   - **Neutral**: Otherwise
5. **Saves the results** into `sentiment_analysis_results.csv`.

## Dataset Used
- The dataset used is **"Women's Clothing E-Commerce Reviews.csv"**.
- Ensure the CSV file is placed in the same directory as the script.

## Contributing
Feel free to contribute by improving the sentiment analysis model or testing with different datasets. Pull requests are welcome!

## License
This project is licensed under the **MIT License**.



