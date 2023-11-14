# EDA_Automidata-project
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
print("Hello, world!")
