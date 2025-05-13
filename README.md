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
The goal was to explore restaurant chains, analyze customer engagement through ratings and views, and identify spatial clusters using geolocation data.

## Project Overflow diagram 

![image alt](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/8f354df056224490c8026f93f5706bbdfc4c3c28/Workflow.PNG)

## Data Source

The dataset was provided by Cognifyz Technologies as part of my Python internship project. It contains information on restaurant names, cuisines, ratings, views, and locations.

## Key Objectives

- Analyze restaurant distribution and performance metrics across different cities
- Evaluate the relationship between online services (delivery, table booking) and restaurant ratings
- Investigate cuisine patterns and their influence on restaurant popularity
- Examine price range distribution and its correlation with service offerings
- Perform geographic clustering analysis to identify restaurant hotspots
- Analyze customer review patterns and sentiment in relation to restaurant ratings

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

![image alt](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/988c193f34ccdc2decdd90e081b4a666530aa555/Data%20cleaning%20screenshot.PNG)

### Exploratory Data Analysis

Several python functions were used to understand the structure of the data, check for null values, number of rows and columns,column names and data type

## Data Analysis 
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

![image alt](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/7cadebfb3bcead4be56608e4b5bcebb36e64050b/Distribution%20of%20Price%20Range%20Among%20Restaurants.png)

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
![image alt](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/7cadebfb3bcead4be56608e4b5bcebb36e64050b/Restaurants%20location.png)

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
![image alt](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/7cadebfb3bcead4be56608e4b5bcebb36e64050b/Correlation%20between%20votes%20and%20ratings.png)

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
![image alt](https://raw.githubusercontent.com/Gracesunday16/Restaurant-analysis-/7cadebfb3bcead4be56608e4b5bcebb36e64050b/Distribution%20of%20aggregate%20ratings.png)

## Results and Findings

- **Location-Based Clustering**:

  Major restaurant concentration found in a specific geographic zone, especially Cluster 41, which contains 7,549 restaurants.

  A smaller dense group, Cluster 29, holds 497 restaurants, while 47 outliers are scattered and identified as noise by DBSCAN.

- **Service Type vs. Pricing Trends**:

  Table booking is common in expensive restaurants (price range 4)
  Only 9.04% of high-end restaurants offer online delivery, showing a preference for dine-in over delivery.

  Cheapest restaurants (price range 1) almost never provide table booking (0.02%).

  Moderately priced restaurants (price range 2) are the most likely to offer online delivery (41.31%), balancing affordability with convenience.
  
- **Weak Link Between Popularity and Ratings**:

  A weak positive correlation (r = 0.3) exists between votes and ratings, meaning more votes don’t strongly predict higher ratings.


## Recommendations
- **Target High-Density Restaurant Areas for Promotions**:

  Focus marketing, partnerships, or delivery expansion in these dense clusters where restaurant activity is high and competition is visible. It increases visibility and customer access.

- **Use Table Booking as a Premium Feature**:

  Offer exclusive table reservation in premium restaurants to maintain a luxury image. Don’t invest in table booking systems for budget restaurants — it's not expected by customers.

- **Expand Online Delivery in Moderately Priced Restaurants**:

  Boost online delivery partnerships and infrastructure in mid-range restaurants. They cater to a wider audience willing to pay for convenience.

- **Improve Visibility and Engagement for Low-Vote Restaurants**:

  Encourage customers to leave reviews and ratings through loyalty programs or post-meal nudges to build trust and increase votes.

- **Consider Restaurant Location Strategy**:

  New restaurants should avoid overly saturated zones unless they offer a unique value. Underserved clusters (with fewer restaurants) might offer better opportunities for niche markets.

- **Pricing Strategy for Online Services**:

  Upscale restaurants could consider premium delivery experiences (e.g., personalized packaging, time slots) to expand their audience without reducing brand prestige.
  
## Contact
Grace Sunday

gracesunday16@gmail.com

[LinkedIn profile](https://www.linkedin.com/in/grace-sunday-b2b0622a6)

