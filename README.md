# bingeplay---project4
# BingePlay Streaming Analytics (Week 4, Advanced SQL)

**Name:** Navya

## About the project
BingePlay is a made-up Indian streaming service. In this project I act as its first data analyst and answer 12 business questions using SQL. The data is in a MySQL database called `bingeplay`, and the queries are run from a Jupyter Notebook with Python.

## Tools used
- MySQL 8 (database)
- Python 3, Jupyter Notebook
- SQLAlchemy and PyMySQL (connect Python to MySQL)
- Pandas (read SQL results into tables)

## Files
| File | What it is |
|---|---|
| `bingeplay_navya.ipynb` | Notebook with all 12 queries, outputs and answers |
| `bingeplay_setup.sql` | Script that creates and fills the database (given by the academy) |
| `README.md` | This file |

## Database tables
| Table | Rows | What it holds |
|---|---|---|
| `users` | 3,000 | Signup date, city, age group, referral source |
| `subscriptions` | 4,497 | Plan, start and end date, status, price |
| `shows` | 100 | Category, language, rating, original or acquired, minimum plan |
| `watch_sessions` | 100,351 | Who watched what, when, how long, device |
| `ratings` | 5,000 | Star ratings given by users |

## How to run
1. Install MySQL and open MySQL Workbench.
2. Run `bingeplay_setup.sql` to create and load the `bingeplay` database.
3. Check the data: `SELECT COUNT(*) FROM watch_sessions;` should give 100351.
4. Install the packages: `pip install notebook pymysql sqlalchemy pandas`
5. Start Jupyter with `jupyter notebook` and open `bingeplay_navya.ipynb`.
6. In the connection cell, replace `YOUR_PASSWORD` with your own MySQL password.
7. Choose Kernel, then Restart and Run All.

## Questions and answers
| Q | Topic | Answer |
|---|---|---|
| 1 | Active revenue (30 Jun 2024) | 2,340 active subscriptions, ₹784,260 per month |
| 2 | Signups per month | Jan 350, Feb 400, Mar 500, Apr 550, May 600, Jun 600 |
| 3 | Device report | Mobile has the most sessions (50,172); length and completion are similar on all devices |
| 4 | Rating distribution | 71.34% of ratings are 4 or 5 stars |
| 5 | Originals vs acquired | Originals average 7.92 IMDb, acquired 6.63 (1.29 higher) |
| 6 | Binge days (Q2 2024) | 414 binge days; top user U02956 with 8 |
| 7 | Q1 signups who never watched | 226 of 1,250 users |
| 8 | Over-paying Premium/Family users | 7 users |
| 9 | Upgrade success cohort | 55 users, 64.96 days on average to upgrade |
| 10 | Cliffhanger comebacks | 4,345 events; top show S088 (Rayalaseema Raga) |
| 11 | Consecutive-week streaks | 1,675 users with 4+ weeks; longest streak 26 weeks |
| 12 | Churn signals (May to June) | 521 users |

## Key SQL ideas used
- **NULL handling:** `end_date IS NULL` (Q1) and `NOT EXISTS` instead of `NOT IN` (Q7).
- **Grouping and HAVING:** binge days are user + show + date with 5 or more sessions (Q6).
- **Subqueries and `NOT EXISTS`:** users who only watch Basic shows (Q8).
- **Window functions:** `ROW_NUMBER()` for first plan and first upgrade (Q9) and for streaks (Q11).
- **Self-join:** matching an unfinished session with a later one for the same show (Q10).
- **CTEs:** each step is a named, readable block, used to filter calculated columns (Q12).


