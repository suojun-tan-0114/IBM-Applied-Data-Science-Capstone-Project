# SpaceX Falcon 9 First-Stage Landing Prediction

## Overview

This project was completed as part of the **IBM Applied Data Science Capstone**. It applies an end-to-end data science workflow to SpaceX Falcon 9 launch data, with the goal of analyzing launch and landing patterns and predicting whether the Falcon 9 first stage will successfully land.

The project includes:

* Data collection using APIs and web scraping
* Data cleaning and wrangling
* Exploratory data analysis using Pandas, SQL, Matplotlib & Seaborn
* Interactive geospatial analysis using Folium
* An interactive dashboard using Plotly Dash
* Predictive modeling using Logistic Regression, Support Vector Machines, Decision Trees, and K-Nearest Neighbors along with Hyperparameter tuning and model evaluation using cross-validation

## 1. Data Collection

Launch data were collected using two approaches.

### SpaceX API

The SpaceX API was used to retrieve launch information, including:

* Flight number and launch date
* Booster versions
* Payload mass and orbit
* Launch sites
* Landing outcomes
* Booster reuse information
* Geographic coordinates

The data were converted from JSON responses into Pandas DataFrames and filtered to focus on **Falcon 9 launches**.

### Web Scraping

`BeautifulSoup` was used to scrape historical Falcon 9 launch records from a Wikipedia page.

The scraping workflow included:

1. Sending HTTP requests using `requests`
2. Parsing HTML using `BeautifulSoup`
3. Identifying launch-record tables
4. Extracting table headers and launch information
5. Cleaning irregular HTML content and annotations
6. Converting the extracted records into a Pandas DataFrame

## 2. Data Wrangling

The collected launch data were cleaned and prepared for analysis. Tasks included:

* Examining launch frequencies by launch site
* Examining the distribution of orbit types
* Analyzing landing outcomes
* Handling missing values
* Creating a binary `Class` target variable: 1` = successful landing; 0` = unsuccessful landing

The processed dataset contains **90 Falcon 9 launch records**, with an overall landing success rate of approximately **66.67%**.

## 3. Exploratory Data Analysis

### Pandas and Data Visualization

Exploratory data analysis was performed using Pandas, Matplotlib, and Seaborn.

The analysis examined relationships between:

* Flight number and launch site
* Payload mass and launch site
* Orbit type and landing success
* Flight number and orbit
* Payload mass and orbit
* Year and landing success rate

Categorical features such as orbit, launch site, landing pad, and booster serial number were also converted into dummy variables for predictive modeling.

One notable trend in the data is the general increase in Falcon 9 landing success over time, with success rates improving substantially during the later years represented in the dataset.

### SQL Analysis

SQLite was used to perform additional exploratory analysis. Queries included:

* Identifying unique launch sites
* Filtering launches by launch-site name
* Calculating total and average payload mass
* Finding the first successful ground-pad landing
* Identifying boosters with successful drone-ship landings
* Counting successful and failed missions
* Finding boosters carrying the maximum payload
* Analyzing failed drone-ship landings by year
* Ranking landing outcomes over selected time periods

## 4. Interactive Visual Analytics (Folium & Plotly Dash)

### Interactive Maps with Folium

Folium was used to explore the geographical locations of SpaceX launch facilities. The maps include:

* Launch-site markers
* Success and failure markers
* Marker clusters
* Geographic coordinates
* Distance calculations between launch facilities and nearby features such as coastlines and railways. 

### Plotly Dash Dashboard

An interactive dashboard was created using **Plotly Dash**. Users can:

* Select an individual launch site or view all launch sites
* Compare successful launches across sites
* Examine success and failure outcomes for a selected site
* Filter launches by payload mass
* Explore the relationship between payload mass, booster version, and landing success

## 5. Predictive Analysis

The objective of this machine-learning stage is to predict whether a Falcon 9 first stage will successfully land. 

Before model training, the data were split into training and test sets and numerical features were standardized using `StandardScaler`. The scaler was then fit only on the training data and subsequently applied to the test data to prevent data leakage. 
We also conduct Hyperparameters tuning using `GridSearchCV` and 10-fold cross-validation was used for model selection. 

Four classification algorithms were evaluated:

1. Logistic Regression
2. Support Vector Machine
3. Decision Tree
4. K-Nearest Neighbors

### Model Results

Results from the current saved notebook run are:

| Model                  | Best Cross-Validation Accuracy | Test Accuracy |
| ---------------------- | -----------------------------: | ------------: |
| Logistic Regression    |                         84.64% |        83.33% |
| Support Vector Machine |                         84.82% |        83.33% |
| Decision Tree          |                     **87.68%** |        83.33% |
| K-Nearest Neighbors    |                         84.82% |        83.33% |

The **Decision Tree** achieved the highest cross-validation accuracy in the current run. However, all four tuned models achieved the same **83.33% accuracy on the held-out test set**, so the test results do not show a clear performance advantage for any one classifier.

Confusion matrices were also used to examine classification errors for each model.

## Technologies Used

**Programming & Data Analysis**

* Python
* Pandas
* NumPy
* SQL / SQLite

**Data Collection**

* REST APIs
* Requests
* BeautifulSoup
* Web scraping

**Visualization**

* Matplotlib
* Seaborn
* Plotly
* Plotly Dash
* Folium

**Machine Learning**

* scikit-learn
* Logistic Regression
* Support Vector Machines
* Decision Trees
* K-Nearest Neighbors
* GridSearchCV
* StandardScaler

## Key Skills Demonstrated

This project demonstrates experience with:

* API-based data collection
* Web scraping
* Data cleaning and preprocessing
* SQL querying
* Exploratory data analysis
* Statistical visualization
* Feature engineering
* Geospatial visualization
* Interactive dashboard development
* Classification modeling
* Hyperparameter tuning
* Cross-validation
* Model evaluation

## Final Presentation

The final presentation summarizes the complete workflow, including:

* Business/problem context
* Data collection
* Data wrangling
* Exploratory analysis
* SQL analysis
* Interactive maps
* Plotly Dash dashboard
* Classification modeling
* Model evaluation
* Key findings and conclusions

## Acknowledgments

This project was completed as part of the **IBM Applied Data Science Capstone** on Coursera. The course provided the project framework, datasets, and lab templates; this repository contains my completed analyses, code, visualizations, model tuning, and final project work.

## Author

**Suo Jun Tan**
