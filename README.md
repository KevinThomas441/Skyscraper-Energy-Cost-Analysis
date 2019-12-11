<h1 align = "center"> Analyzing the Impact of Skyscrapers on Climate Change </h1>

![Charlotte Skyline](https://v1019.com/wp-content/uploads/sites/51/2018/01/Charlotte-Skyline.jpg)

### Team Name: The Mean Squares

Team Members:
1. Ravina Gaikawad
2. Kevin Thomas
3. Sahithi Priya Gutta
4. Uma Sai Madhuri Jetty

### Project Domain: Climate Change

### Project Description: 
- The project focuses on analyzing  the effect of infrastructure modifications from tall building units/skyscrapers on climate change.
- The project includes a study of the energy usage  by the building. Counterfactual models are required to measure the energy consumption done depending on four energy types. The consumption is based on historic usage rates and observed weather.
- It can be then predicted how far will it affect and result in climate change in later years. A goal is to develop a predictive model  for climage change based on energy consumption from skyscrapers.
-The project has a data of over one thousand building's hourly meter reading for three years.
	
### CRISP-DM Process:
We have undergone these steps as a part of CRISP-DM:
- Research Understanding Phase: Buildings and construction account for more than one-third of global energy consumption. They are also responsible for 40% of the world's total CO2 emissions. These numbers continue to rise, as developing countries begin to access previously untapped energy sources. Additionally, as countries start enjoying economic stability, the average size of buildings also increases consequently increasing the overall energy demand.
<br> To counter this disturbing trend, nations and companies are investing in energy and cost-efficient technologies to better manage the energy needs of the building. However, the impact of these measures has not been accurately estimated. Existing models do not consider data such as the type of meter or assume that all buildings are of the same type. Therefore, we propose a solution that includes these features and models the energy usage of building before and after implementing improvements.
- Data Understanding Phase
- Data Preparation Phase
- Data Exploration
- Modeling Phase
- Evaluation Phase	
	
### Data Understanding and EDA:
The dataset has data from four files train.csv, building_meta.csv, weather_[train/test].csv, and sample_submission.csv
Each file has details regarding the specific topic.


#### 1. train.csv

building_id - Foreign key for the building metadata.
meter - The meter id code. Read as {0: electricity, 1: chilledwater, 2: steam, 3: hotwater}. Not every building has all meter types.
timestamp - When the measurement was taken
meter_reading - The target variable. Energy consumption in kWh (or equivalent). Note that this is real data with measurement error, which we expect will impose a baseline level of modeling error.


#### 2. building_meta.csv

site_id - Foreign key for the weather files.
building_id - Foreign key for training.csv
primary_use - Indicator of the primary category of activities for the building based on EnergyStar property type definitions
square_feet - Gross floor area of the building
year_built - Year building was opened
floor_count - Number of floors of the building
	
	
#### 3. weather_[train/test].csv

Weather data from a meteorological station as close as possible to the site.
site_id
air_temperature - Degrees Celsius
cloud_coverage - Portion of the sky covered in clouds, in oktas
dew_temperature - Degrees Celsius
precip_depth_1_hr - Millimeters
sea_level_pressure - Millibar/hectopascals
wind_direction - Compass direction (0-360)
wind_speed - Meters per second
	
	
#### 4. test.csv

The submission files use row numbers for ID codes in order to save space on the file uploads. test.csv has no feature data; it exists so you can get your predictions into the correct order.
row_id - Row id for your submission file
building_id - Building id code
meter - The meter id code
timestamp - Timestamps for the test data period
	
	
### Generally EDA approach is useful for:
- Delving into data
- Examining important interrelationships between attributes
- Identifying interesting subsets of the observations
- Develop an initial idea of possible associations amongst the predictors, as well as between the predictors and the target variable.

### Exploring Discrimination and Bias in data
There are no features related to people or location. Though the site_id is given we can't calculate the location from the given information. From our perspective we do not see any discrimination or bias in our data.

### Data Preparation:
- Due to compute restrictions we had to cut the size of dataset from ~ 20 million to ~ 10 million. We did this by dropping the random selection of 10 million rows so as to avoid the bias.
- We scaled the data to normalize the relations between dependent and independent variables.
- We encoded categorical variables using one-hot encoding and label-encoding.
- Due to the large amount of missing values in the "year_built", "floor_count", "builiding_age" columns in the building metadata table, we dropped the columns.
- Dropped columns like "building_id", "site_id" which are not necessary.
- Instead of having the whole time stamp we just selected the hour value and stored. 

### Modeling:
In our research we found that decision tree is the best algorithm for this problem. Additionaly, since our data set is large we needed an algorithm that dealt with large amounts of data easily. So, we turned to "LightGBM".

#### About Light GBM
- Light GBM is a gradient boosting framework that uses tree based learning algorithm.
- Light GBM is prefixed as ‘Light’ because of its high speed. It can handle the large size of data and takes lower memory to run. Also, the algorithm focuses on accuracy of results and GPU learning.

### Evaluation:
Since our problem is a regression problem we decided to use Root Mean Square Error for model Evaluation. Evaluation is done based on RMSE score. We acheived an RMSE score of 74. 

### Conclusion:
Our model can be used to improve the energy efficiency of the buildings which can be used by Government bodies, contractors and Environmental watch dog organizations. Our model needs more improvements, but it is a good starting ponit.

### Future Work:
- Create four seperate models to predict each meters readings.
- Experiment with fastai and Neural Networks.
- Tune hyper parameters to imrove RMSE score.

### Instructions:
- This project is based on python 3.7
- This file requires Jupyter Notebooks or google colab to be run.
- Need to install numpy, pandas, sklearn, matplotlin, seaborn, LightGBM, tqdm.

### Note:
As per the competition rules we are not allowed to share the dataset or any data. However, all the details regarding the dataset are available [here](https://www.kaggle.com/c/ashrae-energy-prediction/overview)

### References:
- https://www.kaggle.com/c/ashrae-energy-prediction/data
- https://medium.com/@pushkarmandot/https-medium-com-pushkarmandot-what-is-lightgbm-how-to-implement-it-how-to-fine-tune-the-parameters-60347819b7fc
