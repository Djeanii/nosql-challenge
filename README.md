# nosql-challenge

UK Food Establishment Hygiene Ratings - Data Analysis Project

Overview
In this project, I analyzed food hygiene ratings from establishments across the UK, with the data sourced from the UK Food Standards Agency. The goal of the project is to help a food magazine, Eat Safe, Love, evaluate and recommend food establishments. This was done by creating a MongoDB database, cleaning the data, and performing exploratory analysis to answer specific queries about food establishments.

The project consists of three main parts:

Database Setup: Importing and setting up the MongoDB database.
Database Updates: Inserting new data, modifying existing data, and cleaning the database.
Exploratory Data Analysis: Answering specific queries about food establishments based on hygiene scores and other criteria.
Part 1: Database and Jupyter Notebook Setup
I started by setting up the MongoDB database and importing the data from the provided establishments.json file.

Importing Data:

I used the following command in the terminal to import the data:
bash
Copy code
mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json
This command imports the data into a MongoDB database called uk_food and drops any existing establishments collection before importing the new data.
Setting up the Mongo Client:

In the Jupyter Notebook, I created an instance of the Mongo Client, connected it to my database, and checked that the data was loaded correctly.
I used find_one() to display a sample document from the establishments collection to ensure everything was set up correctly.
Part 2: Database Updates
I performed several updates to the database as requested by the magazine editors:

Adding a New Establishment:

I added a new halal restaurant called "Penang Flavours" to the database. I created a dictionary for the restaurant and inserted it into the establishments collection using the insert_one() method.
Updating the New Restaurant with Correct Business Type ID:

I queried the database to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and updated the new restaurant with the correct ID.
Removing Establishments in Dover:

Since the magazine wasn’t interested in Dover establishments, I queried the database to count and delete all documents with LocalAuthorityName set to "Dover."
Converting Data Types:

I used the update_many() method to convert the latitude and longitude fields from strings to decimal numbers and the RatingValue to integers, ensuring all numeric fields were correctly typed.
Part 3: Exploratory Analysis
I performed data analysis to answer specific questions posed by the magazine. Below are the main queries I worked on:

Establishments with a Hygiene Score of 20:

I wrote a query to find all establishments with a hygiene score of 20, counted the results, and displayed the first document. I then converted the results to a Pandas DataFrame to analyze the data.
Establishments in London with a RatingValue ≥ 4:

Using a query with a regex search for London-based establishments, I found all establishments with a RatingValue of 4 or more. I counted the results and displayed them in a Pandas DataFrame.
Top 5 Establishments Near "Penang Flavours" with a RatingValue of 5:

I performed a geographic query to find the top 5 establishments near "Penang Flavours" that have a RatingValue of 5. I sorted the results by hygiene score and displayed the results using Pandas.
Local Authority Areas with the Most Establishments Scoring 0 in Hygiene:

I used an aggregation pipeline to group establishments by LocalAuthorityName and count how many establishments in each area had a hygiene score of 0. The results were sorted from highest to lowest and converted to a DataFrame for further analysis.
Tools and Libraries Used
MongoDB: Used for database management.
PyMongo: Python library for MongoDB interactions.
Pandas: Used for data manipulation and analysis.
Pretty Print (pprint): For better readability of JSON-like data in Python.
Jupyter Notebook: For writing and running the Python code in an interactive environment.

Conclusion
Through this project, I was able to clean and analyze food hygiene data effectively, helping the magazine to identify areas of interest. Using MongoDB and Python, I demonstrated the full cycle of working with NoSQL databases—importing data, updating it, and running complex queries to derive insights.
