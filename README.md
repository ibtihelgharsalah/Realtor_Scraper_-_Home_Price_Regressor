# Project Title: Real Estate Data Analysis and Prediction

## Overview

This project focuses on gathering real estate data by scraping the web, processing it, performing analysis, and providing predictions based on predictive models. 

By leveraging web scraping techniques, it retrieves housing information, prepares it for analysis, visualizes relationships between variables, and predicts property prices using machine learning models.

## Purpose

The primary goal is to assist users in making decisions related to property investments, sales, or purchases by offering them predictions into the housing market.

## Main Functionalities

1. **Data Scraping**: Utilizes web scraping techniques (Selenium and BeautifulSoup) to gather data from online sources.
2. **Data Processing**: Cleans and preprocesses the collected data (using Pandas and NumPy) to make it suitable for analysis and modeling.
3. **Data Visualization**: Generates visualizations (using Matplotlib and Seaborn) to illustrate relationships between housing features and prices.
4. **Machine Learning Modeling**: Constructs predictive models (using scikit-learn's random forest) to forecast property prices based on various features.
5. **Prediction and Insights**: Predicts property prices for new houses' data.

## Libraries and Technologies Used

- **Pandas**: Used for data manipulation and analysis.
- **NumPy**: Used for numerical operations.
- **re**: Used for generating regular expressions.
- **Selenium**: Employed for web scraping.
- **BeautifulSoup**: Utilized for HTML parsing.
- **scikit-learn**: Used for machine learning modeling and evaluation.
- **Matplotlib**: Used for data visualization.
- **Seaborn**: Used for enhanced data visualization.

## Project Structure
### UML
![Project UML](Realtor_Scraper_-_Home_Price_Regressor/UML.png)
### Classes and Functions

#### `RealtorScraper`
- `scrape_houses_data(page_url, ds_file_name)`: Scrapes housing data from specified URLs, saves the data to Excel, and returns a DataFrame.

#### `DataFramePreprocessor`
- `combine_dataframes(dataframes)`: Combines multiple DataFrames into one.
- `prepare_great_df_for_regression(final_ds)`: Prepares the DataFrame for regression by handling missing values, encoding categorical features, and scaling numerical features.

#### `DataVisualizer`
- `visualize_data()`: Generates visualizations for data analysis, including scatter plots and box plots.

#### `PriceRegressor`
- `regress(df)`: Performs regression modeling using Random Forest and evaluates the model's performance.

#### `PricePredictor`
- `predictt(new_data, prediction_file)`: Uses the trained model to predict prices for new data and saves predictions to an Excel file.

#### `Manager`
- `manage_complete_tasks(page_urls, ds_file_names, new_data, final_ds, prediction_file)`: Orchestrates the entire workflow by coordinating scraping, preprocessing, visualization, modeling, and prediction tasks.

## Running the Project

To run the project:
1. Instantiate a Manager object.
2. Define URLs and file names required for scraping and processing data.
4. Create a DataFrame for new data that needs prediction.
5. Run the `manage_complete_tasks` method with the necessary parameters:

   Example:

   ```python
   # create an instance of the manager class
    manager_1= Manager()
    page_urls1= ['https://www.realtor.com/realestateandhomes-search/Birmingham_AL/show-newest-listings/sby-6',
                'https://www.realtor.com/realestateandhomes-search/Birmingham_AL/show-newest-listings/sby-6/pg-2',
                'https://www.realtor.com/realestateandhomes-search/Birmingham_AL/show-newest-listings/sby-6/pg-3',
                ]
    ds_file_names1= ["page_1.xlsx", "page_2.xlsx", "page_3.xlsx"]
    new_data1= pd.DataFrame({
        'num_beds': [3.0, 4.0, 1.0, 2.0, 3.0, 5.0, 6.0, 1.0],
        'num_baths': [2.0, 3.0, 2.5, 4.5, 3.5, 1.0, 4.0, 1.5],
        'sqft': [2000, 2500, 1905, 5000, 3000, 1500, 1200, 3500]})
    final_ds1= "final_ds1.xlsx"
    prediction_file1= "prediction_file1.xlsx"
    new_file1= "new_file1.xlsx"
    prediction_result1= manager_1.manage_complete_tasks(page_urls1, ds_file_names1, new_data1, final_ds1, prediction_file1, new_file1)
    prediction_result1



