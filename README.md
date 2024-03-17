### Flow Prediction for Wastewater Treatment Plants

Ryan Fisher

#### Executive summary
The flow into wastewater treatment plants can be predicted by utilizing a linear regression machine learning model. Various models were investigated for this application using data from a treatment plant in New York State. The Ridge Regression Model was determined to provide the best predicition of flow. 

#### Rationale
The flow into wastewater treatment plants is influenced by precipitation and groundwater that infiltrates into the wastewater collections system piping. This is a particular for old aging infrasture in wet areas such as the Northeast United States. The spike in flows to a treatment plant require the operations staff to adjust treatment operations, place additional treat basins in service and call up addition operations staff to react to the sudden increase in flows. The high flows caused by precipitation events can cause overflows, bypass of treatment or damage to equipment. 

The increase in flows is typically unknown to the operators and they rely on their intuition to estimate the increase in flows due to forecasted weather events. The intent of the project is to develop a machine learning model to help predict the flow to the treatment plant based on forecasted precipitation events. 


#### Research Question
Can a machine learning model be utilized to predict the flows at a wastewater treatment given the current known conditions and the available forecast storm precipitation event? 

#### Data Sources
Three sources are data will be utilized to build a training and test set for the model.
1. Flow data data collected from a treatment in Rockland County, New York was utilized. The data included the daily average influent flow to the treatment plant.
2. Data collected from the nearby New York State Mesonet weather station. The information from the station include hourly precipitation.
3. River flow data from a U.S. Geologic stream gauging station. The flow data was utilized in the model to infer groundwater and the potential on water infiltration into the wastewater collection system. 

#### Methodology
The data from the three different source was cleaned and combined into one dataset. Feature engineering was used to develope the features(inputs) that a treatment plant operator would have avialable to enter to make their prediction. 
A regression model was trained on the data and scored based performation with a set of testing data.

The features used as input to the model include:
- Forecast Precipitation
- Current and hsitoric precipitation
- Current and historic treatment plant flow
- Current and historic river flow

The target data to predict in the model is the forecast wwtp flows for the following day. 
  Model	      Train MAE	Test MAE	Test R2 Score
  Base Model	3.21	3.16	-0.01
  Linear Regression	1.51	1.78	0.63
  Polynomial Regression	1.21	3.05	-3.31
  Ridge Regression	1.54	1.72	0.67
  Lasso Regression	1.51	1.75	0.65
  KNeighborsRegressor	0	1.92	0.52
  SVR	0.97	1.84	0.61



The following SciKitLearn regression models were utilized:
- Linear Regression
- Polynomial Regression
- Ridge Regression
- Lasso Regression
- KNeighbors Regression
- Support Vector Regression


#### Results
Models were evaulated on Mean Absolute Error (MAE) and the R2 score. The MAE was chosen to avoid overfitting on the few peak flows that are far from the average.
 - Ridge and Lasso regression were the best performing models.
 - Polynmial regression overfit on the training data and did not provide good results for this data.
 - The KNeighbors and SVR did well but not as good as the Ridge and Lasso Regression.
The results of the models evaluated are shown in the table below. The results are compared to a base model where the predicted flow is edqual to mean flow at the treatment plant. 


The Features that were most important in the best model (Ridge Regression) were: 

 - Recent historical flow to the treatment plant.
 - Precipitation received in the afternoon of the current day.
 - precipitation forceast in the morning of the next day.
 - Current day flow at the treatment plant.
 - Flow in the adjacent river on the current day.

#### Next steps
The precipitation data was found be the most significant feature in the flow prediction as anticipated. There is a known lag from the receiveing preciptation to the increase in flows at the treatment plant. However, the precipation data is a daily value only and precipiation received in the morning would have more of an influence on the daily treatment plant flow than precipitation recieved in the evening that would not result in treatment plant flow increase until the start of the next day. Therefore, it would be advantages to obtain precipration data on an hourly basis instead of a daily basis to potentially improve the prediction model. 


#### Outline of project




##### Contact and Further Information
Ryan Fisher at r.fisher.pe@gmail.com
