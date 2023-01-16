# DataLemur-SQL
### Data Science Skills [LinkedIn SQL Interview Question]
Given a table of candidates and their skills, you're tasked with finding the candidates best suited for an open Data Science job. You want to find candidates who are proficient in Python, Tableau, and PostgreSQL.

```
SELECT candidate_id
FROM candidates
WHERE skill in ('Python', 'Tableau', 'PostgreSQL')
GROUP BY candidate_id
limit 2
;
```

![image](https://user-images.githubusercontent.com/117888017/212627201-e7f01b69-80ff-40b3-bb90-99c685cb5ba5.png)

### Page With No Likes [Facebook SQL Interview Question]
Assume you are given the tables below about Facebook pages and page likes. Write a query to return the page IDs of all the Facebook pages that don't have any likes. The output should be in ascending order.

```
SELECT pages.page_id
FROM pages
LEFT OUTER JOIN page_likes AS likes
  ON pages.page_id = likes.page_id
WHERE likes.page_id IS NULL;
```
![image](https://user-images.githubusercontent.com/117888017/212627609-b8cf7def-6ef8-44ab-a857-d62ce0f3cef3.png)


### Unfinished Parts [Tesla SQL Interview Question]
Tesla is investigating bottlenecks in their production, and they need your help to extract the relevant data. Write a SQL query that determines which parts have begun the assembly process but are not yet finished.
```
SELECT part
  FROM parts_assembly
  WHERE finish_date IS NULL
  GROUP BY part
;
```

![image](https://user-images.githubusercontent.com/117888017/212628697-153f3f04-f054-47f9-9ee4-2a0bb27be9d6.png)

### Duplicate Job Listings [Linkedin SQL Interview Question]
Assume you are given the table below that shows job postings for all companies on the LinkedIn platform. Write a query to get the number of companies that have posted duplicate job listings.

Clarification:

Duplicate job listings refer to two jobs at the same company with the same title and description.

```
SELECT COUNT(*) AS co_w_duplicate_jobs
FROM
  (SELECT COUNT(*)
  FROM job_listings
  GROUP BY company_id, title, description
  HAVING COUNT(*) > 1) AS sub;
;
```

![image](https://user-images.githubusercontent.com/117888017/212630101-135d73d2-81e0-4ef0-89fd-f5e31b53b9b0.png)

### Laptop vs. Mobile Viewership [New York Times SQL Interview Question]
Assume that you are given the table below containing information on viewership by device type (where the three types are laptop, tablet, and phone). Define “mobile” as the sum of tablet and phone viewership numbers. Write a query to compare the viewership on laptops versus mobile devices.

Output the total viewership for laptop and mobile devices in the format of "laptop_views" and "mobile_views".

```
SELECT 
    SUM(CASE WHEN device_type = 'laptop' THEN 1 ELSE 0 END) AS laptop_views,
    SUM(CASE WHEN device_type IN ('phone','tablet') THEN 1 ELSE 0 END) AS mobile_views
FROM viewership;
```
![image](https://user-images.githubusercontent.com/117888017/212631833-231fb330-87e8-4d29-a7ee-3b534d1c4945.png)

### Average Post Hiatus (Part 1) [Facebook SQL Interview Question]
Given a table of Facebook posts, for each user who posted at least twice in 2021, write a query to find the number of days between each user’s first post of the year and last post of the year in the year 2021. Output the user and number of the days between each user's first and last post.

```
SELECT user_id,
       EXTRACT(DAYS FROM (MAX( post_date) - MIN( post_date))) as days_between 
FROM posts
WHERE EXTRACT(YEAR FROM post_date) = '2021'
GROUP BY user_id
HAVING COUNT(post_id)>1;
```

![image](https://user-images.githubusercontent.com/117888017/212633155-3dd8dd87-09ca-4b28-8b88-1d4999657fcd.png)




