## **Predicting U.S. Housing Prices Using Economic Indicators and Machine Learning**

## **Project Overview**

**What is this project about?**

This project focuses on developing and evaluating machine learning models to predict housing prices across various regions within the United States. The housing market is influenced by a complex interplay of economic factors. In the current economic climate, marked by significant fluctuations and notably high inflation rates (reaching levels not seen in 40 years as of recent reporting), understanding the impact of these macroeconomic variables on housing affordability and valuation is more critical than ever. Our group aims to leverage data-driven techniques to unravel these relationships and provide predictive insights into housing market trends.

**Project Question**

Can machine learning models effectively predict housing prices across diverse regions of the United States utilizing key economic indicators such as inflation rates (Consumer Price Index), fuel prices, interest rates, unemployment rates, and average mortgage rates?

**Why is this important?**

Housing is one of the biggest financial decisions people make. Economic changes, like the recent high inflation, can significantly impact property values. Being able to forecast housing prices, even with some uncertainty, can help:

* **Home Buyers & Sellers:** Make more informed decisions about when to buy or sell, potentially saving or earning thousands of dollars.  
* **Policymakers & Analysts:** Understand the sensitivity of the local housing market to broader economic shifts.

**How did we approach this?**

We used historical data and machine learning (a type of artificial intelligence that learns patterns from data) to build predictive models. We specifically tested and compared three different techniques: Linear Regression, Random Forest, and a Neural Network.

## **Project Goals**

Our main objectives were to:

1. **Explore Data:** Dig into historical economic numbers and housing prices for Zip Code 10001 to find trends and potential connections.  
2. **Identify Key Drivers:** Determine which economic factors seem to have the biggest impact on housing prices in this area.  
3. **Build & Tune Models:** Create and fine-tune three different types of machine learning models (Linear Regression, Random Forest, Neural Network) designed to predict housing prices based on the economic factors.  
4. **Evaluate Performance:** Rigorously test how accurate each model's predictions are using standard statistical measures.  
5. **Recommend the Best:** Identify the most accurate and reliable model for this specific task.  
6. **Generate Insights:** Understand the relationships discovered between the economy and local housing prices.

## **The Data**

* **Source:** The project uses a combined dataset containing historical information gathered from various public sources.  
* **Target:** The primary value we aim to predict is the **median housing price within Zip Code 10001**.  
* **Features (Predictors):** We focused on key economic indicators as inputs to our models:  
  * `PRICE_PER_GALLON`: Average cost of gasoline.  
  * `UNEMPLOYMENT_RATE`: The percentage of the workforce that is unemployed.  
  * `INTEREST_RATES`: Key benchmark interest rates influencing lending.  
  * `INFLATION`: The rate at which the general level of prices for goods and services is rising (measured by CPI).  
  * *(Note: Average Mortgage Rates were also explored but potentially excluded from the final model features based on analysis).*  
* **Data Preparation:** Before analysis, the data required cleaning, ensuring dates were correctly formatted, and handling any missing information to maintain quality.

## **Methodology: Our Step-by-Step Approach**

We followed a structured process to build and evaluate our predictive models:

1. **Data Exploration & Analysis (Understanding the Past):**

   * **Visualization:** We created charts (Time Series Plots) to see how economic factors and housing prices in Zip Code 10001 have changed over time. This helped us spot long-term trends or cycles.  
   * **Statistics:** We calculated basic statistics (like average, min, max) for each economic indicator to get a feel for their typical values and ranges. We also used charts (Histograms, Box Plots) to see the shape of their distributions and identify any unusual data points (outliers).  
   * **Correlation Check:** We looked for statistical relationships between each economic indicator and the housing prices using a Correlation Matrix (visualized as a heatmap). This helped us see if factors tended to move together (positive correlation) or in opposite directions (negative correlation). We also used Pair Plots to visualize relationships between all pairs of economic indicators.  
2. **Feature Selection (Choosing the Right Ingredients):**

   * Based on the correlation analysis, general economic understanding, and the goal of creating a focused model, we selected the following indicators as the primary features for prediction:  
     * `PRICE_PER_GALLON`  
     * `UNEMPLOYMENT_RATE`  
     * `INTEREST_RATES`  
     * `INFLATION`  
3. **Model Development & Tuning (Building the Predictors):**

   * We implemented three different machine learning models:  
     * **Linear Regression:** A fundamental statistical model that assumes a straight-line relationship between the economic factors and housing prices. It serves as a good baseline for comparison.  
     * **Random Forest:** A more advanced model that builds many individual "decision trees" and combines their predictions. It's known for its accuracy and ability to capture complex, non-linear relationships. We used a technique called `GridSearchCV` to automatically find the best settings (hyperparameters) for this model.  
     * **Neural Network:** An algorithm inspired by the structure of the human brain, with interconnected layers of "neurons". It can potentially model very complex patterns. We built a network with two hidden layers and used a manual search process combined with cross-validation to fine-tune its settings (like learning rate and layer sizes).  
   * **Data Scaling:** Before training the models (especially the Neural Network), we scaled the feature data so that all indicators were on a comparable numerical range. This often helps the models learn more effectively.  
4. **Model Evaluation (Checking the Scorecard):**

   * To judge how well each model performed, we used a separate portion of the data (the "test set") that the models hadn't seen during training. We measured performance using:  
     * **Mean Squared Error (MSE):** The average of the squared differences between the model's predicted price and the actual price. *Lower values are better*, indicating less prediction error on average.  
     * **R-squared (R²):** A percentage (between 0 and 1\) that represents how much of the variation in housing prices the model can explain using the economic indicators. *Higher values are better*, indicating a better fit.  
     * **Adjusted R-squared:** Similar to R², but it penalizes the score for using too many features that don't significantly improve the prediction, helping to avoid overfitting. *Higher values are generally preferred*.  
   * We also generated **Diagnostic Plots** (Actual vs. Predicted, Residuals vs. Predicted) to visually inspect the models' predictions and identify any systematic errors or biases.

## **Results & Findings**

The performance of the three models on the test dataset is summarized below:

| Model | Mean Squared Error (MSE) | R² | Adjusted R² |
| :---: | :---: | :---: | :---: |
| Linear Regression | 46.8452 | 0.6631 | 0.6599 |
| **Random Forest (Tuned)** | **26.5339** | **0.8202** | **0.8178** |
| Neural Network (Tuned) | 28.4777 | 0.8069 | 0.8044 |

***(Lower MSE is better, Higher R² / Adjusted R² is better)***

**Key Observations:**

* The **Tuned Random Forest model clearly outperformed** the other two models.  
* It achieved the **lowest prediction error (MSE)** and explained the **highest proportion of housing price variation (R² and Adjusted R²)**, around 82%.  
* While the Tuned Neural Network also performed well (better than Linear Regression), the Random Forest was slightly more accurate and reliable on this specific dataset and task.  
* Linear Regression, being the simplest model, provided a baseline but couldn't capture the complexities as effectively as the other two.

## **Recommendation & Conclusion**

**Recommended Model:**

Based on its superior performance metrics (lowest MSE, highest R²/Adjusted R²), the **Tuned Random Forest model** is recommended for predicting housing prices in Zip Code 10001 using the selected economic indicators.

**Why?**

The Random Forest model demonstrated the best ability to accurately predict unseen housing prices in our tests. Its strength likely comes from its ability to handle potentially complex and non-linear relationships between the economic factors and housing prices, which might exist in real-world markets.

**Conclusion:**

This project successfully demonstrated that machine learning techniques, particularly Random Forest, can be effectively applied to forecast regional housing price trends based on economic indicators. The developed Random Forest model provides a potentially valuable tool for understanding and anticipating housing market movements in Zip Code 10001\.

While no model can predict the future with perfect accuracy, this analysis offers valuable insights. Continuous improvement is possible by incorporating more data, exploring additional relevant features (e.g., housing supply, demographics), and testing other advanced modeling techniques.

## **How to Use / Run the Code**

*(This section would typically include instructions like)*

1. **Setup:** Clone this repository. It's recommended to use a virtual environment.  
2. **Install Dependencies:** Run `pip install -r requirements.txt` (assuming a requirements file exists with pandas, scikit-learn, tensorflow, matplotlib, seaborn).  
3. **Data:** Ensure the data file (`full_data_set_merged.csv`) is placed in the correct directory as specified by the `FILE_PATH` variable in the script.  
4. **Execute:** Run the main Python script: `python your_script_name.py`. The script will perform data loading, analysis, model tuning, evaluation, and generate output/plots. *Note: The Neural Network tuning step can be time-consuming.*

## **Technology Stack**

* **Language:** Python 3.x  
* **Core Libraries:**  
  * Pandas (Data manipulation and analysis)  
  * NumPy (Numerical operations)  
  * Scikit-learn (Machine learning models \- LR, RF, GridSearchCV, metrics, preprocessing)  
  * TensorFlow / Keras (Neural network implementation)  
  * Matplotlib / Seaborn (Data visualization)

