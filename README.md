# Movies_ETL
## Wiki and Kaggle Movies ETL
#### The goal of the project is to:
  - EXTRACT: gather data from Wikipedia and Kaggle
  - TRANSFORM: clean-up and combine them 
  - LOAD: save them to SQL databases
##### Create Extract_transform_load function to accept 3 files and return 3 dataframes 
##### --------------------------------------------------------------------------------

#### Step #1
#### --------
###### Use ETL_function_test.ipynb to convert the following input files to python dataframes:

    * Wikipedia JSON
    * Kaggle metadata file
    * MovieLens ratings file

 Wiki movies dataframe

   ![Wiki Movies]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%231%20-%20wikimovies.PNG)

Kaggle Metadata dataframe

   ![Kaggle Metadata]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%231%20Kaggle%20metadata.PNG)

Rating dataframe
  
   ![Ratings DataFrame]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%231%20-%20ratings.PNG)

#### Step #2
#### -----------------------------------------------------------------------------------------------------------------------------------
##### Using ETL_clean_kaggle_data, the data in the Wiki movies JSON are first cleaned as below:
  
  -	Combine movie title in different languages into a single column
  - Clean up/rename the column titles

    ![Wiki Movies]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%232%20-%20step%20%2320%20-%20wiki-movies_df.PNG)

Wiki movies:
  -	Remove all non-movie rows
  -	Clean-up ‘Box Office’, ‘Budget’, ‘Running Time’, and ‘Release Date’ column values using regex

    ![Wiki movies columns]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%232%20-%20step%20%2321%20-%20wiki-movies_df%20columns.PNG)

#### Step #3:
#### -----------------------------------------------------------------------------------------------------------------------------------
##### Using ETL_clean_kaggle_data, the data in the Kaggle and Ratings files are cleaned as below:

Kaggle metadata:

    *	Remove all ‘adult’ movies
    *	Clean-up ‘video’, ‘budget’, ‘id’ and ‘release date’ columns

Merge Wiki and Kaggle data to Movie dataframe:

      * Inspect the merged data and replace redundant columns with the data from the more reliable format:
      *	Wiki: running_time
      *	Wiki: budget
      *	Wiki: box_office
      *	Rename the columns 
      
   ![Movies]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%233%20-%20step%20%2315%20-%20movies_df.PNG)      
      
Transform and merge ‘Ratings’ data to Movie Dataframe to create movies_with_ratings_df

      *	Clean-up ‘Time stamp’
      *	Add the ratings for the same movieId 
      *	Make column names meaningful

   ![Movies with Ratings]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%233%20-%20step%20%2314%20-%20movies_with_ratings_df.PNG)

   ![Del #3 step14]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%233%20-%20step%20%2314%20-%20movies_with_ratings_df.PNG)

Finally return the 3 dataframes to the calling function.

#### Step #4:
#### --------------------------------------------------------------------------------------------------------------------------------

##### Using ETL_create_database 

    * Save the data to tables in SQLPostgre movies_database by establishing connections using SQLAlchemy
    
    * SQL query to 6502 rows uploaded to movies table
    
   ![movies rows](    https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%234_movies_count.PNG)
      
     * Query to import Ratings file to movies_database in chunks
    
   ![Rating import]( https://github.com/JoRanjit/Movies_ETL/blob/main/Images/Del%20%234%20-%20ratings%20table%20import.PNG)
    
    * SQL query o show 26024289 rows.

    *	Query the tables to make sure all rows are transported correctly.
