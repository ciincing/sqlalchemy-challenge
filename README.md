# sqlalchemy-challenge

## Instructions
Congratulations! You've decided to treat yourself to a long holiday vacation in Honolulu, Hawaii. To help with your trip planning, you decide to do a climate analysis about the area. The following sections outline the steps that you need to take to accomplish this task.

## Part 1: Analyze and Explore the Climate Data
In this section, I used Python and SQLAlchemy to perform a basic climate analysis and data exploration of my climate database. Specifically, I utilized SQLAlchemy ORM queries, Pandas, and Matplotlib. To accomplish this, I followed the following steps:

1. I noted that I had to use the provided files (climate_starter.ipynb and hawaii.sqlite) to complete my climate analysis and data exploration.
2. I began by using the SQLAlchemy create_engine() function to establish a connection to my SQLite database.
3. Next, I employed the SQLAlchemy automap_base() function to reflect my tables into classes and then stored references to these classes, naming them station and measurement.
4. To establish a link between Python and the database, I created a SQLAlchemy session.
5. Then, I performed a precipitation analysis and then conducted a station analysis by completing the steps in the following two subsections.

### Precipitation Analysis
I found the most recent date in the dataset. Using that date, I retrieved the previous 12 months of precipitation data by querying the data from the past 12 months.
I selected only the "date" and "prcp" values from the query results.
I loaded the query results into a Pandas DataFrame and explicitly set the column names.
I sorted the DataFrame values by "date."
I plotted the results using the DataFrame plot method, as shown in the following image:<img width="544" alt="image" src="https://github.com/ciincing/sqlalchemy-challenge/assets/130705911/269d483e-d661-4579-8ceb-99788dabaf39">
Then, I used Pandas to print the summary statistics for the precipitation data.

### Station Analysis
I designed a query to calculate the total number of stations in the dataset. Additionally, I designed a query to find the most active stations, which are the stations with the most rows, and followed these steps:
I listed the stations and their observation counts in descending order (I did these by using the [func.count] function)
Next, I designed a query that calculated the lowest, highest, and average temperatures, filtering on the most-active station ID that I found in the previous query.
Then, Design a query to get the previous 12 months of temperature observation (TOBS) data. To do so, complete the following steps:
- Filter by the station that has the greatest number of observations.
- Query the previous 12 months of TOBS data for that station.
- Plot the results as a histogram with bins=12, as the following image shows:<img width="412" alt="image" src="https://github.com/ciincing/sqlalchemy-challenge/assets/130705911/6b911c61-a0fb-485e-8220-cc0db572949e">


## Part 2: Design Your Climate App
Now that I had completed my initial analysis, I proceeded to design a Flask API based on the queries I had developed. I created the following routes using Flask:
The "/" route, which serves as the homepage.
A route to list all available routes.
The "/api/v1.0/precipitation" route, where I converted the query results from my precipitation analysis (i.e., retrieving only the last 12 months of data) into a dictionary using "date" as the key and "prcp" as the value. I then returned the JSON representation of this dictionary.
The "/api/v1.0/stations" route, which returned a JSON list of stations from the dataset.
The "/api/v1.0/tobs" route, where I queried the dates and temperature observations of the most-active station for the previous year of data. I returned a JSON list of temperature observations for the previous year.
The "/api/v1.0/<start>" and "/api/v1.0/<start>/<end>" routes, which allowed users to specify a start date and, optionally, an end date. For a specified start date, I calculated TMIN, TAVG, and TMAX for all the dates greater than or equal to the start date. For a specified start date and end date, I calculated TMIN, TAVG, and TMAX for the dates from the start date to the end date, inclusive. The results were returned as JSON lists.
