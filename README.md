# Tweet Sentiment Classifier using MLPs

This project focuses on developing a sentiment classification model using Multi-Layer Perceptrons (MLPs) with variations in text representation techniques and hyperparameter tuning, leveraging a balanced subset of the Kaggle [Twitter Sentiment Analysis](https://www.kaggle.com/datasets/jp797498e/twitter-entity-sentiment-analysis) dataset.

## Project Overview
The key objectives were:

1. **Load and Preprocess Data**: We employed Kaggle's Twitter Sentiment Analysis Dataset, balanced the dataset, and applied text preprocessing steps including tokenization, lemmatization, and special token replacement.
2. **TF-IDF and Word Embeddings**: Conversion of text data into numerical features using TF-IDF and Word Embeddings, with further experiments on centroid-based embeddings.
3. **Classification Models**: Implementation and evaluation of the following classifiers:
   - Dummy Classifier (Baseline)
   - Logistic Regression with Cross-Validation
   - Multi-Layer Perceptron (MLP) with TF-IDF and Word Embedding features.
4. **Hyperparameter Tuning**: Optimization of MLP hyperparameters using the Keras Tuner for both TF-IDF and Word Embedding models.
5. **Evaluation Tools**: Use of precision-recall curves, learning curves, and F1-score to evaluate model performance.

## Dataset

The dataset used is Kaggle’s [Twitter Sentiment Analysis Dataset](https://www.kaggle.com/datasets/jp797498e/twitter-entity-sentiment-analysis), which originally consists of 100,000 tweets. To ensure a balanced approach, we selected 5,000 positive and 5,000 negative samples for training and evaluation.

## Preprocessing

The preprocessing steps included:
- **Tokenization and Lemmatization**: Leveraged the NLTK library to convert text into tokens, followed by lemmatization using WordNet POS tags to reduce dimensionality.
- **Special Token Replacement**: Replaced URLs, usernames, hashtags, and numbers with placeholders, ensuring they didn’t affect the sentiment analysis.
- **TF-IDF and Word Embedding**: Utilized the `TfidfVectorizer` for TF-IDF conversion, and pre-trained GloVe embeddings for word embeddings. Both unigram and bigram features were extracted from the text.

## Classification Models

### Dummy Classifier
A baseline model that always predicts the most frequent class. This simple method provides a point of comparison for more advanced models.

### Logistic Regression with Cross-Validation
Logistic regression was applied using K-Fold cross-validation (with three folds), providing a more robust estimate of performance compared to standard logistic regression. This was evaluated using precision, recall, and F1-score.

### Multi-Layer Perceptron (MLP)
An artificial neural network classifier implemented using Keras:
- **MLP with TF-IDF**: The MLP was trained on TF-IDF features and evaluated. Early stopping and dropout layers were employed to prevent overfitting.
- **MLP with Word Embeddings**: The MLP was also trained using word embedding features generated by the GloVe model. This version showed improvements after hyperparameter tuning.

## Hyperparameter Tuning

For the MLP models, hyperparameter tuning was conducted using the Keras Tuner library. Various parameters such as the number of layers, number of units in each layer, learning rates, and dropout rates were optimized through random search.

## Evaluation

### Learning Curves and Loss Curves
Tracked both accuracy and loss across epochs for both MLP models, providing insights into model performance during training.

### Precision-Recall Curves
Evaluated the trade-off between precision and recall using precision-recall curves. Models were compared based on the Area Under the Curve (AUC-PR), with the MLP using Word Embeddings performing best.

### F1 Scores
F1 scores were computed as the harmonic mean of precision and recall, with both macro-averaged and weighted-averaged versions considered to ensure fairness across classes.
