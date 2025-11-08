# An Analysis of Movie Performance

In this part, you’ll gather data about popular movies and award winners. The goal is to build a dataset that you’ll later use to analyze what makes a movie successful and how awards and box office performance relate to one another.

### Part 1: Data Gathering
1. Scrape Best Picture Data.  
    * Scrape the [Best Picture wikipedia page](https://en.wikipedia.org/wiki/Academy_Award_for_Best_Picture).  
    * Extract for each year:  
        * Year  
        * Film Title  
        * Winner (Yes/No)  
    * Data cleaning tips:  
        * Ensure that year and film title columns are clean and consistent (no footnotes, parentheses, etc.).
        * Save the results as best_picture.csv.  
2. Gather Movie Data via TMDB API  
    a. Set up the API    
    * Create a free [TMDB account](https://developer.themoviedb.org/docs/getting-started)  
    * Generate an API key are review their documentation, especially:  
        * /discover/movie  
        * /movie/{movie_id}  
        * /search/movie  
    b. Collect top movies (2015-2024)  
    For each year from 2015 to 2024:  
        * Query TMDB for the top 100 movies (by vote count).  
        * For each movie, gather:  
            * Title  
            * Release Year  
            * Genre(s)  
            * Vote Average  
            * Vote Count  
            * Budget  
            * Revenue  
            * TMDB ID  
        * Store all results in a single DataFrame and export to movies_2015_2024.csv.
        * Hint: TMDB rate limits are generous for free accounts, but you should pause between requests (eg. time.sleep(0.25)). 
        * Some Oscar films may not appear in the top 100 by vote count. For any missing, use the /search/movie endpoint to add it.  

**Optional Extension: Actors and Actresses** 

1. Scrape Wikipedia for Best Actor and Best Actress Data
    * Scrape the following Wikipedia pages:  
        * [Best Actor](https://en.wikipedia.org/wiki/Academy_Award_for_Best_Actor)
        * [Best Actress](https://en.wikipedia.org/wiki/Academy_Award_for_Best_Actress)
    * Each apge contains tables of winners and nominees by year.
    * Extract the following columns:  
        * Year
        * Actor/Actress Name
        * Film Title
        * Winner (Yes/No)
    * Data cleaning tips:  
        * Remove footnote markers from names and movie titles.
        * Ensure that you save just the release year (eg. 2009 instead of 2009 (82nd))
        * Store the cleaned data as two csv files:  
            * best_actor.csv
            * best_actress.csv  

2. Collect Actor and Actress Filmographies  
    Using the data from your actor and actresses CSVs:  
    * Search TMDB for each recent performer (using /search/person). Note: you can start with 2015-2024 initially, but, if time allows, you can go back even further.
    * For each person, retrieve their movie credits using /person/{person_id}/movie_credits.  
    * Extract relevant fields for each movie, such as:  
        * Actor/Actress Name  
        * Movie Title  
        * Character Name (optional)  
        * Release Year  
        * Movie ID
    * Combine all filmographies into one file, actor_filmography.csv