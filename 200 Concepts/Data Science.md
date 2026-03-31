---
tags:
  - cs/ai/ml
created: 2026-03-23
status: draft
type: concept
---
---

>[!Definition]
> It's an interdisciplinary field that **extracts or extrapolates** knowledge from noisy, structured or unstructured data. It draws on techniques from diverse fields such as computer science, statistics, information science, algorithms and scientific computing.

## Intuition
Notice that the definition uses both extract and extrapolate. That's because data science is mainly used for two things: 
1. Capturing **patterns** or underlying structure present in the dataset.
2. Building **predictive models** (learning from existing data to generalize to new, unseen data)

- We can convert massive amounts of raw and unstructured data into meaningful insights. 

## Challenges in Data Science
### **Process Issues**

**Problem Identification** — Data scientists often jump into tools and data without clearly understanding the client's business requirement, leading to poorly designed solutions.

**Identifying the Issue** — Beyond understanding the data, data scientists must also make insights readable for non-technical people and use visualization tools to make data meaningful.

**Data Security** — Interconnected data sources are vulnerable to hacker attacks, requiring global data protection practices, cloud security measures, and even ML-based fraud detection to safeguard data.

### **Data Issues**

**Accessing the Right Data** — Getting the right data in the proper format is time-consuming, with issues like hidden data, insufficient volume, less variety, and difficulty gaining access permissions.

**Cleansing of the Data** — Databases full of inconsistencies and anomalies force data scientists to spend a vast amount of time sanitizing data before analysis, making it expensive and tedious.

**Data Quality** — Poorly curated data leads to flawed model outputs; as seen with Microsoft's Tay chatbot, algorithms only reproduce what they are trained on, making data curation a critical task.

**Data Quantity** — Complex models require large amounts of quality training data, and even unsupervised learning algorithms demand vast datasets to produce meaningful output.

**Multiple Data Sources** — Managing huge data from various platforms is challenging, though virtual data warehouses and cloud-based integrated platforms can help consolidate it effectively.

### **People Issues**

**Lack of Professionals** — Data scientists must bridge the gap between IT and top management, requiring both technical depth and domain expertise, which is difficult to find in a single professional.

**Lack of Domain Knowledge** — A fresh data scientist may have all the statistical skills but without domain understanding, they cannot determine what works and what doesn't in a given business context.

**Communication of Results** — Stakeholders are often non-technical, so findings must be presented in simple terms using metrics and KPIs rather than technical jargon to support business decision-making.

|Aspect|Data Analysis|Data Analytics|
|---|---|---|
|Definition|Process of inspecting, cleaning and modeling data to discover useful information|Broader discipline of using tools, techniques and systems to analyze data for decision making|
|Focus|Understanding **what happened**|Understanding **why it happened** and **what will happen**|
|Scope|Narrower — deals with a specific dataset or problem|Wider — encompasses the entire analytical process and strategy|
|Goal|Extract meaningful insights from existing data|Drive future business decisions and predictions|
|Approach|Mostly retrospective|Both retrospective and predictive|
|Techniques Used|Statistical analysis, data cleaning, visualization|Machine learning, data mining, predictive modeling, statistical analysis|
|Output|Reports, summaries, charts|Actionable insights, predictions, recommendations|
|Time Orientation|Past and present data|Past, present and future data|
|Tools|Excel, SQL, Tableau|Python, R, Hadoop, Spark, ML frameworks|
|Who Uses It|Analysts, researchers|Data scientists, business strategists|

In short — **Data Analysis** is a step or subset **within** Data Analytics. Analytics is the bigger umbrella that includes analysis plus prediction and decision-making.

## Related Concepts
