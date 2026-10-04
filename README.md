# Machine Learning Assignment 4

## End-to-End — Raw File to Model-Ready Data

### Dataset

**Hotel Booking Demand Dataset**

Dataset link: https://github.com/mpolinowski/hotel-booking-dataset

The dataset contains hotel booking records with numerical, categorical, and date-related attributes. It contains more than 5,000 rows and more than 8 columns, along with genuine missing values.

### Objective

The objective of this assignment is to build an end-to-end preprocessing workflow that converts a raw dataset into a clean, model-ready matrix.

No machine learning model is trained in this assignment.

### Workflow

The preprocessing workflow consists of:

1. Loading the raw dataset
2. Creating a data dictionary
3. Performing a raw data quality assessment
4. Handling missing values
5. Removing duplicate records
6. Handling invalid numerical values
7. Standardizing categorical values
8. Creating new features
9. Splitting the dataset into training and testing sets
10. Encoding categorical variables
11. Scaling numerical variables
12. Creating a preprocessing pipeline
13. Verifying that the final matrix contains no missing values
14. Saving the cleaned dataset and fitted pipeline

### Feature Engineering

Four new features were created:

* `total_nights` — total number of weekend and weekday nights.
* `total_guests` — total number of adults, children, and babies.
* `total_previous_bookings` — total previous canceled and non-canceled bookings.
* `adr_per_guest` — average daily rate calculated per guest.

### Cleaning Decisions

The following cleaning decisions were implemented:

* Duplicate rows were removed.
* The `company` column was removed because it contains a very large proportion of missing values.
* Missing `children` values were replaced with 0.
* Missing `country` values were replaced with `Unknown`.
* Missing `agent` values were replaced using the median.
* Negative numerical values were treated as invalid and replaced using median values.
* Leading and trailing whitespace was removed from categorical values.
* Remaining missing numerical and categorical values were handled before preprocessing.
* `reservation_status` and `reservation_status_date` were excluded from the model-ready feature matrix because they contain post-booking information.

### Before and After

The notebook generates the following comparison table:

| Metric         | Raw Dataset |         Final Dataset |
| -------------- | ----------: | --------------------: |
| Row Count      |      119390 | Generated in notebook |
| Column Count   |          32 | Generated in notebook |
| Missing Values |     Present |                     0 |
| Duplicate Rows |     Present |                     0 |

The exact final values are generated directly from the dataset during notebook execution.

### Preprocessing Pipeline

The preprocessing pipeline uses:

* Median imputation for numerical variables
* StandardScaler for numerical variables
* Most-frequent imputation for categorical variables
* OneHotEncoder for categorical variables
* `handle_unknown="ignore"` for unseen categories

### Output Files

This repository contains:

* `assignment4_endtoend.ipynb` — complete preprocessing notebook
* `cleaned_data.csv` — cleaned and feature-engineered dataset
* `pipeline.joblib` — fitted preprocessing pipeline
* `README.md` — project documentation

### Final Verification

The notebook verifies that:

* No NaN values remain in the processed training or testing matrices.
* Training and testing matrices contain the same number of columns.
* No feature is constant.
* The complete workflow runs from raw data to model-ready matrices.

### Conclusion

The assignment demonstrates an end-to-end data preparation workflow starting from a raw hotel booking dataset and ending with clean numerical matrices suitable for future machine learning tasks. The preprocessing pipeline is saved using Joblib so that the same transformations can be reused later.
