# Investigating the Relationship Between Music Habits and Music Type with Mental Health States

## Overview
This project explores the relationship between **music listening habits, preferred music genres, and mental health conditions** such as **anxiety, depression, insomnia, and OCD**. The study utilizes statistical analyses to examine how different aspects of music consumption may influence mental health states.

## Features
- **Analyzes the correlation between music listening habits and mental health conditions.**
- **Investigates the impact of different music genres on mental health severity levels.**
- **Applies statistical models such as ANOVA, chi-square tests, and regression analysis.**
- **Utilizes a dataset of 736 responses from a music and mental health survey.**

## Installation
Download the dataset and related files:
- **Dataset**: [Download](https://www.kaggle.com/datasets/catherinerasgaitis/mxmh-survey-results?resource=download)
- **Google Colab Notebook**: run Music_Mental_Health/Final_analysis.ipynb


## Methodology
This study investigates the effects of **music habits and genre preferences** on mental health using statistical analysis techniques.

### **1. Data Collection**
The dataset consists of **736 survey responses** collected via Kaggle. Participants provided information on:
- Music listening habits (e.g., hours per day, streaming service, listening while working).
- Favorite music genres and listening frequency.
- Self-reported mental health conditions (anxiety, depression, OCD, insomnia).
- Perceived effects of music on mental health (improve, no effect, worsen).

### **2. Data Preprocessing**
- Categorical variables were encoded into numerical values.
- Mental health severity was categorized into **none, mild, moderate, and severe**.
- Composer and instrumentalist variables were merged into a **musical background** variable.

### **3. Hypothesis Testing**
#### **Hypothesis 1: Music Habits and Mental Health**
- **Analyzed the effect of music listening hours on mental health severity.**
- **Investigated the relationship between listening while working and mental health conditions.**
- **Used ANOVA and Kruskal-Wallis tests to compare severity levels across different groups.**

#### **Hypothesis 2: Music Preferences and Mental Health**
- **Examined the correlation between favorite genres and mental health conditions.**
- **Used chi-square tests to assess the relationship between music frequency and perceived mental health effects.**
- **Investigated whether listening to foreign music influences mental health.**

### **4. Visualization & Interpretation**
We visualized the relationships using heatmaps, bar charts, and histograms:

<p align="center">
    <img width="45%" alt="figure1" src="./images/figure1.JPG" />
    <img width="45%" alt="figure2" src="./images/figure2.JPG" />
</p>

## Experiment
### Dataset
We use the **Music & Mental Health Survey Dataset**, which contains:
- **736 responses** with **33 features**
- **Music listening habits, favorite genres, and mental health scores**
- **Categorical and numerical data suitable for statistical analysis**

### Training Setup
- **Statistical models used**: ANOVA, chi-square tests, linear regression, Kruskal-Wallis tests
- **Software**: Python (pandas, scipy, seaborn, statsmodels)

## Results
| Variable          | Test                 | Statistic | p-value  |
|-------------------|----------------------|-----------|----------|
| OCD Severity      | t-test               | 2.81      | 0.0051   |
| Depression Severity| t-test               | 1.28      | 0.2005   |
| Insomnia Severity | t-test               | 0.86      | 0.3902   |
| Anxiety Severity  | t-test               | 0.98      | 0.3299   |

### **Key Findings**
- **Increased music listening hours were associated with higher OCD and insomnia severity.**
- **Listening to music while working was significantly related to higher OCD scores.**
- **Genres like Metal, Rock, and EDM were correlated with higher levels of depression and anxiety.**
- **Listening to foreign language music showed minor effects on depression and anxiety.**

<p align="center">
    <img width="45%" alt="figure3" src="./images/figure3.JPG" />
    <img width="45%" alt="figure4" src="./images/figure4.JPG" />
</p>

## Conclusion
Our results indicate that **music habits and preferences influence mental health in complex ways**. While music can be a therapeutic tool, its impact varies depending on genre, listening duration, and individual mental health conditions. Future research can focus on:
- **Understanding causality between music listening habits and mental health conditions.**
- **Personalizing music therapy based on genre preferences and listening behavior.**
- **Exploring larger datasets to validate these findings.**

## Contributors

**Mahsa Aghazadeh**  
Graduate School of Data Science, KAIST  
Email: [mahsa_agz@kaist.ac.kr](mailto:mahsa_agz@kaist.ac.kr)  

**Alexandre Goujon**  
Department of Industrial & Systems Engineering, KAIST  
Email: [alexandre.goujon@kaist.ac.kr](mailto:alexandre.goujon@kaist.ac.kr)  

