# Automidata-project
Background on the Automatidata scenario
Automatidata works with its clients to transform their unused and stored data into useful solutions, such as performance dashboards, customer-facing tools, strategic business insights, and more. They specialize in identifying a client’s business needs and utilizing their data to meet those business needs. 

Automatidata is consulting for the New York City Taxi and Limousine Commission (TLC). New York City TLC is an agency responsible for licensing and regulating New York City's taxi cabs and for-hire vehicles. The agency has partnered with Automatidata to develop a regression model that helps estimate taxi fares before the ride, based on data that TLC has gathered. 

The TLC data comes from over 200,000 taxi and limousine licensees, making approximately one million combined trips per day. 
# Project background
Automatidata is working on the TLC project. The following tasks are needed before the team can begin the data analysis process:

EDA and cleaning

Select and build visualization(s) type

Create plots to visualize relationships between relevant variables

Share your results with the Automatidata team

# Exploratory data analysis
In this activity, you will examine data provided and prepare it for analysis. You will also design a professional data visualization that tells a story, and will help data-driven decisions for business needs.

Please note that the Tableau visualization activity is optional, and will not affect your completion of the course. Completing the Tableau activity will help you practice planning out and plotting a data visualization based on a specific business need. The structure of this activity is designed to emulate the proposals you will likely be assigned in your career as a data professional. Completing this activity will help prepare you for those career moments.

The purpose of this project is to conduct exploratory data analysis on a provided data set. Your mission is to continue the investigation you began in C2 and perform further EDA on this data with the aim of learning more about the variables.

The goal is to clean data set and create a visualization.

This activity has 4 parts:

Part 1: Imports, links, and loading

Part 2: Data Exploration

Data cleaning
Part 3: Building visualizations

Part 4: Evaluate and share results
Throughout these project notebooks, I'll see references to the problem-solving framework PACE. The following notebook components are labeled with the respective PACE stage: Plan, Analyze, Construct, and Execute.
# PACE: PLAN
Identify any outliers:
What methods are best for identifying outliers?

Use numpy functions to investigate the mean() and median() of the data and understand range of data values
Use a boxplot to visualize the distribution of the data
Use histograms to visualize the distribution of the data
How do I make the decision to keep or exclude outliers from any future models?

There are three main options for dealing with outliers: keeping them as they are, deleting them, or reassigning them. Whether I keep outliers as they are, delete them, or reassign values is a decision that you make taking into account the nature of the outlying data and the assumptions of the model you are building. To help ME make the decision, I can start with these general guidelines:

Delete them: If I am sure the outliers are mistakes, typos, or errors and the dataset will be used for modeling or machine learning, then I am more likely to decide to delete outliers. Of the three choices, I’ll use this one the least.
Reassign them: If the dataset is small and/or the data will be used for modeling or machine learning, I am more likely to choose a path of deriving new values to replace the outlier values.
Leave them: For a dataset that I plan to do EDA/analysis on and nothing else, or for a dataset I am preparing for a model that is resistant to outliers, it is most likely that I am going to leave them in.
# Task 1. Imports, links, and loading
For EDA of the data, import the data and packages that would be most helpful, such as pandas, numpy and matplotlib.

Then, import the dataset.
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import datetime as dt
import seaborn as sns

df=pd.read_csv('2017_Yellow_Taxi_Trip_Data.csv')
```
# PACE: Analyze
# Task 2a. Data exploration and cleaning
Given our scenario, which data columns are most applicable? Which data columns can I eliminate, knowing they won’t solve our problem scenario?
Consider functions that help to understand and structure the data.
```python
head()
describe()
info()
groupby()
sortby()
```
Consider these questions:
What do you do about missing data (if any)?
Are there data outliers?
What do the distributions of variables tell about the question asking or the problem I am trying to solve?
```python
df.head(10)
```
![Screenshot 2023-11-14 012104](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/4cdd66af-fb3a-4503-9715-22b4c0ea599d)
```python
df.describe()
```
![Screenshot 2023-11-14 012435](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/83ba815a-e6ea-4747-9cc5-74b11383969c)
```python
df.info()
```
![Screenshot 2023-11-14 012714](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/d91d448e-69c0-45b4-978e-9f84ed082e42)
There is no missing data according to the results from the info() function.
# Select visualization type(s)
Select data visualization types that will help to understand and explain the data.

Now that I know which data columns I’ll use, it is time to decide which data visualization makes the most sense for EDA of the TLC dataset. What type of data visualization(s) would be most helpful?

Line graph
Bar chart
Box plot
Histogram
Heat map
Scatter plot
A geographic map
A box plot will be helpful to determine outliers and where the bulk of the data points reside in terms of trip_distance, duration, and total_amount
A scatter plot will be helpful to visualize the trends and patters and outliers of critical variables, such as trip_distance and total_amount
A bar chart will help determine average number of trips per month, weekday, weekend, etc.
# PACE: Construct
# Task 3. Data visualization
# Boxplots
```python
# Convert data columns to datetime
df['tpep_pickup_datetime']=pd.to_datetime(df['tpep_pickup_datetime'])
df['tpep_dropoff_datetime']=pd.to_datetime(df['tpep_dropoff_datetime'])
```
```python
# Create box plot of trip_distance
plt.figure(figsize=(7,2))
plt.title('trip_distance')
sns.boxplot(data=None, x=df['trip_distance'], fliersize=1);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/98e9440c-1a53-4bb0-8003-df3d02426333)
```python
# Create histogram of trip_distance
plt.figure(figsize=(10,5))
sns.histplot(df['trip_distance'], bins=range(0,26,1))
plt.title('Trip distance histogram');
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/8b2b3c81-2713-4c01-94f0-48ab8a0e8e53)
The majority of trips were journeys of less than two miles. The number of trips falls away steeply as the distance traveled increases beyond two miles.
```python
# Create box plot of total_amount
plt.figure(figsize=(7,2))
plt.title('total_amount')
sns.boxplot(x=df['total_amount'], fliersize=1);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/ce7d1c8e-b9e7-469f-be6e-8050193d6b5d)
```python
# Create histogram of total_amount
plt.figure(figsize=(12,6))
ax = sns.histplot(df['total_amount'], bins=range(-10,101,5))
ax.set_xticks(range(-10,101,5))
ax.set_xticklabels(range(-10,101,5))
plt.title('Total amount histogram');
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/c9608672-e885-4906-b5cf-da55ebd7dfe9)
The total cost of each trip also has a distribution that skews right, with most costs falling in the $5-15 range.
```python
# Create box plot of tip_amount
plt.figure(figsize=(7,2))
plt.title('tip_amount')
sns.boxplot(x=df['tip_amount'], fliersize=1);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/2c35e795-56e6-42ed-b64e-cd7ee3d8775e)
```python
# Create histogram of tip_amount
plt.figure(figsize=(12,6))
ax = sns.histplot(df['tip_amount'], bins=range(0,21,1))
ax.set_xticks(range(0,21,2))
ax.set_xticklabels(range(0,21,2))
plt.title('Tip amount histogram');
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/53790cd8-9352-4c84-a25f-4a3e1fcb78d8)
The distribution for tip amount is right-skewed, with nearly all the tips in the $0-3 range.
```python
# Create histogram of tip_amount by vendor
plt.figure(figsize=(12,7))
ax = sns.histplot(data=df, x='tip_amount', bins=range(0,21,1), 
                  hue='VendorID', 
                  multiple='stack',
                  palette='pastel')
ax.set_xticks(range(0,21,1))
ax.set_xticklabels(range(0,21,1))
plt.title('Tip amount by vendor histogram');
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/03abadb5-bc18-4529-89c9-d4793b27bebe)
Separating the tip amount by vendor reveals that there are no noticeable aberrations in the distribution of tips between the two vendors in the dataset. Vendor two has a slightly higher share of the rides, and this proportion is approximately maintained for all tip amounts.

Next, zoom in on the upper end of the range of tips to check whether vendor one gets noticeably more of the most generous tips.
```python
# Create histogram of tip_amount by vendor for tips > $10 
tips_over_ten = df[df['tip_amount'] > 10]
plt.figure(figsize=(12,7))
ax = sns.histplot(data=tips_over_ten, x='tip_amount', bins=range(10,21,1), 
                  hue='VendorID', 
                  multiple='stack',
                  palette='pastel')
ax.set_xticks(range(10,21,1))
ax.set_xticklabels(range(10,21,1))
plt.title('Tip amount by vendor histogram');
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/2ddfb679-e26c-44a2-b03a-12ff82947e4e)
The proportions are maintained even at these higher tip amounts, with the exception being at highest extremity, but this is not noteworthy due to the low sample size at these tip amounts.
```python
# Examine the unique values in the passenger_count column
df['passenger_count'].value_counts()
```
![Screenshot 2023-11-14 014729](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/cabe8180-b45b-4712-a819-ddcf3e5aa1b0)
Nearly two thirds of the rides were single occupancy, though there were still nearly 700 rides with as many as six passengers. Also, there are 33 rides with an occupancy count of zero, which doesn't make sense. These would likely be dropped unless a reasonable explanation can be found for them.
```python
# Calculate mean tips by passenger_count
mean_tips_by_passenger_count = df.groupby(['passenger_count']).mean()[['tip_amount']]
mean_tips_by_passenger_count
```
![Screenshot 2023-11-14 014945](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/d4b4e9fb-d890-48cd-bc9e-29c05fae6084)
```python
# Create bar plot for mean tips by passenger count
data = mean_tips_by_passenger_count.tail(-1)
pal = sns.color_palette("Greens_d", len(data))
rank = data['tip_amount'].argsort().argsort()
plt.figure(figsize=(12,7))
ax = sns.barplot(x=data.index,
            y=data['tip_amount'],
            palette=np.array(pal[::-1])[rank])
ax.axhline(df['tip_amount'].mean(), ls='--', color='red', label='global mean')
ax.legend()
plt.title('Mean tip amount by passenger count', fontsize=16);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/d99f38cc-7375-49ba-aa1e-f57ba002d01a)
Mean tip amount varies very little by passenger count. Although it does drop noticeably for four-passenger rides, it's expected that there would be a higher degree of fluctuation because rides with four passengers were the least plentiful in the dataset (aside from rides with zero passengers).
```python
# Create a month column
df['month'] = df['tpep_pickup_datetime'].dt.month_name()
# Create a day column
df['day'] = df['tpep_pickup_datetime'].dt.day_name()
```
```python
# Get total number of rides for each month
monthly_rides = df['month'].value_counts()
monthly_rides
```
![Screenshot 2023-11-14 015420](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/ab7aa033-2e27-441a-a52f-7acf3af94058)
The months are out of order.
Reorder the results to put the months in calendar order.
```python
# Reorder the monthly ride list so months go in order
month_order = ['January', 'February', 'March', 'April', 'May', 'June', 'July',
         'August', 'September', 'October', 'November', 'December']

monthly_rides = monthly_rides.reindex(index=month_order)
monthly_rides
```
![Screenshot 2023-11-14 015641](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/471536ac-5c17-48df-b893-a108e1ba6633)
```python
# Create a bar plot of total rides per month
plt.figure(figsize=(12,7))
ax = sns.barplot(x=monthly_rides.index, y=monthly_rides)
ax.set_xticklabels(month_order)
plt.title('Ride count by month', fontsize=16);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/a1b86fff-7652-4fd2-be9a-34374a69bbbf)
Monthly rides are fairly consistent, with notable dips in the summer months of July, August, and September, and also in February.
```python
# Repeat the above process, this time for rides by day
daily_rides = df['day'].value_counts()
day_order = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
daily_rides = daily_rides.reindex(index=day_order)
daily_rides
```
```python
# Create bar plot for ride count by day
plt.figure(figsize=(12,7))
ax = sns.barplot(x=daily_rides.index, y=daily_rides)
ax.set_xticklabels(day_order)
ax.set_ylabel('Count')
plt.title('Ride count by day', fontsize=16);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/a908eda6-2b39-4153-950a-a875ff89f122)
Suprisingly, Wednesday through Saturday had the highest number of daily rides, while Sunday and Monday had the least.
```python
# Repeat the process, this time for total revenue by day
day_order = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
total_amount_day = df.groupby('day').sum()[['total_amount']]
total_amount_day = total_amount_day.reindex(index=day_order)
total_amount_day
```
```python
# Create bar plot of total revenue by day
plt.figure(figsize=(12,7))
ax = sns.barplot(x=total_amount_day.index, y=total_amount_day['total_amount'])
ax.set_xticklabels(day_order)
ax.set_ylabel('Revenue (USD)')
plt.title('Total revenue by day', fontsize=16);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/5ade9879-b3cb-494e-b4d2-b5220980095d)
Thursday had the highest gross revenue of all days, and Sunday and Monday had the least. Interestingly, although Saturday had only 35 fewer rides than Thursday, its gross revenue was ~$6,000 less than Thursday's—more than a 10% drop.
```python
# Repeat the process, this time for total revenue by month
total_amount_month = df.groupby('month').sum()[['total_amount']]
total_amount_month = total_amount_month.reindex(index=month_order)
total_amount_month
```
```python
# Create a bar plot of total revenue by month
plt.figure(figsize=(12,7))
ax = sns.barplot(x=total_amount_month.index, y=total_amount_month['total_amount'])
plt.title('Total revenue by month', fontsize=16);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/9086a78d-229a-4d7f-b328-59cdeca5b29f)
Monthly revenue generally follows the pattern of monthly rides, with noticeable dips in the summer months of July, August, and September, and also one in February.
```python
# 1. Generate random points on a 2D plane from a normal distribution
test = np.round(np.random.normal(10, 5, (3000, 2)), 1)
midway = int(len(test)/2)  # Calculate midpoint of the array of coordinates
start = test[:midway]      # Isolate first half of array ("pick-up locations")
end = test[midway:]        # Isolate second half of array ("drop-off locations")

# 2. Calculate Euclidean distances between points in first half and second half of array
distances = (start - end)**2           
distances = distances.sum(axis=-1)
distances = np.sqrt(distances)

# 3. Group the coordinates by "drop-off location", compute mean distance
test_df = pd.DataFrame({'start': [tuple(x) for x in start.tolist()],
                   'end': [tuple(x) for x in end.tolist()],
                   'distance': distances})
data = test_df[['end', 'distance']].groupby('end').mean()
data = data.sort_values(by='distance')

# 4. Plot the mean distance between each endpoint ("drop-off location") and all points it connected to
plt.figure(figsize=(14,6))
ax = sns.barplot(x=data.index,
                 y=data['distance'],
                 order=data.index)
ax.set_xticklabels([])
ax.set_xticks([])
ax.set_xlabel('Endpoint')
ax.set_ylabel('Mean distance to all other points')
ax.set_title('Mean distance between points taken randomly from normal distribution');
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/90189b09-3ae8-4ec8-a424-f4a393cd3f39)
The curve described by this graph is nearly identical to that of the mean distance traveled by each taxi ride to each drop-off location. This reveals that the drop-off locations in the taxi dataset are evenly distributed geographically. Note, however, that this does not mean that there was an even distrubtion of rides to each drop-off point. Examine this next.
There are 49 numbers that do not represent a drop-off location.

To eliminate the spaces in the historgram that these missing numbers would create, sort the unique drop-off location values, then convert them to strings. This will make the histplot function display all bars directly next to each other.
```python
plt.figure(figsize=(16,4))
# DOLocationID column is numeric, so sort in ascending order
sorted_dropoffs = df['DOLocationID'].sort_values()
# Convert to string
sorted_dropoffs = sorted_dropoffs.astype('str')
# Plot
sns.histplot(sorted_dropoffs, bins=range(0, df['DOLocationID'].max()+1, 1))
plt.xticks([])
plt.xlabel('Drop-off locations')
plt.title('Histogram of rides by drop-off location', fontsize=16);
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/316450e3-00fc-4ba8-8b91-a46f5386f6cd)
Notice that out of the 200+ drop-off locations, a disproportionate number of locations receive the majority of the traffic, while all the rest get relatively few trips. It's likely that these high-traffic locations are near popular tourist attractions like the Empire State Building or Times Square, airports, and train and bus terminals. However, it would be helpful to know the location that each ID corresponds with. Unfortunately, this is not in the data.
# PACE: Execute
# Results and evaluation
I have learned .... the highest distribution of trip distances are below 5 miles, but there are outliers all the way out to 35 miles. There are no missing values.

My other questions are .... There are several trips that have a trip distance of "0.0." What might those trips be? Will they impact our model?

My client would likely want to know ... that the data includes dropoff and pickup times. We can use that information to derive a trip duration for each line of data. This would likely be something that will help the client with their model.
# Tableau
![Total distance and Total amount TLC 2017](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/5518be70-26bf-458d-b5e1-6658edf55448)
# Statistical Analysis
The goal is to apply descriptive statistic and hypothesis testing. The goal for this A/B test is to sameple data and analyze whether there is a relationship between payment type and fare amount.For example discover if customers who use credit cards pay high fare amounts than those who use cash.
# Imports and data loading
```python
import panadas as pd
from scipy import stats
```
As data has already loaded so I will move to next step.
As a data prfessional I will use descriptive statistics for exploratory data analysis. In general descriptive statistics is useful to quiclly explore and understand large amount of data. In this project it will help quickly to compare the avaerage total fare amount among different payment types.
```python
# descriptive stats code for EDA
taxi_data.describe(include = 'all')
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/115150f9-dd53-4cd3-ba37-a9d31a19fe62)
```python
taxi_data.groupby('payment_type')['fare_amount'].mean()
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/97aa8cef-4722-44fb-b46e-0badf4621890)
Based on the average shown, it appears that customers who pay in credit card tend to pay larger fare amount than those who pays in cash. However, this difference might arise from random sampling, rather than being true difference in fare amount. To assess whether the difference is statistically significant, I will conduct a hypothesis testing.
# Hypothesis Testing
Steps for conducting hypothesis testing:
1. State the null hypothesis and alternative hypothesis
2. chose a significance level
3. find the p-value
4. reject or fail to reject the null hypothesis
Note: For the purpose of this project, hypothesis test is main component for A/B test.
Ho : there is no difference in average fare amount between customers who use credit cards and customers who use case.
Ha : there is difference in average fare amount between customers who use credit cards and customers who use cash.
I choose 5% significance level and proceed with two-sample test.
```python
# Hypothesis test, A/B test
# Significance level
credit_card = taxi_data[taxi_data['payment_type'] == 1]['fare_amount']
cash = taxi_data[taxi_data['payment_type'] == 2]['fare_amount']
stats.ttest_ind(a = credit_card, b = cash, equal_var = False)
```
![image](https://github.com/Sufyantheanalyst/EDA_Automidata-project/assets/129004768/aa840012-148c-4ce9-b09c-17da7a70a27c)
since the p-value is significantly smaller than the significance level of 5%, I reject the null hypothesis and conclude that there is statistically significant difference in the average fare amount between customers who use credit card and who use cash.
# Communicate insights with stakeholders
1. The key business insight is that encouraging customers to pay with credit cards can generate more revenue for taxi cab drivers.
2. This project requires an assumption that passengers were forced to pay one way or the other, and that once informed of this requirement, they always compiled with it. The data was not collected this way; so an assumption had to be made to randomly group data entries to perform A/B test. This dataset does not account for other likely explanations. For example riders might carry not lots of cash, so its easier to pay for longer/father trips with a credit card. In other words, its far more likely that fare amount determines payment type, rather than vice versa.




