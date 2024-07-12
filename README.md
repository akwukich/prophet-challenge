# prophet-challenge
Module 8 Prophet Challenge


# Module 6 Read Me Notes

## Background

The purpose of this challenge was to prepare data for use by a recommendation system, which would provide users with movie reviews and the corresponding movies.

Data was extracted from two different sources: The New York Times API and The Movie Database (“TMDB”). Movie reviews from The New York Times were compiled into the reviews_df data frame. The titles from these movies were then used to access the corresponding details from TMDB, which were compiled into a second data frame, movie_list_df.

The data frames were merged and cleaned to the clean_df data frame to consolidate the information and then extracted to love_movie_reviews_and_details.csv. The .csv file has been prepared to provide the recommendation system with data that can be easily accessed, analyzed, and used to make a movie recommendation with specificity.

## Installation

#### The following dependencies are required to successfully run the project:
- import requests
- import time
- from dotenv import load_dotenv
- import os
- import pandas as pd
- import json
- from pandas import json_normalize

## Methodology
The project was completed in three phases: 
1. Access the New York Times API
2. Access TMDB API	
3. Merge and Clean the Data for Export
### Part 1 - Access the New York Times API
1. Using the variables that were provided in the starter code, I created a query_url. Our goal was to retrieve 200 results, but the New York Times API limits its results to 10 per page. Since we needed to access 20 pages of results, I created a for loop. Inside the loop, the following occurred:
2. The query_url was extended to include a variable page parameter.
3. I made a "GET" request and retrieved the JSON in a variable.
4. A 12-second interval was added between the queries to stay within the New York Times’ API query limit of 5 per minute.
5. A try-except clause was added to loop through the JSON data and add it review to the reviews_list. I used the print function to print the completed query page number to ensure that the loop was executed.
6. I converted the reviews_list to a Pandas DataFrame, and extracted the movie title from the “headline.main” column using the Pandas apply() method and a lambda function provided in the starter code. The extracted movie titles were saved into a new “titles” column, which was ultimately used to create a list of titles using the to_list() function. This “titles” list was then used to perform TMDB queries in Part 2.
### Part 2 - Access TMDB API
1. Using the “titles” list from Part 1 and the query_url provided in the starter code, I was able to perform queries using TMDB.
2. To account for TMDB API’s query limit, I initiated a request counter that would increment by 1 for each iteration through the titles list. For every request that was a multiple of 50, i.e. 50, 100, 150,  I added a time sleep.
3. Using a loop, I was able to make a “get request” using the title from the “title” list, which provided limited information regarding the movie. 
4. Using a try clause, the “movie id” was collected from these results and was then used with the details query to get and retrieve the full movie details.
5. When a movie’s details were successfully found, the results were cleaned and used to create a dictionary that was appended to a list, “tmdb_movies_list.” After a movie’s details were appended to the list, a print statement was drafted to indicate the title was found. Of the original 200 titles, details were retrieved for 154.
6. Where the “movie id” could not be found or was unable to be used to retrieve additional details, the except clause would be activated and print a statement that the movie was not found. This was the case for 46 of the original 200 titles.
7. The “tmdb_movies_list” containing the details for the 153 movies was converted to a DataFrame movie_list_df.

### Part 3 - Merge and Clean the Data for Export
1. In this final part, the DataFrames from Part 1 and Part 2, reviews_df and movie_list_df, respectively, were merged using an inner join on the common “titles” column. The rows that did not include matching data were dropped, resulting in the merge_df DataFrame, which contains 128 common titles. 
2. This merged data frame was cleaned, duplicates dropped, and the index was reset. 
This process ended up requiring more time than I expected, as I struggled with the extraction of genres, spoken_languages, and production_countries columns. Initially, I had attempted to complete this process using another for loop, but it wasn’t until I used list comprehension (and trial and error) that the extraction was successful. The data could be fixed by converting it to a string and removing the problematic characters.
3. Next, I dropped the duplicate rows and reset the index and I took some time to verify that the duplicates were dropped from the merged DataFrame. I used the value_counts function on the “title” column, which confirmed that there was only one duplicate title: “After Love.” I reviewed both rows and while the movies are related, they are different versions with different details and production information.  
4. Finally, after confirming the DataFrame was cleaned and did not contain duplicates, I exported it to a csv file. 

## Resources Consulted
As this challenge was the most difficult to date, I consulted several sources throughout the process. 

I consulted the starter code that was included with the challenges as well as the notes and activities from Modules 4, 5, and 6.

Beyond the class resources, I also relied on the API documentation. [The New York Times API Documentation](https://developer.nytimes.com/docs/articlesearch-product/1/overview) and [TMDB](https://developer.themoviedb.org/docs/search-and-query-for-details).

When I was stuck on the extraction in Part 3, I looked at [Stack Overflow](https://stackoverflow.com/questions/51566336/how-do-i-loop-through-an-entire-json-file-and-extract-the-data-into-variables) for help with extraction using list comprehension.



