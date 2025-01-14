# This Readme file is to highlight the project team contribution as per the rubric for Segment-2.

## Presentation

[google slides](https://docs.google.com/presentation/d/1b0U9tTp1LIhrh8zkYAMvX0BZqA8qRPFrOiRTJiwtGKI/edit?usp=sharing)

### Selected Topic

The topic has been selected as **"Win/Loss Prediction in Major League Soccer using Deep Learning model"**.

### Reason behind choosing this topic

Our team decided on this project because our home city, Austin, Texas, recently got its first MLS soccer club. **Austin FC**, a new member of the Western Conference, has had a hot start to the 2021 season. We wanted to dig into the historic perforamance of rival clubs and develop a **machine learning model** to predict outcomes for our home team's first season. 

### Description of the Source of Data

**Data Source** is the **Kaggle** data, Major League Soccer Dataset - by Joseph Mohr, last updated 11th July, 2021; version 34. The weblink: https://www.kaggle.com/josephvm/major-league-soccer-dataset

  This dataset contains player, game, event, and table data from Major League Soccer (MLS).

  There is currently information on over 6000 matches and almost 420,000 events from those matches.

### Questions we hope to answer with the data

![image](https://user-images.githubusercontent.com/58155187/127813723-fc574beb-701c-4300-a891-fe95db09245a.png)

### Data Exploration

In the data exploration stage, each member worked on their own .csv file to understand the data content i.e., columns, empty or null values. 

The key task in exploration was - 
- To understand most of the abbreviated column headers using Google search and match key columns (e.g., Team / CLub) with all 4 .csv files;
- Deciding which columns seem insignificant in decision making and may be dropped; 
- Identifying columns with data anomaly which needed to be cleaned.

### Data Analysis and Cleaning

Following steps summarize the process of data analysis including data cleaning where necessary,

- Updated column titles for clarity
- Fixed Goal_Differential calculation errors
- Removed all data prior to 2004 (due to most of the columns having null values)
- Removed seemingly insignificant data column
- Cleaned, renamed mismatching club names
- Removed duplicate entries
- Applied regex on a date column with anomaly in entry
- Fixed Points column calculations
- Reordered columns for clarity
- Exported the cleaned .csv files to the project folder
- These clean files are used in DB forming and ML processing phases

The following figure shows an example of **data cleaning** process,

![data_cleaning](https://user-images.githubusercontent.com/58155187/128083380-48edef5c-7b45-4041-a0ee-ace6d8f3e168.png)

### Creating an ERD for PostgreSQL Database

![QuickDBD-export](https://user-images.githubusercontent.com/58155187/128083646-835b9c1a-edad-449f-acd3-142afd558732.png)

### Creating an empty Database named "major_league_soccer" in PostgreSQL

![empty_db_mls](https://user-images.githubusercontent.com/58155187/128083845-81a91eac-7b79-478e-bbe8-fd5275f11f40.png)

### Export data from pandas DataFrame to PostgreSQL database

Exported 6 cleaned DataFrames to SQL tables and 2 tables are joined using SQL Query, as shown in the following figure,

![six_tables_to_mls_db_join](https://user-images.githubusercontent.com/58155187/128083949-ec90384f-0e70-41d9-a3b8-429acbe90cb4.png)

### Reading data from SQL Database

For Deep Learning preprocessing, data tables are imported from the SQL database as shown below,

![read_from_sql](https://user-images.githubusercontent.com/58155187/128084232-7f776d13-8a9b-482f-83b8-cf7fc510bb69.png)


## Machine Learning Model

[MLS_matches_NN.ipynb](https://github.com/moonem/FinalProject/blob/main/Segment_2/MLS_matches_NN.ipynb)

In order to predict a team's outcome in a game we chose **Neural Network** based **Deep Learning** algorithm. As the decision is kind of binary *yes / no*, we could choose other simpler *regression* based prediction algorithm also. Since neural network based algorithm provides better accuracy even with non-linear data relationship, *we preferred Deep Learning Model* over other prediction models.

  ### Data Preprocessing
  
  The data on matches is imported from SQL localhost server to a jupyter notebook for preprocessing. Following image screeshots of the **MLS_matches_NN.ipynb** link: [jupyter notebook](https://github.com/moonem/FinalProject/blob/main/Segment_2/MLS_matches_NN.ipynb) shows the steps of data preprocessing.
  
- Read data from SQL database:
  
  ![read_from_sql](https://user-images.githubusercontent.com/58155187/128084656-1c9a7470-1087-4df3-8c46-aa1b6107f6a8.png)

- Check categorical variables for OneHotEncoding:
 
 ![image](https://user-images.githubusercontent.com/58155187/128084901-7e709ac0-3058-4508-b525-374349d752c2.png)

- **OneHotEncoder** to encode categorical variables:

![image](https://user-images.githubusercontent.com/58155187/128085043-f220b549-e1c9-4a49-b9bf-3f5e07dfa03a.png)

- **Merging** `encode_df` with original `mls_matches`:

![image](https://user-images.githubusercontent.com/58155187/128085209-2f2507cc-89a8-4e53-b83e-606ad9dbe3ec.png)

- Define **features (X)** and **output (y)** in the *training* and *test* dataset :

We need to **split** our **training** and **testing** data *before* fitting our **StandardScaler** instance. This <u> prevents testing data from influencing the standardization </u> function.

To build our training and testing datasets, we need to separate two values:

input values (which are our *independent variables* commonly referred to as **model features or "X"**) and **target output** ( *dependent variable* commonly referred to as **target or "y"** in TensorFlow documentation).

![image](https://user-images.githubusercontent.com/58155187/128085484-825a5f7e-f654-47b5-b776-d1ec9e284bf2.png)

- **Scaling** training and testing dataset:

![image](https://user-images.githubusercontent.com/58155187/128085568-5a33f838-9187-48a2-b463-2c0bbd8afee9.png)

- Define the **neural network** model:

![image](https://user-images.githubusercontent.com/58155187/128085706-80fddcee-0663-4e34-9eb9-7dbd969f4bce.png)

- **Compile** and **Evaluate** the model:

![image](https://user-images.githubusercontent.com/58155187/128085771-729ef88a-3f85-4be7-bcd5-0a65646dea78.png)

### Findings from Deep Learning Model:

- A team outcome for the “Win” in a game is predicted with 99% accuracy.
- Observation:
  - The accuracy of the model seems “too good to be true”.
  - We’ve checked back again and made sure we followed all the steps we’ve learned in Module-19.

## GitHub

- The `main` branch has all data and codes in **Resources** folder. A copy of files relevant to *Segment-2* of the project, have been kept inside the **Segment_2** folder under the **FinalProject** folder; url: [Segment_2](https://github.com/moonem/FinalProject/tree/main/Segment_2).
- A separate **MLS_matches_NN.ipynb** file is created to design the machine learning model; [file url:](https://github.com/moonem/FinalProject/blob/main/Segment_2/MLS_matches_NN.ipynb)
- Communication protocols are defined in the **Readme.md** file for the project team.
- Outline of the project is described in the Readme.md which is updated regularly as the teamwork is progressing every week.
- Each of 4 team members have their individual brances. 
- Each team member is uploading their commits to their respective branch and/or to the `main` and 'Segment_2' project folders.

## Database

Details of PostgreSQL database creation, exportin files to database, importing from database, joining files using SQL Query - have been discussed in the previous sections.

## Dashboard

We will be presenting our analysis on Tableau, an interactive data visualization tool. The presentation will be in the form of a multi-dashboard Tableau story hosted online on Tableau Public. 

Our dashboards will incorporate historical data in the form of various team and player statistics from previous MLS seasons. We will be filtering our data by team and using team logo images as part of our filter-selection features. After selecting a team logo, the dashboard will present statistics like last year's top scorer, the team's record over the years, and data on average stadium attendance rates, among others.
