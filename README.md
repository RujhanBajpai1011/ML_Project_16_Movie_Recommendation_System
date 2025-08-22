# 🎬 Movie Recommendation System

This project builds a content-based Movie Recommendation System using machine learning techniques. It suggests movies to users based on the similarity of their preferred movie's attributes (genres, keywords, cast, director, and tagline). The system leverages TF-IDF vectorization and cosine similarity to find these resemblances.

## 📊 Dataset

The core of this recommendation system is the `movies.csv` dataset. This dataset typically contains a wide range of information about various films, including but not limited to:

- **genres**: The categories or types of the movie (e.g., Action, Adventure, Fantasy).
- **keywords**: Important words associated with the movie's plot or theme.
- **tagline**: A memorable phrase or slogan used to promote the movie.
- **cast**: The main actors featured in the movie.
- **director**: The director of the movie.
- **title**: The title of the movie (used for user input and output).

Other features like budget, popularity, vote_average, overview, etc., are also present but selected_features are used for generating recommendations.

The dataset contains 4803 movies, each with 24 attributes initially, before feature selection.

## ✨ Features

**Data Loading and Initial Exploration**: Loads the `movies.csv` dataset into a pandas DataFrame and provides an initial overview of its structure, including the first 5 rows and the total number of rows and columns.

**Feature Selection**: Identifies and selects key textual features crucial for content-based recommendations: genres, keywords, tagline, cast, and director.

**Missing Value Handling**: Fills any missing (null) values in the selected_features with empty strings. This ensures that text processing doesn't encounter errors due to missing data.

**Feature Combination**: Concatenates all the selected features into a single string for each movie. This combined text forms the basis for similarity calculation.

**Text to Feature Vectors (TF-IDF)**: Converts the combined text features into numerical vectors using TfidfVectorizer. TF-IDF (Term Frequency-Inverse Document Frequency) assigns weights to words based on their importance in a document relative to the entire corpus, effectively capturing the essence of each movie's description.

**Similarity Calculation (Cosine Similarity)**: Computes the cosine similarity between all pairs of movie feature vectors. Cosine similarity measures the angle between two vectors, where a smaller angle indicates higher similarity. This results in a similarity matrix, where each value represents how similar two movies are.

**Interactive User Input**: Prompts the user to enter their favorite movie name.

**Close Match Finding**: Uses the difflib library to find the closest match to the user's input movie name from the dataset's movie titles, accounting for potential typos or variations.

**Recommendation Generation**: Based on the exact match (or the closest match), it retrieves the similarity scores of that movie with all other movies in the dataset.

**Sorting and Output**: Sorts the movies based on their similarity scores (in descending order) and recommends the top movies (excluding the input movie itself).

## 🛠️ Technologies Used

- **Python**: The primary programming language.
- **pandas**: For efficient data loading, manipulation, and structuring of movie data.
- **numpy**: For numerical operations, especially when working with feature vectors and similarity matrices.
- **difflib**: A Python library used to compute and compare sequences, specifically for finding close matches to user-input movie titles.
- **scikit-learn**: For core machine learning components:
  - **TfidfVectorizer**: To convert textual data into meaningful numerical feature vectors.
  - **cosine_similarity**: To calculate the similarity between movie feature vectors, forming the basis of recommendations.

## 📦 Requirements

To run this project, you will need the following Python libraries installed:

- pandas
- numpy
- difflib (usually part of Python's standard library, but good to list)
- scikit-learn

## 🚀 Getting Started

Follow these steps to set up and run the Movie Recommendation System on your local machine:

### Installation

1. Clone the repository (if applicable):
```bash
git clone <repository_url>
cd <repository_name>
```

2. Install the required Python packages:
```bash
pip install pandas numpy scikit-learn
```

(Note: difflib is a built-in Python module and typically doesn't need separate installation.)

### Usage

1. **Place the dataset**: Ensure the `movies.csv` file is located in the same directory as the Jupyter notebook (`Movie_Recommendation_System.ipynb`).

2. **Run the Jupyter Notebook**: Open and execute all the cells in the `Movie_Recommendation_System.ipynb` notebook using a Jupyter environment (e.g., Jupyter Lab, Jupyter Notebook, Google Colab).

The notebook will guide you through:
- Loading and preprocessing the movie data.
- Converting text features into a numerical representation.
- Calculating movie similarities.
- Prompting you to enter your favorite movie.
- Displaying a list of recommended movies based on your input.

## 🌟 How it Works

**Data Preparation**: Relevant text-based features (genres, keywords, tagline, cast, director) from the `movies.csv` dataset are extracted and combined into a single descriptive string for each movie. Missing values are handled to ensure data quality.

**Vectorization**: The TfidfVectorizer converts these combined textual descriptions into numerical TF-IDF vectors. Each vector represents a movie, and its dimensions correspond to the unique words in the entire corpus, with values indicating the importance of each word to that movie.

**Similarity Measurement**: The cosine_similarity function then calculates the similarity between every pair of movie vectors. This results in a square matrix where similarity[i][j] indicates how similar movie i is to movie j.

**Recommendation**: When a user inputs a movie name, the system finds the closest matching movie in the dataset. It then looks up this movie's row in the similarity matrix to get its similarity scores with all other movies. Finally, it sorts these scores to present a ranked list of the most similar movies as recommendations.

## 🧑‍💻 Contributing

We welcome contributions to enhance this movie recommendation system! Feel free to:

- Fork the repository.
- Create your feature branch (`git checkout -b feature/new-recommendation-logic`).
- Implement new features or improvements (e.g., adding more features for similarity, trying different similarity metrics, integrating user ratings).
- Commit your changes (`git commit -m 'Add new recommendation feature'`).
- Push to the branch (`git push origin feature/new-recommendation-logic`).
- Open a Pull Request.

## 📄 License

This project is open-source.
