# ETL-Project-Team6

ELT - Extract Transform Load

Objective:
Create a database to check book popularity, price and information about the author for the books published between year 2015 to 2020. Our database will help track popular books by rating and number of reviews. 

Sources:
Original Source - https://zenodo.org/record/4265096#.Y5vlCVHMJD-
Web Scraping - from Wikipedia page for author information.

The Process
Extract :
i.	Downloaded good books data csv from zenodo.org
ii.	Web Scraping for the author information


Transform :
i.	Source 1 CSV file located at 
https://zenodo.org/record/4265096#.Y5vlCVHMJD-
-	The original dataset has around 50000 rows. We filtered the dataset for the books published in English and books published in latest 5 years in             the dataset that is 2015 to 2020 for web scraping purpose as well as interest towards latest books. There are about 3800 rows of data after                 filtering.
-	The original dataset has about 25 columns filtered down to 13 columns unnecessary columns were dropped.
-	title, author, rating, description, language, isbn, genres, pages, publishDate, publisher, numRatings, likedPercent, awards.
-	Author column has terms such as (Goodreads Author), (Translator), (Editor), (Foreword), (Pseudonym) and lots of non-alphabetical characters all of them     were split by commas, brackets into separate columns then they were dropped to create main author column which has author name.
-	PublishDate column has dates that are in different formats such as 09/14/08 for which we don’t know the exact year of release, some of the rows have       values that are not dates (published, expected publish dates) all of them were filtered and converted the remaining rows to one format (YYYY-MM-DD)         and created the column called year published.
-   Empty values in awards column is updated to 'not awarded'(as every book don't recieve award) to avoid data loss while dropping NA's.
-	All the rows that have NA values and/or duplicate ISBN numbers were dropped.
-	Genres and Awards had multiple values for each book. We removed unnecessary values, split the strings and added each unique value to a list. A specific     dataframe/table was created for awards and genres.
-   Page number, price were changed to int and float datatypes which were strings.

ii.	Source 2
Web Scraping:
-	Created the list of unique authors using python.
-	Scraped the Wikipedia page for the date of birth of the author.
-	Created a table for the author information.


Load:

We used sqlalchemy to load our data into the Book_db database. The database is relational(postgres). You can see the tables in this image of our Entity Relationship Database. It was created using QuickDBD.

![database_schemata_visual](https://user-images.githubusercontent.com/113364137/209022859-a17e3b16-54c4-427e-9fbc-b63a4d0215f9.png)

Sample Queries
1. SELECT *
FROM book
WHERE rating > 4.5 AND main author = 'Lucy Score'
ORDERBY rating DESC
Limit(5)

2. SELECT *
FROM author
INNER JOIN book 
ON book.main_author=author.main_author;

Analysis in future:
1. What age group of authors books were published in the period between 2015 to 2020 and which age group recieved more awards?
2. what genre is more popular/have more ratings?
3. Which books cost less as well as top rated?
4. Is price of the book effecting the popularity?
5. Which books recieved more number of awards?


