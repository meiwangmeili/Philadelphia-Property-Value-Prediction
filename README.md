# AlphaEngineer_JC_DS_FT_BSD_JKT_15_FinalProject
## Philadelphia Property Value Prediction
### By: Billy Witanto, Muhammad Rivaldi Prabowo, Vinsensia Fresian Meiliana

<p align='justify' style="font-weight: bold;">
These notebooks serve as the final project of Job Connector-Data Science and Machine Learning program at Purwadhika Start-up and Coding School.
</p>

<p align="center">
<img src="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/Pictures/ReadMe%20Header.jpg">
</p>

## Background
<p align='justify' style="font-weight: bold;">
Philadelphia city is one of the hottest real estate market in the US. With high increment every year, its property price is suprisingly lower compared to other cities in the US. That said, with lowered home demand index in 2022 compared to 2021, this is the best time for property agent to actively promote its remaining properties listed. In this project, we will aid the promotion by providing predicted market value of properties obtained by machine learning model. Hopefully, it will reduce the cost of property appraisal. And also, with a justified market value based on property characteristics and location, both buyer and seller will be benefitted, thus hypothetically will lead to increase in success transaction of properties.
</p>

## Dataset Source
<p align='justify' style="font-weight: bold;">
This is a real-world data of properties in Philadelphia city. You can download it from <a href="https://www.kaggle.com/datasets/adebayo/philadelphia-buildings-database">Kaggle</a> or <a href="https://www.kaggle.com/datasets/adebayo/philadelphia-buildings-database">City of Philadelphia: Metadata Catalog</a>.
</p>

## Methodology
### Data Understanding
<p align='justify' style="font-weight: bold;">
With such an enormous dataset with a lot of columns and rows, we first need to know what information the dataset has. From a thorough investigation, we summarize them in <a href="https://docs.google.com/spreadsheets/d/1WapgNftGZMUBt6H2SkDbNedN6vAwY56xvdr9P1My-30/edit#gid=781668512">Spreadsheet</a>. 
</p>

### Data Cleaning
<p align='justify' style="font-weight: bold;">
First, we pick columns which informative enough to help us fill the missing value and anomalies in the dataset based on its description. Thus, reducing the columns. Then, initial exploratory data analysis (EDA) was performed to match the column description with the data, also to detect and correcting missing values and anomalies. Furthermore, after correcting missing values, this section resulting in clean dataset, free from missing values. <a href="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/1.%20Background%20and%20Data%20Cleaning.ipynb">Jupyter</a>
</p>

### Detailed EDA
<p align='justify' style="font-weight: bold;">
Detailed EDA to further understand the characteristics and correlations of the features and label to determine the proper preprocessing of the data. This section will also help us in gaining insights about feature engineering. <a href="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/2.%20Detailed%20EDA.ipynb">Jupyter</a>
<a href="https://public.tableau.com/views/FinalProjectPurwadhika/MarketValuebyYear?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link">Tableau Vizualization</a>
</p>

### Feature Selection
<p align='justify' style="font-weight: bold;">
We select the features that will be used in the model building based on evidence in detailed EDA and also on the basis of domain knowledge. 
</p>

### Modeling
<p align='justify' style="font-weight: bold;">
In building process, we use linear regression, random forest regression and xgboost regression as potential models. First, we made a base model without any feature engineering, with only handling contextual outliers. In the second improved model, we include feature engineering. In each model, we select the best model based on MAPE (mean absolute percentage error) and also considering its standard deviation. After that, we will use the best model to predict the test data. Then, comparing the predicted value with the actual value of property to evaluate our prediction model. The model will be improved as necessary.
</p>

## Results

### Base Model
<a href="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/3.%20Supervised%20Modelling-Regression%20(1).ipynb">Jupyter</a>

#### Model Selection with Cross-Validation
<p align="center">
<img src="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/Pictures/Crossvalidation%20Base%20Model.png">
</p>
<p align='justify' style="font-weight: bold;">
From the result above, it is not suprising for linear regression to have MAPE around 85% since the outliers in the data really exists. With slightly lower standard deviation than linear regression, XGBoost regression have MAPE around 34% which is still not good enough. <a href="https://onlinelibrary.wiley.com/doi/pdf/10.1002/9781119199885.app1">Reference</a> Random forest regressor proved to be the best model with good MAPE (14.475%) and the lowest standard deviation (0.00447) compared to two other models. Thus, we will use random forest model to predict the test data.
</p>
  
#### Predicting Test Data
<p align="center">
<img src="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/Pictures/Base%20Model%20Test%20Evaluation.png">
</p>
<p align='justify' style="font-weight: bold;">
From the result above, the model was able to predict the test data nicely with MAPE of 13.18%. MAPE below 10% indicating an excellent accuracy of the prediction model, while 10-20% indicating a good accuracy. <a href="https://onlinelibrary.wiley.com/doi/pdf/10.1002/9781119199885.app1">Reference</a> Can we improve the model?
</p>

### Model Improvement with Feature Engineering
<a href="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/4.%20Supervised%20Modelling-Regression%20(2).ipynb">Jupyter</a>


#### Model Selection with Cross-Validation
<p align="center">
<img src="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/Pictures/Crossvalidation%20Model%202.png">
</p>
<p align='justify' style="font-weight: bold;">
After adding and removing certain features, the MAPE of random forest regressor is increased by little, but still comparable to the model before (14.58%).
</p>

#### Predicting Test Data
<p align="center">
<img src="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/Pictures/Model%202%20Test%20Evaluation.png">
</p>
<p align='justify' style="font-weight: bold;">
From the result above, based on the MAPE value, the feature engineering didn't improve the model (13.35%). However, it's important to note that in this step, we dropped building code description with more than 400 unique values (that probably explain why the previous model better than this one). But since the difference is only 0.17%, we can say that there's no change in the quality of the model. However, it is also important to note that the goodness of fit of this model is better than the previous model, it is more representable to the test data. Also, there is a reduction in MSE that probably because improvement in the features used reducing the effect of outliers.
</p>

## Limitations and Suggestions
<p align='justify' style="font-weight: bold;">
1. Since the data are enormous, the process of random forest regression was taking too much time. When trying to improve the model with hyperparameter tuning, our computational power are not enough. Our suggestion for this problem is whether to explore other unconvential model that may work faster with comparable performance with random forest or use device with more computational power.
</p>
<p align="center">
<img src="https://github.com/meiwangmeili/Philadelphia-Property-Value-Prediction/blob/main/Pictures/Random%20Forest.JPG">
</p>
<p align='justify' style="font-weight: bold;">
2. Our model can only predict market values of properties in range of 6800-1.4799*1e8, with range of numerical values: a.) Total livable area: 0 - 798189; b.) Total area: 600 - 99964; c.) Number stories: 0 - 40; d.) Number rooms: 0 - 154; e.) Number bedrooms: 0 - 93; f.) Number bathrooms: 0 - 84; g.) Year built: 1652 - 2020; h.) Sale year: 1918 - 2020.  
</p>

## Conclusion
<p align='justify' style="font-weight: bold;">
From the model performance, we conclude that the property agent can use this model to predict the market value of properties in Philadelphia based on their characteristics and location. Even though that this model can't determine the sentimental/historical value of a property, we hope that this model can objectively and closely match the market value made by a professional property appraiser, thus reducing the cost of property appraisal. By using this model, we also hope that the justified market value can improve the success in property transaction between saler and buyer. 
</p>

