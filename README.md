# Restaurant Data Analytics: A Multi-Level Analysis Project 

## Table of content
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Key Objectives](#key-objectives)
- [Tools and Technologies ](#tools-and-technologies)
- [Why This Project Matters](#why-this-project-matters)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [ Data Analysis ](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Contact](#contact)
  
## Project Overview

This project is the culmination of my Data Analytics Internship at Cognifyz Technologies, where I performed an in-depth analysis of restaurant data to uncover business insights and geographical patterns.
The goal was to explore restaurant chains, analyze customer engagement through ratings and reviews, and identify spatial clusters using geolocation data.

## Project Overflow diagram 

![Project Overflow diagram](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/8f354df056224490c8026f93f5706bbdfc4c3c28/Workflow.PNG)

## Data Source

The dataset was provided by Cognifyz Technologies as part of my Python internship project. It contains information on restaurant names, cuisines, ratings, views, and locations.

## Key Objectives

- Analyze restaurant distribution and performance metrics across different cities
- Evaluate the relationship between online services (delivery, table booking) and restaurant ratings
- Investigate cuisine patterns and their influence on restaurant popularity
- Examine price range distribution and its correlation with service offerings
- Perform geographic clustering analysis to identify restaurant hotspots
- Analyze customer review patterns in relation to restaurant ratings

## Tools and Technologies 

- Python
- Pandas for data manipulation 
- NumPy for numerical operations
- Scikit-learn (DBSCAN) for clustering
- Matplotlib and Seaborn for data visualisation 

## Why This Project Matters

Restaurant owners, marketers, and analysts can use this kind of analysis to:

1. Identify top-performing chains across regions.
2. Detect potential areas for business expansion.
3. Understand customer behavior based on ratings and popularity.
4. Make data-driven decisions using location and engagement metrics.

## Data Cleaning and Preparation

The following task was performed in the initial data preparation phase:

1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting

![Data Cleaning](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/988c193f34ccdc2decdd90e081b4a666530aa555/Data%20cleaning%20screenshot.PNG)

### Exploratory Data Analysis

The following Python functions and methods were used to gain an initial understanding of the dataset:

- **df.shape** – to determine the number of rows and columns.

- **df.unique()** - to get a NumPy array of all the distinct values in each column.

- **df.info()** – to check data types and non-null counts for each column.

- **df.describe()** – to get summary statistics for numeric columns.

- **df.isnull().sum()** – to identify columns with missing values.
  
[View complete EDA and Data Cleaning](https://github.com/Gracesunday16/restaurant-data-analytics/blob/95a0ccbaf18b29e701b062790cc5e2d6a7f44233/Data%20Cleaning%20and%20EDA.ipynb)

## Data Analysis Tasks


## Level 1 task

**Task 1: Top Cuisines**
- Determine the top three most common cuisines in the dataset.
- Calculate the percentage of restaurants that serve each of the top cuisines.

**Task 2: City Analysis**
- Identify the city with the highest number of restaurants in the dataset.
- Calculate the average rating for restaurants in each city.
- Determine the city with the highest average rating.

**Task 3: Price Range Distribution**
- Create a histogram or bar chart to visualize the distribution of price ranges among the restaurants.
- Calculate the percentage of restaurants in each price range category.

**Task 4: Online Delivery**
- Determine the percentage of restaurants that offer online delivery.
- Compare the average ratings of restaurants with and without online delivery.

[View full solution to level 1](https://github.com/Gracesunday16/restaurant-data-analytics/blob/95a0ccbaf18b29e701b062790cc5e2d6a7f44233/Data%20analysis%20task%201.ipynb)

```
 Python

# BAR CHART SHOWING DISTRIBUTION OF PRICE RANGES AMONG THE RESTAURANTS

# Count occurrences of each price range
price_counts = df["Price range"].value_counts()

# Plot bar chart
plt.figure(figsize= (10, 5))
plt.bar( price_counts.index, price_counts.values, color="blue", edgecolor="black")

# Labels and title
plt.xlabel("Price range")
plt.ylabel("Frequency")
plt.title("Distribution of Price Range Among Restaurants")
plt.grid(axis= 'y', linestyle= '--', alpha= 0.6)

# Ensure x-axis ticks match the price range categories
plt.xticks(price_counts.index)

# Show the plot
plt.show()
```

![Price range distribution among restaurants](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/7cadebfb3bcead4be56608e4b5bcebb36e64050b/Distribution%20of%20Price%20Range%20Among%20Restaurants.png)


## Level 2 task

**Task 1: Restaurant Ratings**
- Analyze the distribution of aggregate ratings and determine the most common rating range.
- Calculate the average number of votes received by restaurants.

**Task 2: Cuisine Combination**
- Identify the most common combinations of cuisines in the dataset.
- Determine if certain cuisine combinations tend to have higher ratings.

**Task 3: Geographic Analysis**
- Plot the locations of restaurants on a map using longitude and latitude coordinates.
- Identify any patterns or clusters of restaurants in specific areas.

**Task 4: Restaurant Chains**
- Identify if there are any restaurant chains present in the dataset.
- Analyze the ratings and popularity of different restaurant chains.

[View full solution to level 2](https://github.com/Gracesunday16/restaurant-data-analytics/blob/95a0ccbaf18b29e701b062790cc5e2d6a7f44233/Data%20analysis%20task%202.ipynb)

```
Python

MAP DISPLAYING THE LOCATIONS OF RESTAURANTS

coords = df[['Latitude', 'Longitude']]
print(coords)

plt.figure(figsize=(10, 6))
plt.scatter(df['Longitude'], df['Latitude'], alpha=0.5, c='blue', edgecolors='black')
plt.title('Restaurant Locations')

plt.show()
PATTERNS AND CLUSTERS OF RESTAURANTS IN SPECIFIC AREAS

# Extract coordinates
coords = df[['Latitude', 'Longitude']]

# Apply DBSCAN
dbscan = DBSCAN(eps=0.01, min_samples=5, metric='haversine').fit(np.radians(coords))

# Add cluster labels to the DataFrame
df['Cluster'] = dbscan.labels_

# Count the number of restaurants in each cluster
cluster_counts = df['Cluster'].value_counts()

print(cluster_counts)
```
![Restaurant location](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/7cadebfb3bcead4be56608e4b5bcebb36e64050b/Restaurants%20location.png)

## Level 3 task

**Task 1: Restaurant Chains**
- Identify if there are any restaurant chains present in the dataset.
- Analyze the ratings and popularity of different restaurant chains.

**Task 2: Votes Analysis**
- Identify the restaurants with the highest and lowest number of votes.
- Analyze if there is a correlation between the number of votes and the rating of a restaurant.

**Task 3: Price Range vs. Online Delivery and Table Booking**
- Analyze if there is a relationship between the price range and the availability of online delivery and table booking.
- Determine if higher-priced restaurants are more likely to offer these services.

[View complete solution to level 3 task](https://github.com/Gracesunday16/restaurant-data-analytics/blob/95a0ccbaf18b29e701b062790cc5e2d6a7f44233/Data%20analysis%20task%203.ipynb)

```
Python

CORRELATION BETWEEN NUMBER OF VOTES AND RATING OF RESTAURANTS

correlation = df['Votes'].corr(df['Aggregate rating'])
print(f"Correlation between votes and rating : {correlation}")

# Scatter plot of votes vs. rating to visualize the correlation
plt.figure(figsize=(8,5))
sns.scatterplot(x=df['Votes'], y=df['Aggregate rating'])
plt.xlabel("Number of Votes")
plt.ylabel("Aggregate rating")
plt.title("Votes vs Rating of Restaurants")
plt.show()
```

```
Python

DISTRIBUTION OF AGGREGATE RATINGS

plt.figure (figsize= (10, 6))
plt.hist(df['Aggregate rating'], bins=10, color= 'skyblue', edgecolor= 'black')
plt.title ("Distribution of Aggregate Ratings")
plt.xlabel= ("Aggregate rating")
plt.ylabel= ("Frequeny")
plt.show()

# Define rating ranges
bins = [0, 1, 2, 3, 4, 5]  

# Labels for ranges
labels = ['0-1', '1-2', '2-3', '3-4', '4-5']  
df['Rating Range'] = pd.cut(df['Aggregate rating'], bins=bins, labels=labels, include_lowest=True)
```
![Distribution of aggregate rating](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/7cadebfb3bcead4be56608e4b5bcebb36e64050b/Distribution%20of%20aggregate%20ratings.png)



## Results and Findings

- **Location-Based Clustering**:

  Major restaurant concentration found in a specific geographic zone, especially Cluster 41, which contains 7,549 restaurants.

  A smaller dense group, Cluster 29, holds 497 restaurants, while 47 outliers are scattered and identified as noise by DBSCAN.

- **Service Type vs. Pricing Trends**:

  Table booking is common in expensive restaurants (price range 4)
  Only 9.04% of high-end restaurants offer online delivery, showing a preference for dine-in over delivery.

  Moderately priced restaurants (price range 2) are the most likely to offer online delivery (41.31%), balancing affordability with convenience.
  
  Cheapest restaurants (price range 1) almost never provide table booking (0.02%).

- **Weak Link Between Popularity and Ratings**:

  A weak positive correlation (r = 0.3) exists between votes and ratings, meaning more votes don’t strongly predict higher ratings.


## Recommendations
- **Target High-Density Restaurant Areas for Promotions**:

  Focus marketing, partnerships, or delivery expansion in the dense clusters where restaurant activity is high and competition is visible. It will increase visibility and customer 
  access.

- **Use Table Booking as a Premium Feature**:

  Offer exclusive table reservation in premium restaurants to maintain a luxury image. Don’t invest in table booking systems for budget restaurants — it's not expected by customers.

- **Expand Online Delivery in Moderately Priced Restaurants**:

  Boost online delivery partnerships and infrastructure in mid-range restaurants. They will cater to a wider audience that is willing to pay for convenience.

- **Consider Restaurant Location Strategy**:

  New restaurants should avoid overly saturated zones unless they offer a unique value. Underserved clusters (with fewer restaurants) might offer better opportunities for niche markets.

- **Pricing Strategy for Online Services**:

  Upscale restaurants could consider premium delivery experiences (e.g., personalized packaging, time slots) to expand their audience without reducing brand prestige.
  
## Contact
Grace Sunday

gracesunday16@gmail.com

[LinkedIn profile](https://www.linkedin.com/in/grace-sunday-b2b0622a6)

