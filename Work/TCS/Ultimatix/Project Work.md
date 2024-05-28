### Show Drop Down Table Data

##### Solution
Reduced 12 queries to single query 80% reduction, reduced, DAO impl code by 60%


### query optimization pagination and caching

Infinite API calls -> if spinnerCount == 1 show table, but it was stuck in infinite loop, removed the spinnerCount condition then it worked

used index scan approach for pagination instead of LIMIT and OFFSET, which improved the performance very much

4.96s ----> 3.28ms (units)
2.92s -----> 2.45s (portfolios)
7.21s -----> 3.97s (projects)
2.51s ------> 2.38s (Applications)
			(vulnerability)
4.7s -------> 2.5s (assessment)


### UI Problem 

In Hello Canada work the backend was sending the html template for the mail section in icici which had links, so while converting to IOS app the links were not opening in a new window, so what we did was we sent header,body and links as api response to ffrontend and there used another library so that for ios the links will open in new window