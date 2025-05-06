# Missing Data Imputation and Outlier Detection
This repository showcases a comprehensive and end-to-end workflow designed for managing missing values and pinpointing potential error records within a clinical dataset. The entire process is implemented using the R programming language, leveraging the scripts that are provided as part of the course materials.

In terms of techniques, it encompasses MCAR (Missing Completely at Random) testing to assess the nature of missingness in the dataset. Additionally, multiple imputation is carried out with the MICE (Multivariate Imputation by Chained Equations) package, which helps in filling in the missing values in a statistically sound manner. For identifying outliers, two distinct methods are employed: the Local Outlier Factor (LOF) algorithm and z-score diagnostics, both of which effectively flag data points that deviate significantly from the norm.

The dataset utilized for this workflow is sourced from the course materials, specifically from Module 1. The source code implementing this entire data cleaning and analysis pipeline can be found in the "./DataCleaning/" directory. All the resulting outputs, including various graphs and visualizations, are stored in the "./Outputs/graphs/" directory.  
# Working flows
Data Import and Cleaning​
Import the Excel - formatted dataset using the read_excel() function. Remove redundant variables with more than 40% missing values. Filter the dataset to retain only variables with a missing data ratio of less than or equal to 40%, ensuring the validity and integrity of the data.​
Missing Data Handling​
Visualization Analysis​
Visualize the patterns of missing data among variables with the help of the ggmissingo and VIM packages. Create stacked bar charts and matrix plots to intuitively examine the distribution and characteristics of missing values, thereby gaining a comprehensive understanding of the overall situation of data missing.​
Missing Mechanism Testing​
Use the mcar_test() function in the Amelia package to evaluate whether the data missing mechanism is Missing Completely at Random (MCAR). The test reveals that the data does not meet the MCAR condition, suggesting that the missing data is more likely to be Missing at Random (MAR) or Missing Not at Random (MNAR).​
Multiple Imputation​
Carry out data imputation using the miceadds package: For data with complex linear relationships, select the "2l.pan" method; to maintain the characteristics of the original data distribution, use the "norm" method. After performing the imputation, generate imputed datasets under different methods and compare the imputation results. Visualize the distribution of the original data and the imputed data. The results show that the "norm" method performs better in preserving the original data distribution. Although its effect is similar to that of the "2l.pan" method, considering its good ability to maintain the data distribution, the "norm" method is finally selected as the preferred data imputation method.​
Outlier Detection​
Local Outlier Factor (LOF)​
Use the lof() function in the DMwR package to detect multivariate outliers in the dataset. Visualize data points with high LOF scores by creating histograms and box plots to identify potential outliers.​
Z - Score Method​
Calculate the Z - score for each numeric variable. Mark data points with a Z - score greater than 3 as extreme values, assuming these extreme values may be outliers or data entry errors.​
Suspicious Error Reporting​
Extract records with high LOF scores for in - depth inspection; mark extreme values with a Z - score greater than 3; export suspected outliers to a CSV file for manual review to determine whether these data are actual outliers or data entry errors. Future plans involve exploring more efficient screening methods to accurately identify suspicious records that require further verification.
# Insights
1. Random Forest (RF) outperforms k - Nearest Neighbors (kNN) in predicting categorical variables. Ensemble learning methods combined with feature importance analysis offer a reliable approach for variable selection. Domain - specific knowledge is crucial to distinguish between relevant features and noise.
2. Neural network architectures like LSTM retain temporal dependencies more effectively than traditional RNNs. The combination of clustering algorithms and dimensionality reduction techniques creates a powerful framework for data segmentation. Expert judgment is indispensable to separate valid patterns from spurious correlations.
3. GLMnet provides more stable coefficient estimates than ordinary least squares in high - dimensional data. The integration of anomaly detection algorithms and data profiling tools forms a comprehensive strategy for data quality assessment. A thorough cross - validation process is vital to differentiate between reliable models and overfitted ones. 
