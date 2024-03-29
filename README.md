### Flow Prediction for Wastewater Treatment Plants

Ryan Fisher

#### Executive summary
The flow into wastewater treatment plants can be predicted by utilizing a linear regression machine learning model. Various models were investigated for this application using data from a treatment plant in New York State. The Ridge Regression Model was determined to provide the best predicition of flow. 

#### Rationale
The flow into wastewater treatment plants is influenced by precipitation and groundwater that infiltrates into the wastewater collections system piping. This is a particular for old aging infrasture in wet areas such as the Northeast United States. The spike in flows to a treatment plant require the operations staff to adjust treatment operations, place additional treat basins in service and call up addition operations staff to react to the sudden increase in flows. The high flows caused by precipitation events can cause overflows, bypass of treatment or damage to equipment. 

The increase in flows is typically unknown to the operators and they rely on their intuition to estimate the increase in flows due to forecasted weather events. The intent of the project is to develop a machine learning model to help predict the flow to the treatment plant based on forecasted precipitation events. 
    <center>
        <img src = images/overview.png width = 70%/>
    </center>


#### Research Question
Can a machine learning model be utilized to predict the flows at a wastewater treatment given the current known conditions and the available forecast storm precipitation event? 

#### Data Sources
Three sources are data will be utilized to build a training and test set for the model.
1. Flow data data collected from a treatment in Rockland County, New York was utilized. The data included the daily average influent flow to the treatment plant.
2. Data collected from the nearby New York State Mesonet weather station. The information from the station include hourly precipitation.
3. River flow data from a U.S. Geologic Survey stream gauging station. The flow data was utilized in the model to infer groundwater and the potential on water infiltration into the wastewater collection system. 

#### Methodology
The data from the three different source was cleaned and combined into one dataset. Feature engineering was used to develope the features(inputs) that a treatment plant operator would have avialable to enter to make their prediction. 
A regression model was trained on the data and scored based performation with a set of testing data.

The features used as input to the model include:
- Forecast Precipitation
- Current and historic precipitation
- Current and historic treatment plant flow
- Current and historic river flow

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
 - Polynomial regression overfit on the training data and did not provide good results for this data.
 - The KNeighbors and SVR did well but not as good as the Ridge and Lasso Regression.
The results of the models evaluated are shown in the table below. The results are compared to a base model where the predicted flow is edqual to mean flow at the treatment plant.

    <center>
        <img src = images/results_table.png width = 60%/>
    </center>

The Features that were most important in the best model (Ridge Regression) were: 

 - Recent historical flow to the treatment plant.
 - Precipitation received in the afternoon of the current day.
 - precipitation forceast in the morning of the next day.
 - Current day flow at the treatment plant.
 - Flow in the adjacent river on the current day.

The treatment plant in this project has a mean flow of 23 million gallons per day (mgd) with a range of from from  13 mgd to 64 mgd. The Ridge model was able to predict the flow of treatment plant with a +/- 1.7 (mgd). The flow prediction test set graph is shown below. 
    <center>
        <img src = images/result_graph.png width = 90%/>
    </center>
#### Next steps
The utilization of the flow prediction model should be deployed in real-time in order to provide useful flow predictions for the treatment plant operators.  

#### Outline of project
The Jupyter notebooks for this project are arrranged as follows:
1. Exporatory Data Analysis: [flow_prediction_EDA](https://github.com/rfisher133/Flow_Prediction/blob/main/1_flow_prediction_EDA.ipynb)
2. Feature Engineering: [flow_prediction_feature_engineering](https://github.com/rfisher133/Flow_Prediction/blob/main/2_flow_prediction_feature_engineering.ipynb)
3. Modeling: [flow_prediction_model](https://github.com/rfisher133/Flow_Prediction/blob/main/3_flow_prediction_model.ipynb)

##### Contact and Further Information
Ryan Fisher at r.fisher.pe@gmail.com
