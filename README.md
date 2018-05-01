# TimeSeriesProject-
- Forecase Oakland Temperatures by creating a Time-Series Autoregression Model using historic Oakland temperature averages
# Getting Started
Anaconda and Python3 installation

- [Anaconda_Python3_Mac_OS_X](https://www.anaconda.com/download/#macos)

- [Anaconda_Python3_Microsoft_Windows](https://www.anaconda.com/download/#macos)

- [Anaconda_Python3_Linux](https://www.anaconda.com/download/#macos)

Jupyter Notebook installation

- Access command line by opening Terminal

- type `<pip install jupyter>`

- Confirm installation of Jupyter Notebook 

- type `<jupyter notebook>`

# Access the Data

- [Obtain Weather History](https://www.wunderground.com/history/airport/KOAK/2013/12/5/CustomHistory.html?&reqdb.zip=&reqdb.magic=&reqdb.wmo=)

# Abstract

I wanted my commensurate project to be a tangible solution to a problem I am currently experiencing. One of my passions in life is horticulture. Specifically, succulents!! I have a massive collection and propogate on the side. The success of propogation depends heavily on temperature and percipation. With this insight, I decided to create a model that would predict the temperature so I would know what day and time period would be the most ideal for successful propogation. 

# Exploratory Data Analysis

I collected historical temperature averages from [Weather Underground](https://www.wunderground.com/history/airport/KOAK/2013/12/5/CustomHistory.html?&reqdb.zip=&reqdb.magic=&reqdb.wmo=). This is an affliate of The Weather Channel. Their historical data provides temperature averages for all airport temperature sensors within the United States. I collected temperature averages for the past five years 2013-2017.

An issue I encountered when looking over my data is the leap day we observe every four years. This creates a year with an additional day with its own set of data. I could either input variables for the missing three days within the three years that did not have a leap year, or remove the two variables for the two years that did have a leap day. The mean temperature would be used if I had chosen to insert dummy variables. I ran my model with dummy variables and then ran my model excluding the two leap year variables. The result did not alter my MSE(MeanSquaredError) at all. With this knowledge, I continued my analysis exluding the two leap year variables. This would make my dataset clean with each time-series year having 365 days or values. 

# Visualizing the Data

First, I plotted the temperature averages on a linear line plot. X axis is Time and Y axis being Temperature.

# Autocorrelation

In a time-series model utilizing Autoregression, Autocorrelation is key to a successful prediction with the lowest MSE(MeanSquaredError).
Autocorrelation assumes an observation value at a previous time-step is useful in predicting the observation value at the next time step. This relationship is called autocorrelation. Once the time-series data is determined to be autocorrelated, the dataset is considered stationary and ready for further analysis. 

My model uses Visualization and Plotting, the Pearson Correlation Coefficient, and Lag Variable visualization to determine autocorrelation within my dataset. 

# Persistence Model

Persistence modeling splits the data into two sets. Once set is for training the model and the other is for testing. I split the data into a training set and left the last seven days for the testing data. The model trained on 1,818 observation value. This is 4 years and 358 days. The last seven days of the five year time-series data is what my model used to test or prediction. The prediction is then compared against the acutal observation value of my dataset. 

My presistence model had a MSE of 4 (RMSE of 2).

This model is stationary and ready for prediction. 

# Autoregression and Prediciton

I take the same model and train the model to use its learned coefficients to make predicitons. The model take the last 29 observation values and use those values in its regression to make predictions. The coefficients include the intercept and lag variable from t-1 to 
t-n. 

My Autoregression model had a MSE of 4.6 (RMSE of 2.2)

The forecast looks to be nice a warm, consistenct with previous temperatures in historical time-steps. 

# Model Evaluation

Traditional train test split cannot be used on time-series forecasting. If a model knows the exact observation value and its exact timestamp, then every prediction would be 100% accurate. The model assumes their is no relationship between each observation value. But in time-series we must respect time and the order in which each oberservation value is observed. 

One way is to evaluate your model is to create multiple train-test splits - these can be 60/40 - 50/50 - 40/60 - 70/30 or whichever ratio you would like the model to be evaluated on. These train-test splits are then graphed on a linear time line (X) and then compared with the actual observation value. 

When visualizing the train-test predictions the plot should resemble the visualization of the original observation data. Any outliers or high error prediction can be identified by visually observing its deviance from the original dataset visualization. 

Walk Forward Validation is also another technique. This is a technique I did not try, but recommend if anyone wants to replicate this model for their own predictions. Walk Forward Validation trains a model to be updated everytime new data is available. Conceptually, time is continuous and new data is inevitable because of the temporal order of time within itself. 

# Conclusion 

I had so much fun creating a predictive model for Oakland temperatures. To make this model dynamic, it can include other features such as humidity and percipatation. This would make it a complete forecast!

Additionally, this model is ubiquitous an is utilized by many forecasters because of its low margin for error and the consistency in the pattern of historic temperatures. 

One variable that is concerning but exciting at the same time is allocating for climate change. Climate change causes variables to deviate wildly from its historical obeservation value. I find great interest in developing a model that can allocate for such a swing in variable that is inconsistent with temporal time. 

This model can be utilzed for any predictive forecast that observes its values over time and has a continous variable. 

# Special Consideration

I'd like to thank George McIntire a Data Science instructor at General Assembly for his expertise regarding time-series, autoregression, and cross validation/ train-test split. 

Additionally, I'd like to thank the many resources online within the Data Science community for providing documentation and knowledge regarding time-series autoregression prediction. 

Without these resources I would have had a challenging time creating such an accurate model. 

# Final Word 

"Hiding within those mounds of data is knowledge that could change the life of a patient, or change the world." ~ Atul Butte, Stanford

