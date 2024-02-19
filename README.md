### Flow Prediction for Wastewater Treatment Plants

Ryan Fisher

#### Executive summary

#### Rationale
The flow into wastewater treatment plants is influenced by precipitation and groundwater that infiltrates into the wastewater collections systems. This is a particular for old againg infrasture in wet areas such as the Northeast United States. The spike in flows to a treatment plant require the operations staff to adjust treatment operations, place additional treat basins in service and call up addition operations staff to react to the sudden increase in flows. The high flows caused by precipitation events can cause overflows, bypass of treatment or damage to equipment. 

The increase in flows is typically unknown to the operators and they rely on their intuition to estimate the increase in flows due to forecasted weather events. The intent of the project is to develop a machine learning model to help predict the flow to the treatment plant based on forecasted precipitation events. 

#### Research Question
Can a machine learning model be utilized to predict the flows at a wastewater treatment given the current known conditions and the available forecast storm precipitation event? 

#### Data Sources
Three sources are data will be utilized to build a training and test set for the model.
1. Flow data and precipiation data collection from a treatment in Rockland County, New York will be utilized. The data include the daily average influent flow to the treatment plant and the daily precipitation received. 
2. Data collected from the nearest National Weather Service monitoring station. The information from the station include precipitation and temperature will be utilized in the model.
3. River flow data from a U.S. Geologic stream gauging station. The flow data will be utilized in the model to infer groundwater and the potential on water infiltration into the wastewater collection system. 

#### Methodology
The machine learning model has been setup to allow the treatment plant operator to use current available information to make a prediction of the flows to the treatment plant tomorrow.
The data from the three different source was cleaned and combined into one dataset. Feature engineering was used to develope the features(inputs) that a treatment plant operator would have avialable to enter to make their prediction. 
A regression model was trained on the data and scored based performation with a set of testing data.

The features used as input to the model include:
Forecast Temperature 
Forecast Precipitation
Todays temperature
Todays precipitation
Todays wwtp flow
Todays river flow
Yesterdays temperature
Yesterdays precipitation
Yesterdays wwtp flow
Yesterdays river flow

The target data to predict in the model is the forecast wwtp flows for tomorrow. 

The following SciKitLearn regression models were utilized:
- Linear Regression
- Polynomial Regression
- Ridge Regression
- Lasso Regression


#### Results
Models were evaulated on Mean Absolute Error (MAE) to avoid overfitting on the few peak flows that are far from the average.
The results of the models used are shown in the table below.
- The Ridge regression model had the best reuslts.
- The most important features were found to be:
  -wwtp flow yesterday
  -wwtp flow today
  -precipitation rain today
  -river flow today
  -precipitation rain forecast
  -temperature minimum yeasterday


#### Next steps
The precipitation data was found be the most significant feature in the flow prediction as anticipated. There is a known lag from the receiveing preciptation to the increase in flows at the treatment plant. However, the precipation data is a daily value only and precipiation received in the morning would have more of an influence on the daily treatment plant flow than precipitation recieved in the evening that would not result in treatment plant flow increase until the start of the next day. Therefore, it would be advantages to obtain precipration data on an hourly basis instead of a daily basis to potentially improve the prediction model. 


#### Outline of project

- [Link to notebook 1]()
- [Link to notebook 2]()
- [Link to notebook 3]()


##### Contact and Further Information
Ryan Fisher at r.fisher.pe@gmail.com
