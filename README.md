Wheat Experiment Yields and Nitrogen Uptake Exploration

Introduction
This is code written in Python to look at wheat crop yields under different types and levels of fertilisation treatments to try and predict which Nitrogen treatment was applied based off of grain yield and percentage of Nitrogen found in the harvested grain.
I used this dataset as my PhD is investigating wheat plants, looking at their root exudates to see if changing their composition can reduce the rate of soil erosion. This dataset is looking at wheat yield when fertilizer composition is modified, so whilst the two things aren’t directly related, I’m still interested to learn about the different relationships wheat plants can have with the soil.
This code will find out the maximum and minimum grain yields seen, to give an initial idea of which nitrogen fertilizer treatments (n_factor_level) are best and worst for growing wheat before moving onto a K Nearest Neighbours Analysis, which takes the k nearest (15 for this code) data points to a point x and then labels x based on whichever label was found most frequently within the k neighbours. This code can be used in future to predict what nitrogen fertilizer treatment a crop of wheat was given based on the percentage of Nitrogen found in the grain and the yield of the grain.

Methods
To run, download the python script in this repository along with the dataset the code uses into the same directory. To understand the n_factor_level codes, also download n_factor_data to understand what all of the treatments entail. These datasets were obtained from the Rothamsted Long-term experiment titled ‘Broadbalk Wheat Experiment yields and N uptake Section 1, 2001-2015’ (Rothamsted Research, 2022).
Import the following libraries for use with the code (also shown in the code at required locations):

1.	pandas as pd
2.	seaborn as sns
3.	matplotlib.pyplot as pt
4.	numpy as np

From the pandas library, import: 
1.	scatter_matrix
2.	DataFrame

From the sklearn library, import: 
1.	train_test_split
2.	GridSearchCV
3.	KNeighborsClassifier

Firstly, the data is loaded in and tidied up to remove columns that are not wanted for the analysis. They were removed as they contained a lot of NaNs which make it difficult to represent relationships clearly. Next, the data was explored to find the maximum and minimum grain yield amounts from the experiment. 
Having determined which conditions caused the highest and lowest grain yields, the code moves on to prepare for a K-Nearest Neighbours (KNN) analysis. n_factor_level, which indicates the level of nitrogen applied to the crop, was used to create a new column for crop_data, with the data type float for use later on during the KNN analysis. The relationships in the data were explored in a heatmap and a multivariate scatter matrix. The least correlated variables with the best distribution were identified by eye to take forward for the KNN analysis. A blown up plot was created for the selected variables of grain_%_n against grain_yield and these variables were taken forward for KNN.

Next, the crop data was split into subsets so that one subset could be tested against the other to test the model fit. The number of neighbours to be used was also optimised before being used to create the model which was then plotted and scored.

Results & Conclusions
The worst fertilizer treatment for grain yield was nill, which is what was expected as no extra nutrients would be supplied to the plant. The best n_factor_level was N1+N3+N1, which was the second highest amount of Nitrogen added to crops in the experiment.

The heatmap shows that grain_%_n and grain_yield are two of the variables with the lowest correlation. Then the scatterplot plots those two variables and shows how within this relationship different fertiliser treatment groups produce grains with quite different nitrogen contents and yields compared to other fertiliser treatment groups.

The model created using KNN was plotted and given a score of 0.46 (to 2 dp) out of 1. This means we can predict what nitrogen fertilizer amount was used given the grain yield and harvested grain percentage nitrogen with 46% accuracy. This is not the most accurate prediction, but this model could be used as a primary method to predict what fertilizer has been used on a crop of wheat.

Reference
Rothamsted Research (2022). Dataset: Broadbalk Wheat Experiment yields and N uptake Section 1, 2001-2015 Electronic Rothamsted Archive, Rothamsted Research https://doi.org/10.23637/rbk1-yldS10115-01

