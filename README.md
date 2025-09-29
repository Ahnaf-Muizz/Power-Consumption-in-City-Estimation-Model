# Power-Consumption-in-City-Estimation-Model
Conducted literature review and developed linear, polynomial, and ML-based models using bootstrapping on 50K+ weather data points to estimate urban power consumption
# Tetuan City Power Consumption Prediction

[cite_start]This project, developed by Ahnaf Muizz Chowdhury and Miles St. James, focuses on predicting power consumption in Tetuan City based on meteorological data[cite: 2, 14]. We utilize various regression models to estimate power usage in three distinct zones, providing a tool for analysis and forecasting.

## Project Overview

[cite_start]The primary goal is to build predictive models that estimate power consumption for three different zones using weather parameters as independent variables[cite: 89, 90]. [cite_start]The project involves data cleaning, exploratory data analysis, and the implementation of both multilinear and polynomial regression models to find the best fit for the data[cite: 210, 1093]. [cite_start]Finally, a command-line user interface was developed to make predictions using the most effective models[cite: 1737, 1738].

## Dataset

[cite_start]The analysis is based on the "Tetuan City power consumption" dataset[cite: 40].

* [cite_start]**Initial Size**: 52,416 entries and 7 columns[cite: 42, 88].
* **Features**:
    * [cite_start]`DateTime` [cite: 88]
    * [cite_start]`Temperature` [cite: 88]
    * [cite_start]`Humidity` [cite: 88]
    * [cite_start]`Wind Speed` [cite: 88]
    * [cite_start]`Zone 1 Power Consumption` [cite: 88]
    * [cite_start]`Zone 2 Power Consumption` [cite: 88]
    * [cite_start]`Zone 3 Power Consumption` [cite: 88]
* [cite_start]**Independent Variables**: `Temperature`, `Humidity`, and `Wind Speed`[cite: 89, 211].
* [cite_start]**Dependent Variables**: Power consumption for `Zone 1`, `Zone 2`, and `Zone 3`[cite: 90, 212].

## Methodology

### 1. Data Preprocessing

[cite_start]The initial dataset was loaded and inspected for inconsistencies[cite: 36, 44]. [cite_start]Outliers were identified in the `Wind Speed` column through pair plot analysis[cite: 128, 132]. [cite_start]To refine the dataset, entries where the `Wind Speed` exceeded a value of 5 were removed[cite: 134]. [cite_start]This resulted in a cleaned dataset with 52,397 rows[cite: 168, 180].

### 2. Exploratory Data Analysis (EDA)

* [cite_start]**Pair Plots**: Scatter plots and histograms were generated for all variables to visually inspect distributions and relationships between them[cite: 91, 135].
* [cite_start]**Correlation Heatmaps**: To quantify the strength of linear relationships between the weather variables and power consumption in each zone, correlation heatmaps were created[cite: 241, 530, 839]. [cite_start]For example, the correlation between Temperature and Zone 1 Power Consumption was found to be 0.44 [cite: 267][cite_start], while it was 0.38 for Zone 2 [cite: 537] [cite_start]and 0.49 for Zone 3[cite: 848].

### 3. Modeling and Evaluation

[cite_start]The dataset was split into training (80%) and testing (20%) sets to build and validate the models[cite: 293, 1104]. [cite_start]Both Multilinear and Polynomial (degree 2) regression models were trained for each zone[cite: 210, 1093]. [cite_start]Model performance was assessed using the following metrics on both the training and test sets[cite: 297, 303]:
* $R^2$ (R-squared)
* Mean Squared Error (MSE)
* Root Mean Squared Error (RMSE)

After evaluating multiple combinations of features, the following models were selected for the final prediction tool:

| Zone | Model Type | Independent Variables | Test Set $R^2$ Score |
| :--- | :--- | :--- | :--- |
| **Zone 1** | Polynomial (Degree 2) | Temperature, Humidity | [cite_start]0.228 [cite: 1182, 1222] |
| **Zone 2** | Multilinear | Temperature, Humidity | [cite_start]0.172 [cite: 1751, 732] |
| **Zone 3** | Polynomial (Degree 2) | Temperature, Humidity | [cite_start]0.296 [cite: 1759, 1689] |

## Features

### Prediction Tool & User Interface

[cite_start]A command-line interface (CLI) was developed to allow users to get power consumption estimates based on their inputs[cite: 1783, 1784].

* [cite_start]The user provides values for **Temperature** and **Humidity**[cite: 1788].
* [cite_start]The user selects a **Zone (1, 2, or 3)** for the prediction[cite: 1794].
* [cite_start]The tool uses the pre-trained model for the selected zone to output the predicted power consumption[cite: 1796, 1797].
* [cite_start]The interface also provides an option to save the user's input and the corresponding prediction to a new CSV file named `New Power Consumption Observations.csv`[cite: 1801, 1812, 1818].

## Technologies Used

[cite_start]The project was implemented in Python 3.12.4 (via Anaconda) [cite: 12, 24] and utilized the following libraries:
* [cite_start]`pandas` [cite: 27]
* [cite_start]`numpy` [cite: 28]
* [cite_start]`matplotlib` [cite: 29]
* [cite_start]`seaborn` [cite: 30]
* [cite_start]`scikit-learn` [cite: 31]
* [cite_start]`statsmodels` [cite: 33]

## How to Run the Prediction Tool

1.  Ensure you have a Python environment with the libraries listed above installed.
2.  Save the prediction script to a file (e.g., `predict.py`).
3.  Run the script from your terminal:
    ```bash
    python predict.py
    ```
4.  Follow the prompts to enter the temperature, humidity, and select a zone.

**Example Interaction:**
Welcome to the Power Consumption Prediction Tool!
Enter the temperature (°C): 25
Enter the humidity (%): 80

Select the Zone for Prediction:
1: Zone 1
2: Zone 2
3: Zone 3
Enter the zone number (1, 2, or 3): 2

Predicted Power Consumption for Zone 2: 24843.86 kW

Do you want to add this observation to the dataset? (yes/no): yes
Observation added and saved to 'New_Power_Consumption_Observations.csv' successfully!
