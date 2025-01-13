## Module 6 Challenge: Data Sourcing with APIs
### Challenge Instructions:
You've been tasked to prepare some data for a recommendation system to help people find movie reviews and related movies. You will extract data from two different sources: The New York Times API and The Movie Database, then merge the data together. The text extracted from these APIs can later be used with natural language processing methods.
This Challenge has three parts, and must be completed in order:

Part 1: Access the New York Times API.

Part 2: Access The Movie Database API.

Part 3: Merge and Clean the Data for Export.
### Requirements
- Part 1: Access the New York Times API (35 points)
  - query_url is correctly constructed (2 points).
  - An empty list reviews_list is created (1 point).
  - A for loop is created to loop through 20 times (3 points).
  - The query_url is extended to include a page (1 point).
  - A GET request is made to retrieve results and the JSON data is stored in a variable called reviews (4 points).
  - A 12-second interval is used between queries (2 points).
  - A try-except clause is used (2 points).
  - Inside the try clause, there is a loop to loop through the reviews["response"]["docs"] list (3 points).
  - The reviews results are correctly appended to reviews_list (2 points).
  - The query page number is printed (1 point).
  - The except clause prints out the page number that had no results, then breaks from the loop (2 points).
  - json.dumps with the argument indent=4 is used to preview the first five results (2 points).
  - reviews_list is converted to a Pandas DataFrame using json_normalize() (2 points).
  - The title is extracted from the "headline.main" column and is saved in a new column "title" (3 points).
  - The "keywords" column is correctly converted to string data using the supplied extract_keywords function (3 points).
  - A list called titles is created from the "title" column using to_list() (2 points).
- Part 2: Access The Movie Database API (40 points)
  - Preparation (4 points):
  - An empty list called tmdb_movies_list is created (1 point).
  - A variable called request_counter is created and assigned the value of 1 (1 point).
  - A for loop is created to loop through the titles list (2 points).
  - Inside the titles for loop (12 points):
  - request_counter is incremented by 1 (1 point).
  - time.sleep(1) when request_counter reaches a multiple of 50 (3 points).
  - A GET request that sends the title to The Movie Database search is performed, and the JSON results are retrieved (4 points).
  - A try-except clause is used (3 points).
  - The except clause prints out a statement if a movie is not found (1 point).
  - -nside the try clause (20 points):
  - The movie ID is collected from the first result and saved as a variable (2 points).
  - A GET request is made using the movie query URL and movie ID to retrieve the full movie details in JSON format (4 points).
  - The genre names are extracted from the results into a list called genres (2 points).
  - The spoken_languages' English names are extracted from the results into a list called spoken_languages (2 points).
  - The production_countries' names are extracted from the results into a list called production_countries (2 points).
  - A dictionary is created with the specified 15 fields (4 points).
  - The results dictionary is appended to the tmdb_movies_list list (3 points).
  - A message is printed with the name of the movie to indicate that the title was found. (1 point)
  - Actions after the results are collected (4 points):
  - The first five results are previewed using json.dumps with the argument indent=4 (2 points).
  - The results are converted to a DataFrame called tmdb_df with pd.DataFrame() (2 points).
- Part 3: Merge and Clean the Data for Export (25 points)
  - The New York Times reviews and TMDB DataFrames are merged on the title column (4 points).
  - A list called columns_to_fix is created to store the names of the genres, spoken_languages, and production_countries columns (2 points).
  - A list is created called characters_to_remove containing [, ], and ' (2 points).
  - A for loop is created to loop through columns_to_fix (2 points).
  - The columns to fix are converted to the string data type (2 points).
  - characters_to_remove is looped through to remove the characters from the string using the Pandas str.replace() method (4 points).
  - The head of the updated DataFrame is displayed to confirm the list characters were removed (2 points).
  - The byline.person column is dropped (2 points).
  - Duplicate rows are deleted (1 point).
  - The DataFrame index is reset (1 point).
  - The DataFrame is exported to a CSV file without the index (3 points).
### Grade: 95
### Feedback from Grader:
Hello Geoff,



Thank you for completing and submitting this challenge.  Data is arguably the most important ingredient required in any data-driven decision-making process or model building. You have successfully sourced data from two different API servers. Sourcing reliable and cost-effective data is crucial to creating robust models and performing accurate analysis. Great job on the work done!

-----------------------------------------------------------------------------------------------------------------------------------------------------------



The code breaks very early in your program, this is caused by the path specified in the program. To solve this, use relative paths only, the path should not have any reference your computer's system like C:Users... but rather the working directory. This will ensure that your program runs error free when we run it to review it.



I want to commend the structure of your code. You set up the fields required for the NYT API call. This allows you to test out a simple API call and upon receiving a valid response, you can now proceed to making iterated API calls.  Very well done on adding a Try and Except, anticipating potential errors and catching them ahead of time shows good defensive programming and ensures the reliability of the data retrieval process. The 20 pages requested were returned, you parsed through the Json response object and performed some necessary data cleaning and finally transformed into a DataFrame, nicely done!!





-----------------------------------------------------------------------------------------------------------------------------------------------------------

Moving on, you used the titles list generated from the NYT API call in your next mission. You retrieved the relevant fields from the TMDB API server. You performed the necessary data cleaning needed to merge this DataFrame with the other NYT DataFrame you created. The only recommendation would be to parse through the JSON response object in a way that it does not generate strange errors like list index out of range but instead simply shows that that title was not found or could not be retrieved from the server. This is caused by the .get() method. The code should look like this

 genres = [genre["name"] for genre in tmdb_details["genres"]]



Great job here, you now have a cleaned dataset to be used in an application, to analyze or build a robust model. Sidenote, in order to make sure the model is accurate and generalizes well, you may have to repeat this process to obtain more data. 







You have essentially sourced your own data. This sets the tone for some exciting Modules ahead. Continue to put these skills to the test.





Best,

Learning Specialist -D.A.
Central Grader , Jun 23, 2024 at 6:01pm
