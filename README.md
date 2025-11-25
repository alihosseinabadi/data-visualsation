# Customer Data Analysis with Pandas

A comprehensive data analysis project demonstrating pandas operations on customer dataset with data cleaning, transformation, and analysis techniques.

## 📋 Project Overview

This Jupyter Notebook contains a complete data analysis workflow using Python's pandas library to process and analyze customer data from a CSV file. The project showcases various data manipulation techniques commonly used in real-world data analysis scenarios.

## 📊 Dataset Information

The dataset contains **100 customer records** with the following columns:
- `Index` - Unique identifier
- `Customer Id` - Customer identification code
- `First Name` - Customer's first name
- `Last Name` - Customer's last name
- `Company` - Company name
- `City` - Customer's city
- `Country` - Customer's country
- `Phone 1` - Primary phone number
- `Phone 2` - Secondary phone number
- `Email` - Email address
- `Subscription Date` - Date of subscription
- `Website` - Company website

## 🛠️ Technologies Used

- **Python 3.x**
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computing
- **Matplotlib** - Data visualization (imported but not used in shown code)

## 🔧 Data Operations Performed

### 1. Data Loading & Initial Exploration
```python
# Load dataset
cs = pd.read_csv("downloads/costumer.csv")

# Display first 10 records
print(cs.head(10))

# Dataset information
cs.info()
cs.columns
```

### 2. Data Cleaning & Validation
- Checked for null values with `cs.isnull()`
- Filled missing values with `cs.fillna(0)`
- Verified no null values remain with `cs.isnull().sum()`

### 3. Data Transformation
```python
# Create new columns
cs['newname'] = cs["First Name"]

# Remove duplicates
cs.drop_duplicates(inplace=True)

# Rename columns
cs.rename(columns={"newname": "cpfirstname"}, inplace=True)

# String operations - convert to lowercase
cs["First Name"] = cs["First Name"].apply(lambda x: x.lower())
```

### 4. Data Filtering & Selection
```python
# Select specific columns
cs[['First Name', 'Last Name', 'Index']].head(10)

# Filter records
cs[(cs['Index'] < 20)]

# Conditional column creation
cs["first10website"] = cs["Website"].index < 10
```

### 5. Data Sorting
```python
# Sort by index in descending order
cs.sort_values("Index", ascending=False)
```

### 6. Custom Functions & Grouping
```python
# Apply custom function
def greet(Firstname):
    return f"hello {Firstname}"
cs["greet"] = cs["First Name"].apply(greet)

# Group operations
mix = cs.groupby("Index")[["First Name", "Last Name"]].tail(10)
```

## 📈 Key Features Demonstrated

### Data Quality Checks
- Comprehensive null value detection and handling
- Duplicate record removal
- Data type validation

### Data Manipulation
- Column creation and renaming
- String operations and case conversion
- Conditional column generation
- Efficient data filtering techniques

### Advanced Operations
- Custom function application with `apply()`
- Data grouping and aggregation
- Multi-column sorting
- Conditional indexing

### Data Cleaning Pipeline
1. **Initial Assessment**: Check data structure and quality
2. **Cleaning**: Handle missing values and duplicates
3. **Transformation**: Modify data types and create derived columns
4. **Validation**: Verify data integrity after transformations

## 🚀 Usage

### Prerequisites
```bash
pip install pandas numpy matplotlib jupyter
```

### Running the Analysis
1. Place your customer data CSV file in the `downloads/` directory
2. Update the file path in the notebook: `pd.read_csv("downloads/costumer.csv")`
3. Execute the cells sequentially to reproduce the analysis

## 📁 Project Structure

```
customer-analysis/
├── downloads/
│   └── costumer.csv          # Dataset file
├── customer_analysis.ipynb   # Main notebook
└── README.md                 # Project documentation
```

## 💡 Learning Outcomes

This project demonstrates essential pandas operations including:
- **Data Import/Export** - Reading CSV files
- **Data Inspection** - Understanding dataset structure
- **Data Cleaning** - Handling missing values and duplicates
- **Data Transformation** - Creating and modifying columns
- **Data Filtering** - Selecting subsets of data
- **Data Aggregation** - Grouping and summarizing data
- **Data Sorting** - Organizing data for analysis

## 🔍 Potential Extensions

- Add data visualization with matplotlib/seaborn
- Implement statistical analysis
- Create data validation functions
- Build automated data cleaning pipelines
- Add unit tests for data quality checks

## 📝 Note

The dataset used in this project contains synthetic customer data with international entries, making it ideal for practicing various data manipulation scenarios commonly encountered in business analytics.

---

*This project serves as a comprehensive example of pandas data manipulation techniques suitable for data analysts, data scientists, and anyone working with tabular data in Python.*
