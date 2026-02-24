# 🎬 Movie Recommendation System

A content-based movie recommendation system built with Python and Machine Learning. Given a movie title, the system suggests the top 30 similar movies by analyzing features like genres, keywords, tagline, cast, and director using **TF-IDF vectorization** and **cosine similarity**.

---

## 📌 Table of Contents

- [Overview](#overview)
- [How It Works](#how-it-works)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Example Output](#example-output)
- [Tech Stack](#tech-stack)

---

## Overview

This is a **content-based filtering** recommendation system. Unlike collaborative filtering (which relies on user behavior), this approach analyzes the intrinsic properties of movies themselves, genres, keywords, tagline, cast, and director, to measure similarity between films and surface meaningful recommendations.

---

## How It Works

The pipeline follows these steps:

1. **Load Data**: Read `movies.csv` into a Pandas DataFrame.
2. **Feature Selection**: Extract five descriptive columns: `genres`, `keywords`, `tagline`, `cast`, `director`.
3. **Handle Missing Values**: Fill any `NaN` entries with empty strings to prevent errors during vectorization.
4. **Feature Combination**: Concatenate the five selected columns into a single text string per movie.
5. **TF-IDF Vectorization**: Transform the combined text into numerical feature vectors using `TfidfVectorizer`. This weighs terms by how frequent they are in a movie's description relative to the whole dataset.
6. **Cosine Similarity**: Compute pairwise cosine similarity across all movie vectors, producing an N×N similarity matrix.
7. **User Input & Fuzzy Matching**: Accept a movie name from the user and use `difflib.get_close_matches` to find the closest title in the dataset, handling typos gracefully.
8. **Ranking & Output**: Sort all movies by their similarity score to the input movie (descending) and print the top 30 results.

```
User Input → Fuzzy Match → Find Index → Similarity Row → Sort → Top 30 Results
```

---

## Dataset
> **Note:** `movies.csv` is not tracked by Git due to its large size. Download it from the link below and place it in the root of the project before running.
>
> 📥 **[Download movies.csv from Google Drive](https://drive.google.com/file/d/1cCkwiVv4mgfl20ntgY3n4yApcWqqZQe6/view)**

---

## Project Structure

```
movie_recommendation_system/
│
├── Movie_Recommendation_System_using_Machine_Learning_with_Python.ipynb
│                          # Main Jupyter Notebook — full pipeline
├── movies.csv             # Dataset (not tracked by Git)
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
└── .gitignore             # Git ignore rules
```

---

## Dependencies

All dependencies are listed in `requirements.txt`. The core libraries are:

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/AyushMayekar/Movie-Recommendation-System
cd movie_recommendation_system
```

### 2. Create and activate a virtual environment

```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# macOS / Linux
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add the dataset

Place `movies.csv` in the root of the project directory.

### 5. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `Movie_Recommendation_System_using_Machine_Learning_with_Python.ipynb` and run all cells.

---

## Usage

When prompted inside the notebook:

```
Enter your favourite movie name :
```

The system will:
- Fuzzy-match the input to the closest title in the dataset.
- Compute similarity scores against every other movie.
- Print the **top 30 most similar movies**.

---

## Example Output

```
Enter your favourite movie name : Iron Man

Movies suggested for you :

1 . Iron Man 2
2 . Iron Man 3
3 . Avengers: Age of Ultron
4 . The Avengers
5 . Captain America: Civil War
...
```

---

## Tech Stack

- **Language:** Python 3.x
- **Environment:** Jupyter Notebook
- **ML Technique:** Content-Based Filtering (TF-IDF + Cosine Similarity)
- **Key Libraries:** NumPy, Pandas, scikit-learn, difflib