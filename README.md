<div align="center">
    <h1># Where will users book their first travel destination?</h1>
</div>


## Introduction
Airbnb users have over 190 countries to choose from for their first booking. If we can accurately predict which country a new user will book their first trip in, it would allow Airbnb to provide more personalized through emails, on their homepage, and from third-party advertisers. They could also provide coupons to entice potential customers and decrease the amount of time customers wait before booking.

## Repository Structure
* **README.md**: The top-level README for reviewers of this project
* **data**:
    - **train_users_2.csv**: users main dataset. 
* **notebooks**:
    - **01.datat_visualication.ipynb**: visualize train_users_2 dataset
    - **02.data_processing**: First process the main dataset, then the sessions dataset that contains information about users' browsing.
    - **03.model.ipynp**: Try 3 algorithms and compare their scores.

 ## Requirements
In order to "run" the provided codes; jupyter notebook or vsCode.

## Libraries
* pandas
* NumPy
* seaborn 
* matplotlib
* warnings
* scikit-learn

## Algorithms
* Random forest
* lightgbm
* xgboost

image

## Known issues
sessions.csv wasn't included in the data folder due to its huge size. 

## Data Processing Steps

In this project, I performed the following data processing steps to prepare the dataset for predicting users' first travel destination.

1. **Datetime Features**

I started by extracting various date and time features from the `date_account_created` and `date_first_booking` columns in the `train_users_2.csv` dataset. These features included the year, month, and day of account creation and first booking.

2. **Numerical Features**

Next, I handled missing values in numerical columns. I calculated the percentage of missing values in the `age` column and filled them with the mode value. Additionally, I converted the `timestamp_first_active` column, which represented a timestamp, into a datetime format. I further divided this column into separate features such as year, month, day, hour, and minute.

3. **Correlation**

To understand the relationships between different variables, I computed the correlation between numerical features. This allowed me to generate a correlation matrix, providing a visual representation of the relationships.

4. **Object Features**

I selected categorical columns, excluding 'id' and 'country_destination', and handling missing values in the 'first_affiliate_tracked' and 'gender' columns. I filled these missing values with the mode value. Additionally, I processed the 'gender' column by replacing 'OTHER' and '-unknown-' values with NaN and generating random values based on the distribution of existing gender values.

5. **Encoder**

To work with categorical data, I encoded the selected categorical columns using an ordinal encoder. Furthermore, I encoded the target variable, 'country_destination', using a label encoder to prepare it for the machine learning models.

6. **Text Features**

I extracted text features from the 'sessions.csv' dataset. Specifically, I focused on the 'device_type' column and determined the most frequent device type for each user. Additionally, I combined the 'action', 'action_type', and 'action_detail' columns to create a new feature called 'actions'. I transformed the 'actions' column into a single-string representation for each user. To further process the text data, I used TF-IDF (Term Frequency-Inverse Document Frequency) vectorization.

