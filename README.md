# Movie Industry Analysis
This project is a set of real world data science practice from data cleaning, changing data types, data cleaning, EDA, to data visualization using **Python**. We are going to analyze and find insights as much we can get from the Movie Industry Data from IMDB. A Question that came in my mind while analyzing this project is, "Is the Movie Industry Really Dying? Because of Netflix, Prime, and other streaming platforms."

## Dataset
This dataset is collected from [Kaggle](https://www.kaggle.com/datasets/danielgrijalvas/movies). The dataset is scraped from IMDB and contains a list of Movies from 1986 to 2016. Each movie has the following attributes:
  - budget: the budget of a movie. Some movies don't have this, so it appears as 0
  - company: the production company
  - country: country of origin
  - director: the director
  - genre: main genre of the movie.
  - gross: revenue of the movie
  - name: name of the movie
  - rating: rating of the movie (R, PG, etc.)
  - released: release date (YYYY-MM-DD)
  - runtime: duration of the movie
  - score: IMDb user rating
  - votes: number of user votes
  - star: main actor/actress
  - writer: writer of the movie
  - year: year of release

## Data Cleaning
The dataset contains 7668 rows and 15 columns. After examining the data, we find that there are some missing data in columns "rating", "budget", and "gross". Before replacing these missing values, I created a new DataFrame with the same dataset, so the original dataset won't be affected. 
  - Drop columns with more than 30% missing values, this is for the "budget" column.
  - Drop rows where "rating" is missing as it's a very small percentage.
  - Fill missing values for numerical columns with the median of the column. This occurs for "score", "votes", "runtime", "gross" columns.
  - Fill missing values for categorical columns with the mode (most frequent value). This occurs for "released", "writer", "star", "country", "company".

After that, we calculate again the missing values in the dataset. The result is that there are **2114** missing values in the "budget" column. We simply replace the NaN values in budget with its mean. This, then gives us the result of a dataframe with 7591 **rows** and 15 **columns**.

We then change the data types for 3 columns that the types are float to integers, the columns are "budget","gross", and "votes". Also, we make a new "yaer_correct" column contianing the year from "release" column as a string. Followed by dropping the duplicates. From here, our dataset is ready to be analyzed.

## Data Analysis
For the data analysis, we want to find out what variables in the dataset are highly correlated. We also want to gain any insights that influence a movies popularity by their consumers. First, we want to focus on Budget High Correlations and Company High Correlations.

First, for finding High Correlations for the Budget, we want to make a regression plot to examine 2 variables "budget" and "gross". 

![image](https://github.com/CountingCrows/Movie_Industry_Analysis_Project/assets/85608120/acf4b525-c0c3-40d1-aa21-2844e87ff742)

The plot explains that there is a strong positive linear relationship between the 2 variables, but we also want to see more detail for other correlations within the dataset. This can be done by using the **pearsons** correlation for 6 variables including "budget", "gross", "score", "year", "votes", and "runtime". Then, we visualize the correlation using a heatmap.

![image](https://github.com/CountingCrows/Movie_Industry_Analysis_Project/assets/85608120/7d85f2cd-5133-40cb-a8e5-c2ab22ea71d9)

From the heatmap, we can conclude that:
- 0.71: strong correlation between budget and gross revenue
- 0.63: moderate correlation between votes and gross revenue

Second, for finding High Correlations for the Company, we want to make a new dataframe consisiting all columns that the data types are as object.

![image](https://github.com/CountingCrows/Movie_Industry_Analysis_Project/assets/85608120/905e5651-3232-4b58-8c4e-f82e654ffa6c)




