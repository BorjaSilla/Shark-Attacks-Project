# Shark Attacks Data Analysis & Cleaning Project 🦈

<p align="center">
  <img src="/static/shark.png" width="60%" />
</p>

## Overview

This repository contains a data analysis and cleaning project focused on shark attacks. The project aims to explore and analyze shark attack data, clean and preprocess the dataset, and provide insights and visualizations regarding shark attacks worldwide.

## Table of Contents

- [Data Source](#data-source)
- [Project Structure](#project-structure)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)

## Data Source<a id="data-source"></a>

The shark attack data used in this project is obtained from [https://www.kaggle.com/datasets/teajay/global-shark-attacks], which provides comprehensive information about shark attacks worldwide. The dataset is in [CSV format](data/shark_attacks.csv) and includes various attributes such as date, location, species, and more.

## Project Structure<a id="project-structure"></a>

```plaintext
shark-attacks-analysis/
│
├── data/
│   ├── shark_attacks.csv
│   ├── shark_attacks_clean.csv
│
├── notebooks/
│   ├── Data_Cleaning.ipynb
│   ├── EDA.ipynb
│
├── README.md
└──LICENSE
```

## Data cleaning<a id="data-cleaning"></a>

#### 1. Understanding the data

First, I tried to understand the dataframe and make sense out of every column before establishing an objective.

- `Case Number`: unique identifier for the incident. In more recent data, it primarily consists of date values in the format yyyy.mm.dd.
- `Date`: The date of the incident, which can vary from specific calendar dates (dd-mnth-yyyy) to date ranges (e.g., 1845-1853) and relative dates (e.g., Before 1903).
- `Year`: The year of the incident. It may contain precise year values, but in some cases of date ranges or relative dates, it's represented as 0.0.
- `Type`: Describes how the incident happened.
- `Country`: Indicates the country where the incident occurred.
- `Area`: Specifies the geographical area within the country where the incident took place.
- `Location`: Provides more specific details about the incident's location within the area.
- `Activity`: Describes the activity the victim was engaged in at the time of the incident.
- `Name`: The name of the victim involved in the incident.
- `Sex`: Denotes the sex of the victim, typically recorded as 'M' for male or 'F' for female.
- `Age`: The age of the victim at the time of the incident.
- `Injury`: Details the nature of the injury sustained by the victim.
- `Fatal`: Indicates whether the incident resulted in a fatality, recorded as 'Y' for yes or 'N' for no.
- `Time`: Specifies the time of day when the attack occurred.
- `Species`: Identifies the species of the shark involved in the incident.
- `Investigator_or_source`: The source or investigator responsible for collecting and reporting the data.
- `PDF`: The reference to the name of a PDF document related to the attack.
- `href formulas`: A reference to online sources or formulas, which may link to PDF documents about the attack.
- `href`: Another reference to an online source, which may link to PDF documents about the attack.
- `Case Number 1`: A duplicate of the 'Case Number' column.
- `Case Number 2`: Another duplicate of the 'Case Number' column.
- `Original Order`: Represents the order in which the attacks were originally registered.
- `Unnamed 22` & `Unnamed 23`: These columns appear to contain NaN (empty) values and do not have any specific data.

#### 2. Normalize columns

Standarized the columns, made them all lowercase

#### 3. Remove duplicated rows

Removed all the duplicated rows, which were `19441`

#### 4. Remove duplicated rows

Fixed all the `NaN` values with `unknown` or `0` on the corresponding columns

#### 5. Incorrect values

- 1. First I took care of the `year` column, removing the `str` values from the column and the records earlier than `1700` which we can do since they were a small amount of records.
- 2. Normalized `type` column into `5 ` categories.
- 3. Normalized `country` column and removed errors.
- 4. Normalized `activity` column with a dictionary and fuzzywuzzy library.
- 5. Normalized `name` column.
- 6. Normalized `sex` column.
- 7. Normalized `age` column.
- 8. Normalized `species` column with fuzzywuzzy library.
- 9. Splitted `date` column into `year`, `month` and `day`.
- 10. Normalized `fatal` column.

#### 6. Exporting clean dataset

Exported the clean dataset into the `data` folder.

## Exploratory Data Analysis<a id="exploratory-data-analysis"></a>

As for the EDA I used **Tableau** as it is the most interactive way to display the insights.

- 1. Species vs Fatal: A complete view of the shark species information, displaying fatal rate and amount of attacks
- 2. Activity Category and Sex stacked bar chart: A visualization showcasing the amount of attacks per activity category and sex.
- 3. Time of the Day heatmap: A heatmap displaying the amount of attacks % per timeframe
- 4. Attacks per Year: A line chart with the amount of attacks per year.
- 5. Percentage of Fatal Attacks: A simple % indicator of Fatal Attacks
