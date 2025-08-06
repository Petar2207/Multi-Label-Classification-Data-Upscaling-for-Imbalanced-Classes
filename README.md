# 📊 Multi-Label Classification: Data Upscaling for Imbalanced Classes

This project focuses on addressing the issue of imbalanced data in multi-label classification. The objective is to preprocess survey data, encode categorical labels, identify and upscale minority labels to improve model performance, and output a balanced dataset ready for machine learning.

## 🎯 Project Goal

The main goal of this project is to clean, preprocess, and upscale survey data that contains multiple categorical labels, particularly focusing on labels with fewer than 300 instances. This will ensure that the dataset is balanced for training machine learning models, allowing for more accurate predictions.

## ✅ Workflow Summary

### 1. Data Loading & Preprocessing

- **Loading Data**: The project reads three separate Excel files (`1.xlsx`, `2.xlsx`, `3.xlsx`) and merges them into one unified dataset.
  
- **Data Cleaning**:  
    - Removed leading and trailing spaces from string columns.
    - Filtered columns to retain only `questionText`, `category_type`, `answer`, and `categoriesParent`.
    - Split the comma-separated values in the `categoriesParent` column into individual labels, creating a list for each row in the new `labels` column.

- **Handling Missing Values**:  
    - Dropped rows where any critical column (`questionText`, `category_type`, `answer`) contains null values.

### 2. Multi-Label Binarization

- **Label Encoding**: Used `MultiLabelBinarizer` to convert multi-labels into a binary format, creating a column for each possible label and assigning a `1` or `0` to indicate whether the label applies to a given row.

### 3. Upscaling Minority Classes

- **Identifying Minority Labels**:  
    - Checked for labels with fewer than 300 instances, as they are considered underrepresented in the dataset.
  
- **Upscaling**:  
    - For each minority label, the rows with that label were upsampled using bootstrapping (resampling with replacement) to ensure a minimum of 300 instances per label.

### 4. Data Combination & Export

- **Data Combination**:  
    - Combined the original dataset (excluding the minority rows) with the upsampled data, creating a balanced dataset where each label is adequately represented.

- **Export**:  
    - The final balanced dataset is saved as a CSV file (`df_combined.csv`), which can be downloaded for further analysis or used in machine learning models.

## ⚠️ Known Issues & To-Do

- **Data Quality**: Ensure that the Excel files (`1.xlsx`, `2.xlsx`, `3.xlsx`) are clean and formatted correctly before processing.
- **Label Imbalance**: While the script handles minority labels, it is crucial to ensure that the dataset's overall quality is maintained during preprocessing and upscaling.
- **Scalability**: For very large datasets, consider optimizing the upsampling function to reduce memory and time complexity.

## 🛠️ Tech Stack

- **Languages**: Python
- **Libraries**: pandas, numpy, scikit-learn, google.colab (for file uploads/downloads)

## 📜 License

This project is licensed under the MIT License — free to use and modify.

## 👤 Author

Petar Rajic

### Install Required Libraries

To set up the environment and install the necessary libraries, run:

```bash
pip install pandas numpy scikit-learn
