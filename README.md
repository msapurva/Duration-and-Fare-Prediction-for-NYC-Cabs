# About Project : Resurgence of NYC Yellow Cabs

- This Project is for course IST 718: Big Data Analytics @ Syracuse University
- Professor: Daniel Acuna <deacuna@syr.edu>

## Objective and Focus:

- Due to advent of smart cab companies such as Uber and Lyft, people are preferring smart services over the traditional taxis in NYC. The research throws light on the following important issues to be the reason in dip in the usage of Yellow taxis
#### Information Unavailability:
- The yellow taxi drivers do not get real-time updates on availability of
passengers. The drivers spend majority of their time searching for customers
#### Fare negotiation:
- Availability of smartphone apps for Uber and Lyft helps passengers to be informed about the ride prices
- The yellow cab drivers spend time in making a proposal and waiting to make a
deal post the effort of finding a customer


## Focus: 
-  Whether the ride will be profitable for the driver?
-  Does weather and holidays really affect the profitability of driver? 
#### Why these questions:
-  Uber/Lyft Drivers and smart apps have destroyed the remarkable icon cabs
-  Stringent Interviews and Background Checks to achieve driving permits for above mentioned smart cabs. Not everyone gets to become their drivers.
-  Hence, adverse effect on employment rate and crime rate


## Requirements:
- Python 3.7.0.
- Pandas
- Numpy
- Pyspark 2.4.0
- Spark 2.4.0
- xgboost 
- sklearn
- matplotlib.pyplot
- seaborn
- RandomForestRegressor
- GBTRegressor
- RegressionEvaluator
- VectorAssembler
- ascii_letters
- datetime
- StandardScaler
- MinMaxScaler
- Vector

## Installation: 
pip install pyspark

Project Code : In addition to the requirements, we need to Change these lines to read files locally :


## Data Description:

-  Full Merged Dataset : NYC Yellow Taxi Trip Records + USA Federal Holidays Dataset + NYC Weather Data
-  Number of data points : 12 M
-  Training data points out of Sample Dataset: 600 K
-  Total Features: After cleaning, the total features are 61
-  Cleanliness: Merging, Date time conversion, Imputation, Dummy variables, Standardization
-  Label/output to predict: Duration and Total Amount


## Findings

- The average duration of a trip is about 15-18 minutes • The average total amount is between $10-$19
- The average fare price is highest for the month of October
- Longest rides occur at 3:00 PM in the evenings and at 6:00 AM in the morning, the distance of the rides is the shortest
- Overall, our models for predicting taxi pickups’ total amount and duration in New York city performed well
- The gradient boosting regression model closely followed by the random forest model performed the best
- This was likely due to their unique ability to capture complex feature dependencies
- The rmse for gradient boosting regression model was achieved to be ~$3.71178 for amount and ~87.3163 sec for total duration
- Our results and error analysis for the most part supported our intuitions for the usefulness of features with the exception of holiday feature which was not found important for model performance
- Our model can be used by city planners and yellow taxi drivers in determining where to position yellow taxi cabs and understanding patterns in ridership
- In our future work we plan to implement two models: neural network regression for its capability to automatically tune and model feature interactions Although we used k-means clustering, we aim to achieve better results in the future



# ProjectCode
Project Code 

Change these lines :

```py
fulldata = pd.read_csv("/Users//IST718 Dropbox/IST 718 Project/Taxi Data/2015-01_100k.csv")
weatherdata = pd.read_excel("/Users//IST718 Dropbox/IST 718 Project/Weather Data/2015_weather.xlsx")
holidaysdata = pd.read_excel("/Users//IST718 Dropbox/IST 718 Project/Holiday Data/holidays.xlsx")
```

into these lines :

```py
fulldata = pd.read_csv(os.environ.get("TAXI_DATA"))
weatherdata = pd.read_excel(os.environ.get("WEATHER_DATA"))
holidaysdata = pd.read_excel(os.environ.get("HOLIDAY_DATA"))

### Setup the environment variables for Data Path

Append these lines into this file `~/.bash_profile` 
CAUTION: Do not overwrite bash profile, just add these lines to it !

The contents of this file should look like this :

```bash
export TAXI_DATA="/Users//IST718 Dropbox/IST 718 Project/Taxi Data/2015-01_100k.csv"
export WEATHER_DATA="/Users//IST718 Dropbox/IST 718 Project/Weather Data/2015_weather.xlsx"
export HOLIDAY_DATA="/Users//IST718 Dropbox/IST 718 Project/Holiday Data/holidays.xlsx"
```

### How to launch the anaconda navigator

From a new command line terminal, run anaconda-navigator everytime.

```console
$ anaconda-navigator
```

### Instructions for Github

Please push changes ONLY to your respective notebooks to avoid github conflicts in ipynb files



### How to compare two notebooks

install xcode-select like this:

```console
$ xcode-select --install
```

and then, install [nbdiff](https://github.com/jupyter/nbdime#installation) 

and then, run like following from command line :


```diff
MacBook-Pro:ProjectCode apsharma$ nbdiff IST\ 718_Apurva.ipynb IST\ 718_Shivanshi.ipynb 
nbdiff IST 718_Apurva.ipynb IST 718_Shivanshi.ipynb

--- IST 718_Apurva.ipynb  2018-10-28 10:16:25.199350
+++ IST 718_Shivanshi.ipynb  2018-10-28 10:21:35.103231
## deleted /cells/2:
-  code cell:
-    execution_count: 7
-    metadata (known keys):
-      collapsed: True
-    source:
-      #import pandas as pd
-      #fulldata=pd.read_csv("C:/Users/SHIVANSHI/IST718 Dropbox/IST 718 Project/Taxi Data/2015-01_100k.csv")
-      #weatherdata = pd.read_excel("C:/Users/SHIVANSHI/IST718 Dropbox/IST 718 Project/Weather Data/2015_weather.xlsx")
-      #holidaysdata = pd.read_excel("C:/Users/SHIVANSHI/IST718 Dropbox/IST 718 Project/Holiday Data/holidays.xlsx")

## modified /cells/3/source:
@@ -1,4 +1,4 @@
 #import pandas as pd
-#fulldata=pd.read_csv("C:/Users/SHAMA/IST718 Dropbox/IST 718 Project/Taxi Data/2015-01_100k.csv")
-#weatherdata = pd.read_excel("C:/Users/SHAMA/IST718 Dropbox/IST 718 Project/Weather Data/2015_weather.xlsx")
-#holidaysdata = pd.read_excel("C:/Users/SHAMA/IST718 Dropbox/IST 718 Project/Holiday Data/holidays.xlsx")
+#fulldata=pd.read_csv("C:/Users//IST718 Dropbox/IST 718 Project/Taxi Data/2015-01_100k.csv")
+#weatherdata = pd.read_excel("C:/Users//IST718 Dropbox/IST 718 Project/Weather Data/2015_weather.xlsx")
+#holidaysdata = pd.read_excel("C:/Users//IST718 Dropbox/IST 718 Project/Holiday Data/holidays.xlsx")
```

and to view these changes in browser instead , run like following :
```
$ nbdiff-web IST\ 718_Apurva.ipynb IST\ 718_Shivanshi.ipynb 
```

For more on nbdiff and merging conflicts in ipython notebooks, refer:  [nbdiff documentation](https://nbdime.readthedocs.io/en/latest/cli.html)
