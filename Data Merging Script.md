## **Data Merging Script**

[**Script Used**](https://github.com/vishalsurana25/Final-Capstone-Project/blob/main/Merge_files.ipynb) 

This document summarizes the Python script designed to load, preprocess, and merge multiple datasets related to housing prices and economic indicators into a single, unified dataset.

**1\. Setup and Configuration:**

* **Imports:** Imports necessary libraries, primarily pandas for data manipulation and datetime for date handling.  
* **Configuration:** Defines dictionaries for:  
  * paths: Centralizes the file paths for all input CSV files (zipcodes, time-based prices, CPI, interest rates, mortgage rates, unemployment, gas prices) and the final output file.  
  * econ\_cols: Maps original economic indicator column names to standardized final names (e.g., 'CPIAUCNS' to 'INFLATION').

**2\. Helper Function:**

* A function safe\_to\_datetime is defined to convert date columns into datetime objects. It handles potential errors during conversion by turning unparseable dates into NaT (Not a Time) and reports the number of conversion failures.

**3\. Data Loading:**

* The script loads all specified CSV files into separate pandas DataFrames. It includes basic error handling to stop execution if any essential input file is not found.

**4\. Time-Based Housing Price Preprocessing:**

* **Filtering:** The main housing price dataset (time\_prices) is filtered to keep only rows corresponding to RegionIDs present in the zipcodes dataset.  
* **Restructuring:** Unnecessary columns are dropped.  
* **Transposing:** The DataFrame is transposed so that dates become the index and each RegionID becomes a column header representing housing prices for that region over time.  
* **Date Handling:** The date index is converted to datetime objects using the helper function and then reset to become a standard 'DATE' column. Rows with invalid dates are dropped.

**5\. Supplementary Data Preprocessing:**

* Each supplementary dataset (CPI, interest, mortgage, unemployment, gas) undergoes similar preprocessing:  
  * **Column Selection:** Relevant columns (typically a date column and a value column) are selected.  
  * **Date Conversion:** The date column is converted to datetime objects using the helper function, and rows with invalid dates are dropped.  
  * **Renaming:** The value column is renamed to its standardized name as defined in the econ\_cols configuration.

**6\. Data Merging:**

* The preprocessed time-based housing price DataFrame serves as the base.  
* Each preprocessed supplementary DataFrame is sequentially merged with the base DataFrame.  
* The merge operation uses an inner join based on the common 'DATE' column. This ensures that only dates present in *all* datasets being merged are retained in the final output. Checks are performed to ensure the 'DATE' column exists and is of the correct type before each merge.

**7\. Finalization and Output:**

* **Cleaning:** Any rows containing NaN (missing) values are dropped from the merged DataFrame.  
* **Reordering (Optional):** Columns are reordered to place the 'DATE' column first, followed by the standardized economic indicators, and then all the regional housing price columns.  
* **Inspection:** Information (.info()) and the first few rows (.head()) of the final DataFrame are printed. A check is included to warn if the final DataFrame is empty.  
* **Saving:** The final, merged, and cleaned DataFrame is saved to a new CSV file specified in the paths configuration (full\_data\_set.csv or full\_data\_set\_merged.csv based on the specific save command used). Error handling is included for the saving process.

This script effectively combines time-series housing data with relevant economic indicators aligned by date, creating a comprehensive dataset suitable for further analysis or modeling
