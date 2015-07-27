Run queries on the `tutorial.billboard_top_100_year_end` database on the [Mode Analytics editor](https://modeanalytics.com/editor).

1. How many years did Mariah Carey have a song in the Top 10?

SELECT COUNT(*)
FROM tutorial.billboard_top_100_year_end
WHERE artist='Mariah Carey' AND year_rank < 11


2. A list of all Whitney Houston song titles that didn't rank higher than 20th, in chronological order.

SELECT song_name, year, year_rank
FROM tutorial.billboard_top_100_year_end
WHERE artist='Whitney Houston' AND year_rank < 20
ORDER BY year ASC


3. How many artists have finished a year with the number 1 song?

SELECT COUNT(*), artist
FROM tutorial.billboard_top_100_year_end
WHERE year_rank=1
GROUP BY artist
ORDER BY count DESC


4. In which year did Ke$ha have the most charted hits, and how many did she have that year? (Just one query...)

SELECT COUNT(*), year
FROM tutorial.billboard_top_100_year_end
WHERE artist='Ke$ha'
GROUP BY year
ORDER BY count DESC
LIMIT 1


5. What is the highest chart position ever reached by Ke$ha's sometime collaborators, the strangely-named "3OH!3"?

SELECT group, year_rank, year
FROM tutorial.billboard_top_100_year_end
WHERE group='3OH!3'
ORDER BY year_rank DESC
LIMIT 1


6. A list of years that had a charted song containing the word "heaven" and a count of the number.

SELECT year, COUNT(*)
FROM tutorial.billboard_top_100_year_end
WHERE song_name LIKE '%Heaven%'
GROUP BY year
ORDER BY year ASC