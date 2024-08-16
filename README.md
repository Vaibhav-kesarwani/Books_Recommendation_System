# Books Recommendation System 📚

## Introduction
Welcome to the Book Recommendation System! This project is designed to provide personalized book recommendations to users based on their reading preferences, behavior, and ratings. The system uses advanced algorithms like collaborative filtering and content-based filtering to suggest books that align with each user's unique tastes. This README will guide you through the project structure, dataset details, and how to run the system locally.

## Features
- **Personalized Recommendations:** Offers book suggestions tailored to individual users.
- **Multiple Algorithms:** Uses collaborative filtering, content-based filtering, and hybrid approaches.
- **Scalable:** Designed to handle large datasets efficiently.

## Dataset

### Overview
The dataset used in this project consists of three primary components:
1. **Books Dataset:** Contains details about the books such as title, author, genre, publication year, and book cover image.
2. **Users Dataset:** Stores user information including user ID, demographics, and reading history.
3. **Ratings Dataset:** Consists of user ratings for different books, which are crucial for generating recommendations.
4. **Author Ratings:** Includes ratings based on the author's overall contribution, calculated by considering the number of books they have written and their average ratings.

### Author Rating
Author Rating is an additional metric introduced in this system to evaluate an author's influence and consistency in producing quality content. This rating is derived by analyzing the number of books an author has written and the average ratings those books have received. This feature helps in providing more balanced recommendations by considering not only individual book ratings but also the overall credibility of the author.

![Author_rating_for_the_books_recommended_graph](https://github.com/user-attachments/assets/808d2121-31c2-45cf-be17-0d59a430de42)


### Source
The dataset was collected from [Hugging face](https://huggingface.co/datasets/nirajandhakal/goodreads-book-recommend) and includes:
- **Books.csv:** Contains columns like `BookID`, `Title`, `Author`, `Genre`, `Year`, and `CoverImage`.

### Preprocessing
Before using the dataset, it underwent several preprocessing steps:
- **Data Cleaning:** Removed duplicates, handled missing values, and standardized formats.
- **Normalization:** Ratings were normalized to a consistent scale.
- **Feature Engineering:** Additional features such as `AverageRating` and `GenreFrequency` were derived for enhanced recommendations.
![Books_raintg_graph](https://github.com/user-attachments/assets/8699d98e-99ae-4843-b5b0-c6b21093157b) 

## Installation

### Prerequisites
Make sure you have the following installed on your machine:
- Python 3.8 or higher
- pip (Python package installer)
- git (version control system)

### Steps
1. **Clone the Repository**
Clone the project repository to your local machine using git:
```bash
git clone https://github.com/Vaibhav-kesarwani/Books_Recommendation_System.git
cd Book_Recommendation_System
```

2. **Create a Virtual Environment (optional but recommended):**
```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

3. **Install Dependencies**
Install the required Python packages using pip:
```bash
pip install -r requirements.txt
```

4. **Set Up the Dataset**
Place the dataset files `books_data.csv` in the `root` directory.

## Usage
### Running the Project
To run the Book Recommendation System, follow these steps:

1. **Prepare the Dataset:**
Ensure that your `books_data.csv` file is in the root directory. This file should contain the text data and corresponding books info labels, separated by a colon `(:)`.

2. **Run the Script:**
Execute the main script to load the data and perform books recommendation:
```bash
python main.ipynb
```

3. **Output:**
The script will print the first few rows of the dataset to the console, showing the text samples and their associated book info labels.

## Model Training
The model training is performed within the `main.ipynb` script, which processes the text data, tokenizes it, and trains a Plot the model using plotly. You can modify the model architecture, training parameters, or the data processing steps within this script.
```python
def recommend_books(book_title, cosine_sim=cosine_sim):
    # Get the index of the book that matches the title
    idx = data[data['title'] == book_title].index[0]
    
    # Get the cosine similarity scores for all the books with this book
    sim_scores = list(enumerate(cosine_sim[idx]))
    
    # Sort the books based on the similarity scores
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)
    
    # Get the top 10 most similar books (excluding the input book)
    sim_scores = sim_scores[1:11]
    
    # Get the book indices
    book_indices = [i[0] for i in sim_scores]
    
    # Return the top 10 most recommended books
    return data['title'].iloc[book_indices]
```

## Prediction
After training the model, you can use it to predict books recommendation from new text inputs. Implement the prediction logic in a separate script or extend `main.ipynb` to include a prediction function.

## File Structure
Here is an overview of the project directory structure:
```lua
Book_Recommendation_System/
│
├── venv                     # To store the python library files in the virtual env
├── .gitignore               # Containg all the unwanted file venv file and etc.
├── book_data.csv            # The dataset file containing Books name, rating and author name labels
├── main.ipynb               # Jupyter notebooks for data exploration and analysis
├── requirements.txt         # List of dependencies
├── LICENSE                  # Containg the license for the project
└── README.md                # Project documentation (this file)
```

## Contributing
Contributions are welcome! If you'd like to contribute to this project, please follow these steps:

- Fork the repository & Star the repository
- Create a new branch (git checkout -b feature)
- Make your changes
- Commit your changes (git commit -am 'Add new feature')
- Push to the branch (git push origin feature)
- Create a new Pull Request

## License
This project is licensed under the MIT License - see the [LICENSE](https://github.com/Vaibhav-kesarwani/Books_Recommendation_System/blob/main/LICENSE) file for details.

## Acknowledgements
1. [Pnadas](https://pandas.pydata.org/)
2. [NumPy](https://numpy.org/)
3. [Hugging Face](https://huggingface.co/)
4. [Plotly](https://plotly.com/)
5. [SkLearn](https://scikit-learn.org/stable/)

## Contact
If you have any questions or suggestions, feel free to reach out to me at :
1. [GitHub](https://github.com/Vaibhav-kesarwani)
2. [Linkedin](https://www.linkedin.com/in/vaibhav-kesarwani-9b5b35252/)
3. [Twitter](https://twitter.com/Vaibhav_k__)
4. [Portfolio](https://vaibhavkesarwani.vercel.app)

**Happy Coding!** <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Fire.png" alt="Fire" width="30" align=center /><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Travel%20and%20places/Star.png" alt="Star" width="30" align=center />
