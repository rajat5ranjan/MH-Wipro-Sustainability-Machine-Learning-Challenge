# Wipro's Sustainability Machine Learning Challenge - Hiring Hackathon

## [Problem Statement](https://machinehack.com/hackathon/wipro_sustainability_machine_learning_challenge/overview)
Wipro Limited (NYSE: WIT, BSE: 507685, NSE: WIPRO) is a leading global information technology, consulting and business process services company. We harness the power of cognitive computing, hyper-automation, robotics, cloud, analytics and emerging technologies to help our clients adapt to the digital world and make them successful. A company recognized globally for its comprehensive portfolio of services, strong commitment to sustainability and good corporate citizenship, we have over 220,000 dedicated employees serving clients across six continents. Together, we discover ideas and connect the dots to build a better and a bold new future.

Along with being a global leader in artificial intelligence services from the latest reports of analysts like Forrester, IDC and Everest Group, Wipro has been rated as the second-best organization for data scientists to work in India in 2021 by Analytics India Magazine. The company has also been committed to reaching a Net-Zero Greenhouse Gas Emissions by 2040. 

Though a little late in the day, the world is waking up to the deleterious effect of fossil fuels on our environment. As the doomsday clock ticks away, human beings are turning to renewable energy to avert a possible apocalypse. Fortunately, the sun is a well-spring of clean energy. Taking the cue, Wipro, in association with MachineHack, has designed a forecasting challenge to optimise solar power generation using ML models.

A solar power generation company wants to optimize solar power production and needs the prediction model to predict ‘Clearsky DHI’, ‘Clearsky DNI’, ‘Clearsky GHI’. The data is ten years at an interval of every 30 mins with the following data points:

['Year', 'Month', 'Day', 'Hour', 'Minute', 'Temperature', 'Clearsky DHI', 'Clearsky DNI', 'Clearsky GHI', 'Cloud Type', 'Dew Point', 'Fill Flag', 'Relative Humidity', 'Solar Zenith Angle', 'Pressure', 'Precipitable Water', 'Wind Direction', 'Wind Speed']

`Train: 1,75,296 rows x 18 columns`

`Test: 17,520 rows x 15 columns`
 

### Skills
```text
* Time series forecasting
* Multi-label prediction
* Optimizing MSE
```
## Solution Approach

```text
* Text Preprocessing using Different Pipelines
* Text Features based approach using Feature Engineering
* Transfer Learning Using Simple Transformers using different models. Eg BERT, Roberta
* Multi label Straified Cross Validation
* Optimizing Log Loss using Ensemble approach to reduce Variance
```

## Steps to reproduce

* Run Below Notebooks in below Sequence

* **mh-wipro-ml-frkgrouptimekf**
    ```text
    * Approach
        1. Checking & cleaning outliers based on quantiles data for train of different features.
        2. Creating aggregated features based on Cloud Type & Time features.
        3. Feature Engineering on Time series data & getting relevant features from pvlib package for clear sky data & atmospheric variables.
        4. Lag features for dependent features like temperature, pressure, humidity etc. & time series signals
        5. LightGBM Regressor with GroupTimeSeriesSplit on Day column (Cross Validation mainly the key to tackle)
    * Local CV & Score
        * Mean Local CV Score - 429 MSE (Public LB - 261.97 MSE)
    * Solution File - mh_wipro_fork_tg15f_sub_new_v6.csv
    ```
* **mh-wipro-lag-notebook-kfolds**
    ```text
    * Approach
        1. Checking & cleaning outliers based on quantiles data for train of different features.
        2. Creating aggregated features based on Cloud Type & Time features.
        3. Feature Engineering on Time series data & getting relevant features from pvlib package for clear sky data & atmospheric variables.
        4. Lag features for dependent features like temperature, pressure, humidity etc. & time series signals
        5. Lag features for Target Variables
        6. LightGBM Regressor with Cross Validation using Kfold strategy.
    * Local CV & Score
        * Mean Local CV Score - 53.14 MSE (Public LB - 267.49 MSE)
    * Solution File - mh_lag_wipro_fork_v3_288kf_sub_v2.csv
    ```
* **mh-wipro-notebook-stratfkf**
    ```text
    * Approach
        1. Checking & cleaning outliers based on quantiles data for train of different features.
        2. Creating aggregated features based on Cloud Type & Time features.
        3. Feature Engineering on Time series data & getting relevant features from pvlib package for clear sky data & atmospheric variables.
        4. Lag features for dependent features like temperature, pressure, humidity etc. & time series signals
        5. LightGBM Regressor with Cross Validation using Stratified Kfold strategy using target bins.
    * Local CV & Score
        * Mean Local CV Score - 54.00 MSE (Public LB - 279.3 MSE)
    * Solution File - mh_lag_wipro_fork_kf_sub_stratv1.csv
    ```
* **Ensemble Approach**
    ```text
    * Approach
        1. Weighted Average of mh_wipro_fork_tg15f_sub_new_v6.csv, mh_lag_wipro_fork_kf_sub_stratv1.csv, mh_lag_wipro_fork_v3_288kf_sub_v2.csv based on CV score (ensemble.ipynb)
    * Final Solution File - ensemble.ipynb (mh_wipro_ens_stratv1_1_tg15fv6_5_kflgs_4.csv)
    ```

### [Leaderboard]https://machinehack.com/hackathon/wipro_sustainability_machine_learning_challenge/leaderboard)
```text
* Public Leaderboard 9th Rank
* Private Leaderboard 1st Rank
```

### Portfolio

|Site|Links|
|---|---|
|Linked In| https://www.linkedin.com/in/rajat-ranjan24/|
|GitHub| https://github.com/rajat5ranjan/|
|Website | https://rajat5ranjan.github.io |