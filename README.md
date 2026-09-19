# indigo-passenger-cargo-multivariate-analysis-

````markdown
# Passenger–Cargo Dynamics During Operational Disruptions: A Multivariate Analysis of Indian Domestic Aviation

## Overview

This repository contains the complete analytical workflow for a multivariate analysis of passenger, cargo, capacity, and utilization patterns in IndiGo's domestic operations.

The study examines monthly operational data from **2009 to 2025** using multivariate statistical techniques to identify operational regimes, detect extreme multivariate observations, and examine the relative relationship between passenger and cargo activity.

The analysis is observational and does not make causal claims regarding the effect of cargo activity on operational resilience.

---

## Research Questions

### RQ1
What distinct operational regimes characterize IndiGo's domestic operations across 2009–2025, and how do passenger and cargo metrics jointly define these states?

### RQ2
Which periods represent extreme multivariate operational observations, and what do these reveal about variation in joint passenger–cargo operations?

### RQ3
How does cargo activity compare with passenger activity during periods of suppressed passenger demand, and does this provide evidence of a complementary role for cargo?

---

## Research Objectives

- Apply Principal Component Analysis (PCA) and K-means clustering to identify multidimensional operational regimes.
- Identify extreme multivariate observations using robust Mahalanobis distance.
- Compare relative passenger–cargo activity across identified operational regimes.
- Examine passenger–cargo relationships using Spearman rank correlation.
- Interpret the observed operational patterns in the context of operational risk and resilience.

---

## Dataset

### Data Source

The analysis uses monthly domestic operational statistics for **IndiGo** covering **2009–2025**, derived from publicly available aviation statistics.

The raw Excel dataset is **not included in this repository**.

### Dataset Variables

The primary multivariate analysis uses the following six variables:

| Variable | Description |
|---|---|
| `Aircraft_Departures` | Number of aircraft departures |
| `Passengers_Carried` | Number of passengers carried |
| `Total_Cargo_Tonnes` | Total cargo carried in tonnes |
| `Available_Seat_Km` | Available seat kilometres |
| `Passenger_Load_Factor` | Passenger load factor (%) |
| `Weight_Load_Factor` | Weight load factor (%) |

Additional operational variables are present in the source dataset and were retained during data preparation.

---

## Methodology

The analytical workflow consists of:

```text
Data Ingestion
      ↓
Data Cleaning and Standardization
      ↓
Data Quality Assessment
      ↓
Missing-Value Assessment
      ↓
Multivariate Normality Assessment
      ↓
Principal Component Analysis (PCA)
      ↓
K-means Clustering
      ↓
Operational Regime Identification
      ↓
Relative Passenger–Cargo Activity Analysis
      ↓
Robust Mahalanobis Distance
      ↓
Spearman Rank Correlation
      ↓
Temporal Diagnostic
      ↓
Interpretation
````

### 1. Data Preparation

* Combined yearly worksheets into a unified monthly dataset.
* Standardized column names and date formats.
* Checked for duplicate observations.
* Assessed missing values.
* Performed range and logical consistency checks.
* Retained complete observations for the six-variable multivariate analysis.
* Standardized variables before PCA.

### 2. Multivariate Normality

Multivariate normality was assessed using **Mardia's multivariate skewness and kurtosis tests**.

The results indicated significant departures from multivariate normality. Therefore, methods requiring strict multivariate normality were not used as the primary analytical approach.

### 3. Principal Component Analysis

PCA was applied to the standardized six-variable dataset to reduce dimensionality while preserving the major sources of variation.

The first two principal components were retained based on:

* Eigenvalues
* Explained variance
* Scree plot
* Cumulative explained variance

### 4. K-means Clustering

K-means clustering was performed using the retained PCA scores.

Candidate values of:

```text
k = 2, 3, 4, 5, 6
```

were evaluated using silhouette scores.

The final analysis used **three operational clusters**.

### 5. Operational Regime Analysis

The identified clusters were profiled using the original operational variables to characterize differences in:

* Operational scale
* Passenger activity
* Cargo activity
* Available capacity
* Passenger utilization
* Weight utilization

### 6. Relative Passenger–Cargo Activity

Relative cargo activity was calculated using standardized passenger and cargo activity:

```text
Relative Cargo Activity
= Cargo Activity Z-score − Passenger Activity Z-score
```

Positive values indicate that cargo activity was relatively stronger than passenger activity for that observation.

### 7. Robust Multivariate Extreme Detection

Robust Mahalanobis distance was calculated using **Minimum Covariance Determinant (MinCovDet)** estimation.

This was used to identify empirical multivariate extreme observations while reducing sensitivity to the influence of extreme observations on the covariance structure.

### 8. Spearman Rank Correlation

Spearman rank correlation was used to examine associations between:

* Relative cargo activity and passenger load factor
* Relative cargo activity and weight load factor

The analysis was conducted both overall and within the identified under-utilized operational regime where appropriate.

---

## Key Results

### PCA

The first two principal components explained:

| Component     | Explained Variance |
| ------------- | -----------------: |
| PC1           |             68.09% |
| PC2           |             29.22% |
| **PC1 + PC2** |         **97.31%** |

**PC1** primarily represented operational scale/activity, with strong contributions from aircraft departures, passengers carried, total cargo, and available seat kilometres.

**PC2** primarily represented utilization, with strong contributions from passenger load factor and weight load factor.

---

### K-means Clustering

Three operational regimes were identified.

| Cluster   | Observations |  Share |
| --------- | -----------: | -----: |
| Cluster 0 |          102 | 53.68% |
| Cluster 1 |           21 | 11.05% |
| Cluster 2 |           67 | 35.26% |

The silhouette score for the selected three-cluster solution was:

```text
0.4864
```

The regimes were characterized as:

* **Cluster 0:** Low-scale / efficient-utilization regime
* **Cluster 1:** Under-utilized / constrained regime
* **Cluster 2:** High-scale / high passenger-utilization regime

---

### Multivariate Extreme Observations

Robust Mahalanobis analysis identified two empirical extreme observations:

* **August 2020**
* **November 2025**

These observations represent unusual multivariate combinations of operational activity and utilization.

They should be interpreted as **empirical multivariate extremes**, not as statistically significant anomalies, because multivariate normality was rejected.

---

### Passenger–Cargo Relationship

Relative cargo activity was higher during periods in which passenger activity was comparatively weaker.

Across the complete analysis sample:

```text
Relative Cargo Activity vs Passenger Load Factor
Spearman ρ = -0.4472
p < 0.001
```

```text
Relative Cargo Activity vs Weight Load Factor
Spearman ρ = -0.3286
p < 0.001
```

Within the under-utilized regime, the corresponding relationships were not statistically significant.

Therefore, the results provide **observational evidence of relative cargo prominence during weaker passenger activity**, but do not establish that cargo caused or improved operational resilience.

---

## Key Findings

1. IndiGo's domestic operations exhibit distinct multivariate operational regimes rather than a single stable operating pattern.
2. Two principal components capture **97.31%** of the standardized variance in the six-variable analysis.
3. Three operational regimes were identified using K-means clustering.
4. The under-utilized regime is concentrated primarily around the major disruption period of 2020–2021, with isolated earlier observations.
5. Robust Mahalanobis analysis identified August 2020 and November 2025 as empirical multivariate extremes.
6. Cargo activity becomes relatively more prominent when passenger activity is comparatively weak.
7. The findings support interpreting cargo as a **complementary operational channel**, rather than as a proven causal shock absorber.
8. The study is observational and does not establish causal relationships.

---

## Visualizations

The repository contains key analytical visualizations, including:

* Missing-value assessment
* Covariance/correlation analysis
* PCA scree plot
* PCA component visualization
* PCA biplot
* K-means operational regime plot
* Regime distribution over time
* Passenger–cargo activity analysis
* Robust Mahalanobis analysis

---

## Repository Structure

```text
indigo-passenger-cargo-multivariate-analysis/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── Indigo_Multivariate_Analysis.ipynb
│
├── data/
│   └── README.md
│
├── outputs/
│   ├── figures/
│   └── tables/
│
└── docs/
    ├── methodology.md
    └── results.md
```

---

## Reproducibility

The complete analytical workflow is provided in:

```text
notebooks/Indigo_Multivariate_Analysis.ipynb
```

The notebook contains the data preparation, statistical analysis, PCA, clustering, multivariate extreme detection, passenger–cargo analysis, visualizations, and result generation.

### Dataset Availability

The raw Excel dataset is not included in this repository.

To reproduce the analysis:

1. Obtain the publicly available source dataset from the cited aviation statistics source.
2. Place the Excel file inside the `data/` directory.
3. Rename the file as:

```text
Indigoairlines_data_updated.xlsx
```

4. Run the notebook from beginning to end.

The notebook expects the dataset at:

```text
data/Indigoairlines_data_updated.xlsx
```

---

## Software and Libraries

The analysis was conducted using Python.

### Main Libraries

* Python
* Pandas
* NumPy
* SciPy
* Scikit-learn
* Matplotlib
* OpenPyXL
* Jupyter Notebook

Install the required packages using:

```bash
pip install -r requirements.txt
```

---

## Statistical Techniques

The project applies the following multivariate techniques:

* Multivariate descriptive statistics
* Covariance analysis
* Mardia's multivariate normality assessment
* Principal Component Analysis (PCA)
* K-means clustering
* Silhouette analysis
* Robust Mahalanobis distance
* Spearman rank correlation
* Temporal diagnostic analysis

---

## Limitations

* The analysis is observational and does not establish causal relationships.
* Missing observations are not assumed to be missing completely at random because missingness is concentrated in specific periods.
* Complete-case analysis reduces the available sample for the six-variable multivariate analysis.
* K-means clustering depends on the selected variables, scaling procedure, and number of clusters.
* Mahalanobis-based extreme detection is sensitive to distributional assumptions; therefore, robust estimation was used alongside classical Mahalanobis distance.
* The findings describe observed operational patterns and should not be interpreted as evidence that cargo activity causes resilience.

---

## Academic Integrity and AI Disclosure

This repository contains the original analytical workflow developed for the academic project.

AI-based tools were used for assistance with tasks such as:

* Code debugging and explanation
* Statistical interpretation support
* Writing and editing assistance
* Documentation support

All analytical decisions, data preparation, statistical procedures, interpretation, and final conclusions were reviewed and validated by the author.

The underlying dataset is attributed to its respective public source.

---

## Project Context

**Course:** Multivariate Project
**Domain:** Data Science / Analytics
**Application Area:** Indian Domestic Aviation
**Primary Focus:** Multivariate Statistical Analysis
**Techniques:** PCA, K-means Clustering, Robust Mahalanobis Distance, Spearman Rank Correlation

```
```
