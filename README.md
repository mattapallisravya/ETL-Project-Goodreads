# ETL-Project-Team6

ELT - Extract Transform Load

Objective:
Create a database to help track book popularity, price and information about the author for the books published between year 2015 to 2020. Our database will help track popular books by rating and number of reviews. 

Sources:
Original Source - https://zenodo.org/record/4265096#.Y5vlCVHMJD-
Web Scraping - from Wikipedia page for author information.

The Process
Extract
    i.	Downloaded good books data csv from zenodo.org
    ii.	Web Scraping for the author information


Transform
    i.	Source 1
        https://zenodo.org/record/4265096#.Y5vlCVHMJD-
        -	The original dataset has around 50000 rows. We filtered the dataset for the books published in English and books published in latest 5 years in the dataset that is 2015 to 2020 for web scraping purpose as well as interest towards latest books.
        -	There are about 3800 rows of data after filtering.
        -	The original dataset has about 25 columns filtered down to 12 columns unnecessary columns were dropped.
        -	title, author, rating, description, language, isbn, genres, pages, publishDate, publisher, numRatings, likedPercent
        -	Author column has terms such as (Goodreads Author), (Translator), (Editor), (Foreword), (Pseudonym) and lots of non-alphabetical characters all of them were split by commas, brackets into separate columns then they were dropped to create main author column which has author name.
        -	PublishDate column has dates that are in different formats such as 09/14/08 for which we don’t know the exact year of release, some of the rows have values that are not dates (published, expected publish dates) all of them were filtered and converted the remaining rows to one format (YYYY-MM-DD) and created the column called year published.
        -	All the rows that have NA values were dropped.
        
        
        
        
        
                    [ADD MORE DATA HERE]
        -	**Pages column was in string format converted to int.
    -	**Genres :


            [ADD MORE DATA HERE]
                        [ADD MORE DATA HERE]
                                    [ADD MORE DATA HERE]
                                                [ADD MORE DATA HERE]




    ii.	Source 2
        Web Scraping:
        -	Created the list of unique authors.
        -	Scraped the Wikipedia page for the date of birth of the author.
        -	Created a table for the author information.


Load