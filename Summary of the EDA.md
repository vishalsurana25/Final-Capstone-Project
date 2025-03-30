## **Summary of the Exploratory Data Analysis (EDA):**

[**Script Used**](https://github.com/vishalsurana25/Final-Capstone-Project/blob/main/Final%20Project%20with%20EDA.ipynb) 

**1\. Data Loading and Inspection:**

* The dataset (`full_data_set_merged.csv`) was loaded, and the date column (`DATE`) was converted to the appropriate datetime format.  
* Basic information about the dataset, including data types and missing values, was displayed. Any invalid dates were handled appropriately.

**2\. Time Series Visualization:**

* **Economic Indicators:** Time series plots were generated to visualize the trends and patterns of the economic indicators (e.g., `PRICE_PER_GALLON`, `UNEMPLOYMENT_RATE`, `INTEREST_RATES`) over time.  
* **Housing Prices:** A sample of housing prices for different regions was plotted over time to observe their behavior and potential seasonality.

![Image](https://github.com/user-attachments/assets/b6d09ad1-ec23-47bb-acef-a945f18389d3)

![Image](https://github.com/user-attachments/assets/a60951fe-18cf-4529-b6a9-56060c8cdd30)


**3\. Descriptive Statistics:**

* Descriptive statistics (mean, standard deviation, min, max, quartiles, etc.) were calculated and displayed for the economic indicators, providing a statistical overview of their distributions.

<img width="929" alt="Image" src="https://github.com/user-attachments/assets/0e2d06a3-86be-4787-90ec-f83efa58b8e0" />



**4\. Distribution Visualization:**

* **Histograms and Box Plots:** Histograms and box plots were generated for the economic indicators to visualize their distributions, identify potential skewness or outliers, and gain a better understanding of the data's central tendency and spread.

![Image](https://github.com/user-attachments/assets/17e396f4-d958-44cd-a6cd-3504bb538c67)

![Image](https://github.com/user-attachments/assets/201eca0c-fb6b-4bab-b384-6c0d19fa989b)


**5\. Correlation Analysis:**

* **Correlation Matrix and Heatmap:** A correlation matrix was calculated and visualized as a heatmap to identify the relationships (positive, negative, or weak) between the economic indicators. This helps in understanding how changes in one indicator might be related to changes in others.

![Image](https://github.com/user-attachments/assets/284b57d4-41c1-4173-8d5b-84082792070a)



* **Correlation with Target:** The correlation between the economic indicators and the selected target region's housing prices was also analyzed to identify potentially predictive features.

![Image](https://github.com/user-attachments/assets/a0610776-9bc8-45f1-9505-5f29eb7546aa)

**6\. Pair Plot Visualization:**

* **Pairwise Relationships:** A pair plot was generated to visualize the relationships between all pairs of economic indicators. This provides a more detailed view of the correlations and potential interactions between features.

![Image](https://github.com/user-attachments/assets/41f693d1-0ded-45b2-af2b-9d4850cb1406)

**7\. Target Region Selection:**

* The user was prompted to select a target region (* **selected Zipcode was 26869**) for housing price prediction, ensuring that the selected region is present in the dataset.

**8\. Target Variable Analysis (Scatter Plots):**

* **Feature vs. Target:** Scatter plots were generated to compare each economic indicator to the housing prices of the selected target region. This visualization helps assess the individual relationship and potential predictive power of each feature.

![Image](https://github.com/user-attachments/assets/12c3e17c-f2e5-4d6b-9d9d-565bf6b8a7e5)

**Key Insights and Potential Observations (hypothetical):**

* **Time series plots** may reveal overall economic trends or seasonal patterns in housing prices.  
* **Histograms and box plots** could highlight data skewness, outliers, or unusual distributions in economic indicators.  
* **Correlation analysis** might show strong positive or negative correlations between specific indicators and housing prices, suggesting potential predictive relationships.  
* **Pair plots** may uncover further interactions or patterns among features.  
* **Scatter plots** would help visualize the relationship between each individual indicator and the target region's housing prices.

**Overall,** the EDA provides a comprehensive understanding of the dataset, identifying potential patterns, relationships, and insights that can inform feature selection, model development, and ultimately, housing price prediction.



## **Model Comparison: Housing Price Prediction**

[**Script Used**](https://github.com/vishalsurana25/Final-Capstone-Project/blob/main/Final%20Project%20with%20EDA.ipynb) 

This section provides a comprehensive comparison of the three models employed for predicting housing prices in zip code 10001 using economic indicators. The comparison focuses on their performance, strengths, weaknesses, and suitability for this specific task.

### **1\. Linear Regression:**

* **Performance:**  
  * MSE: 46.8452  
  * R²: 0.6631  
  * Adjusted R²: 0.6599  
* **Strengths:**  
  * **Simplicity:** Linear Regression is a straightforward and easily interpretable model, making it a good baseline for comparison.  
  * **Computational Efficiency:** It is computationally inexpensive to train and predict, which can be advantageous for large datasets or real-time applications.  
* **Weaknesses:**  
  * **Linearity Assumption:** It assumes a linear relationship between features and target, which might not hold true in complex real-world scenarios like housing markets.  
  * **Sensitivity to Outliers:** It can be sensitive to outliers, potentially affecting the accuracy of predictions.  
* **Suitability:**  
  * Linear Regression may be suitable for initial exploration or when a simple, interpretable model is desired. However, its performance was weaker compared to the other models in this project, indicating limitations in capturing the complexities of the housing market.

![Image](https://github.com/user-attachments/assets/bd08782e-4034-4927-8dd7-56e3ef69e22c)


### **2\. Random Forest (Tuned):**

* **Performance:**  
  * MSE: 26.5339  
  * R²: 0.8202  
  * Adjusted R²: 0.8178  
* **Strengths:**  
  * **Non-Linearity:** It can capture non-linear relationships between features and target, making it more adaptable to real-world data.  
  * **Robustness to Outliers:** It is less sensitive to outliers compared to Linear Regression, improving prediction accuracy and stability.  
  * **Feature Importance:** It provides insights into feature importance, helping understand which economic indicators are most influential in predicting housing prices.  
* **Weaknesses:**  
  * **Computational Cost:** It can be computationally more expensive to train than Linear Regression, especially with a large number of trees.  
  * **Interpretability:** While feature importance provides some insight, the overall model can be less interpretable than Linear Regression.  
* **Suitability:**  
  * Random Forest proved to be the best-performing model for this project, achieving the lowest MSE and highest R². Its ability to handle non-linear relationships and robustness to outliers make it well-suited for predicting housing prices using economic indicators.
  * 

![Image](https://github.com/user-attachments/assets/7cd950e4-c120-4e0f-8112-6034a4aebdfb)

### **3\. Neural Network (Tuned):**

* **Performance:**  
  * MSE: 28.4777  
  * R²: 0.8069  
  * Adjusted R²: 0.8044  
* **Strengths:**  
  * **High Complexity:** It can model highly complex relationships, potentially achieving even higher accuracy than Random Forest with sufficient data and tuning.  
  * **Adaptability:** It is adaptable to different types of data and can be customized with various architectures to suit specific problems.  
* **Weaknesses:**  
  * **Overfitting:** Prone to overfitting, especially with limited data or complex architectures, requiring careful hyperparameter tuning and regularization techniques.  
  * **Computational Cost:** Can be computationally expensive to train, especially with deep architectures and large datasets.  
  * **Black Box:** Less interpretable than Linear Regression or Random Forest, making it challenging to understand the underlying decision-making process.  
* **Suitability:**  
  * Neural Network performed competitively, offering the potential for high accuracy but requiring careful tuning. It might be a better choice with larger datasets and for scenarios where interpretability is less critical.

![Image](https://github.com/user-attachments/assets/636e9186-983e-445e-9ff5-b74935b26ef2)

### **4\. Summary:**

* **Best Performer:** Random Forest (Tuned) emerged as the best overall model for this project based on its superior performance scores (lowest MSE, highest R²) and ability to capture non-linear relationships.  
* **Runner-Up:** Neural Network (Tuned) also demonstrated strong performance and could potentially achieve even higher accuracy with further tuning and larger datasets. However, it's more prone to overfitting and less interpretable.  
* **Baseline:** Linear Regression served as a baseline, but its limitations in capturing complex relationships led to weaker performance compared to the other models.

**Overall Recommendation:**

* For predicting housing prices in zip code 10001 using the selected economic indicators, **Random Forest (Tuned)** is recommended due to its accuracy, robustness, and relatively good interpretability.  
* If higher accuracy is paramount and sufficient data is available, **Neural Network (Tuned)** could be further explored with careful attention to overfitting and computational cost.  
* **Linear Regression** may be suitable for initial exploration or simpler scenarios, but it's likely not the optimal choice for this specific problem due to its performance limitations.

![Image](https://github.com/user-attachments/assets/ef599264-9351-4f3d-804e-30e24d345946)

This detailed comparison provides a thorough analysis of the three models, considering their performance, strengths, and weaknesses in the context of housing price prediction using economic indicators. The recommendation is based on a balanced evaluation of these factors and aims to provide the most effective approach for this particular task.


