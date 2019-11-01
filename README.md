## KDD_TermProject

### Team Name: The Mean Squares

Team Members:
1. Ravina Gaikawad
2. Kevin Thomas
3. Sahithi Priya Gutta
4. Uma Sai Madhuri Jetty

### Project Domain: Climate Change

### Project Title: Analyzing the impact of skyscrapers on climate change

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
- Modeling Phase
- Evaluation Phase
- Deployment Phase
	
	
### Data Understanding and EDA:
	The dataset has data from four files train.csv, building_meta.csv, weather_[train/test].csv, and sample_submission.csv
	Each file has details regarding the specific topic.
	
	1. train.csv
	building_id - Foreign key for the building metadata.
	meter - The meter id code. Read as {0: electricity, 1: chilledwater, 2: steam, 3: hotwater}. Not every building has all meter types.
	timestamp - When the measurement was taken
	meter_reading - The target variable. Energy consumption in kWh (or equivalent). Note that this is real data with measurement error, which we expect will impose a baseline level of modeling error.
	
	2. building_meta.csv
	site_id - Foreign key for the weather files.
	building_id - Foreign key for training.csv
	primary_use - Indicator of the primary category of activities for the building based on EnergyStar property type definitions
	square_feet - Gross floor area of the building
	year_built - Year building was opened
	floor_count - Number of floors of the building
	
	3. weather_[train/test].csv
	Weather data from a meteorological station as close as possible to the site.
	site_id
	air_temperature - Degrees Celsius
	cloud_coverage - Portion of the sky covered in clouds, in oktas
	dew_temperature - Degrees Celsius
	precip_depth_1_hr - Millimeters
	sea_level_pressure - Millibar/hectopascals
	wind_direction - Compass direction (0-360)
	wind_speed - Meters per second
	
	4. test.csv
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

### Note:
	As per the competition rules we are not allowed to share the dataset or any data. However, all the details regarding the dataset are available at https://www.kaggle.com/c/ashrae-energy-prediction/overview

### References:
- https://www.kaggle.com/c/ashrae-energy-prediction/data
