### Show Drop Down Table Data

##### Solution
Reduced 12 queries to single query 80% reduction, reduced, DAO impl code by 60%


### query optimization pagination and caching

Infinite API calls -> if spinnerCount == 1 show table, but it was stuck in infinite loop, removed the spinnerCount condition then it worked


4.96s ----> 3.28ms (units)
2.92s -----> 2.45s (portfolios)
7.21s -----> 3.97s (projects)
2.51s ------> 2.38s (Applications)
			(vulnerability)
4.7s -------> 2.5s (assessment)

