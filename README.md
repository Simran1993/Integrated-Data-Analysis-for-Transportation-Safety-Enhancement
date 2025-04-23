# Integrated Data Analysis for Transportation Safety Enhancement

## Table of Contents
- [Introduction](#introduction)
- [Business Understanding](#business-understanding)
- [Project Plan](#project-plan)
- [Data Understanding](#data-understanding)
  - [Collect Data](#collect-data)
  - [Describe Data](#describe-data)
  - [Explore Data](#explore-data)
  - [Verify Data Quality](#verify-data-quality)
- [Data Preparation](#data-preparation)
  - [Select Data](#select-data)
  - [Clean Data](#clean-data)
  - [Construct Data](#construct-data)
  - [Integrate Data](#integrate-data)
  - [Format Data](#format-data)
- [Data Modeling](#data-modeling)
  - [Classification](#classification)
  - [Clustering](#clustering)
  - [Association (Apriori)](#association-apriori)
  - [Outlier Detection](#outlier-detection)
- [Discussion of Results](#discussion-of-results)
- [Conclusion](#conclusion)
- [References](#references)

---

## Introduction
This project analyzes the **2020 Tabular Transportation Collision Data** for Ottawa to explore underlying factors contributing to traffic collisions. By leveraging data science methodologies, we aim to enhance road safety through evidence-based insights.

*Author: Harsimranjit Singh*

---

## Business Understanding
The goal is to uncover key factors leading to traffic collision fatalities and severe injuries in Ottawa, and empower stakeholders with actionable insights.

*Key Question:* What are the contributing factors for a collision to end up in a fatality?

---

## Project Plan

| Name             | Task               |
|------------------|--------------------|
| Diya Valand      | Classification     |
| Arshpreet Kaur   | Outlier Detection  |
| Harsimranjit Singh | Clustering       |

---

## Data Understanding

### Collect Data
The dataset includes detailed records of transportation collisions in Ottawa for 2020, available via [Open Ottawa](https://open.ottawa.ca).

### Describe Data
- **Instances**: 10,047
- **Attributes**: 28 (e.g., Accident_Date, Road_Surface_Condition, Light, Injury Severity)

### Explore Data
- Most collisions occurred at **non-intersections**
- Clear weather conditions led to the highest number of collisions
- Rear-end collisions were the most common impact type

### Verify Data Quality
- **Missing Values**: 8280 in `Max_injury`
- **Outliers**: Present in selected attributes
- No duplicates found

---

## Data Preparation

### Select Data
Selected 12 key attributes for focused analysis including accident time, location, injury count, and environmental conditions.

### Clean Data
- Missing values replaced with "Unknown"
- Normalization applied for clustering and classification

### Construct Data
- Extracted parts of the date and time
- Converted categorical to numerical where needed

### Integrate Data
- No external datasets were integrated

### Format Data
- Attributes formatted numerically for modeling

---

## Data Modeling

### Classification
- **Methods Used**: Decision Tree, Random Forest, k-Nearest Neighbors (kNN)
- Data split 70/30 (train/test)
- Key features: Season, Environment, Light, Road Surface, Injuries

### Clustering
- Used Elbow Method to determine optimal `k=4`
- Applied K-Means clustering and identified 4 clusters with distinct accident patterns

### Association (Apriori)
- Used FP-Growth algorithm
- Generated rules like:
  - Dry roads + property damage → Clear weather (confidence: 99.6%)
  - Non-intersection + no injuries → No traffic control (confidence: 100%)

### Outlier Detection
- **LOF (Local Outlier Factor)** and **ISF (Isolation Forest)** used
- Outliers mostly found in **Winter and Fall**
- Combined both methods for improved accuracy

---

## Discussion of Results

### Classification
- Environmental and road surface conditions strongly influence accident severity

### Clustering
- Identified clusters based on accident location, time, weather, and control presence

### Association Rules
- Strong correlations found between road, light, and environment conditions

### Outlier Detection
- Outliers linked to seasonal patterns, especially in Winter

---

## Conclusion

- **Most collisions** happen:
  - At intersections
  - On wet roads
  - In winter months
- **Most outliers** also occur in Winter, followed by Fall

---

## References

[1] el_chief, "RapidMiner Community," RapidMiner, November 2010. [Online]. Available: https://community.rapidminer.com/discussion/11263/apriori-algorithm-in-rapidminer
