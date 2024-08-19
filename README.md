# Movie Review Sentiment Analysis with SVM

This project involves performing sentiment analysis on movie reviews using a Support Vector Machine (SVM) classifier. The analysis leverages Natural Language Processing (NLP) techniques, specifically TF-IDF (Term Frequency-Inverse Document Frequency) vectorization, to transform textual data into numerical features that the SVM can process.

## Project Overview

The primary objectives of this project are:
1. Load and preprocess the movie review dataset.
2. Build and evaluate a text classification model using an SVM pipeline.
3. Experiment with different stopword configurations to observe their effect on model performance.

## Dataset

The dataset consists of movie reviews labeled as either positive (`pos`) or negative (`neg`). The dataset is loaded from a CSV file named `imdb_reviews.csv` located in the `Resources` directory.

### Sample Data

| label | review                                                                                             |
|-------|-----------------------------------------------------------------------------------------------------|
| neg   | A very, very, very slow-moving, aimless movie about a distressed, drifting young man.               |
| neg   | Not sure who was more lost - the flat characters or the audience, nearly half of whom walked out.   |
| neg   | Attempting artiness with black & white and clever camera angles, the movie disappointed...          |
| pos   | The best scene in the movie was when Gerardo is trying to find a song that keeps running through... |

## Project Structure

### 1. Data Preprocessing

- **Load the dataset**:
  - The movie reviews are loaded into a pandas DataFrame.
  - The dataset is checked for missing values.

- **Feature and Target Variables**:
  - The `review` column is used as the feature variable (`X`).
  - The `label` column is used as the target variable (`y`).

- **Data Splitting**:
  - The data is split into training and testing sets with a 70-30 split using `train_test_split`.

### 2. Model Building

- **Pipeline Construction**:
  - A pipeline is constructed using `TfidfVectorizer` for text vectorization and `LinearSVC` for classification.

- **Model Training**:
  - The pipeline is fitted to the training data.

- **Model Evaluation**:
  - The model is evaluated on both training and testing sets to calculate accuracy.
  - A confusion matrix and classification report are generated to provide detailed performance metrics.

### 3. Experimenting with Stopwords

- **Default Stopwords**:
  - The model is first built without using stopwords, yielding a baseline accuracy.

- **English Stopwords**:
  - The second model is built using the default English stopwords in `TfidfVectorizer`.
  - This version shows a slight improvement in processing speed and accuracy.

- **Custom Stopwords**:
  - A custom list of stopwords is created and used to build the third model.
  - This approach further improves the model’s accuracy and highlights the importance of domain-specific stopwords in text classification.

### 4. Example Predictions

- A sample movie review is fed into each version of the model to observe how the classification changes based on different stopword configurations.

## Results

### Performance Metrics

- **No Stopwords**:
  - Train Accuracy: 99.8%
  - Test Accuracy: 74.2%
  
- **Default Stopwords**:
  - Train Accuracy: 99.0%
  - Test Accuracy: 75.6%

- **Custom Stopwords**:
  - Train Accuracy: 99.8%
  - Test Accuracy: 77.8%

### Confusion Matrix (Custom Stopwords)

|          | Predicted Neg | Predicted Pos |
|----------|---------------|---------------|
| **Actual Neg** | 77            | 34            |
| **Actual Pos** | 16            | 98            |

### Example Review Classification

The sentiment of the sample review about the "Barbie" movie changes across different models, demonstrating the sensitivity of the SVM classifier to the inclusion or exclusion of certain words in the stopword list.

## Conclusion

This project demonstrates the impact of preprocessing steps, particularly stopword removal, on the performance of an SVM classifier for sentiment analysis. Using a custom stopword list tailored to the specific domain can significantly improve model accuracy. Future work could include expanding the dataset, experimenting with other classification algorithms, and further refining the stopword list based on more detailed analysis.
