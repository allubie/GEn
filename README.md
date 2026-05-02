# GEn - Synthetic Dataset Generator

This project provides a modular, Python-based synthetic dataset generator designed specifically for Jupyter Notebook environments. It features a user-friendly gui built with `ipywidgets`, allowing users to select data fields across multiple domains and generate a logically consistent, relational dataset exportable as a CSV file.

## Features

* Interactive GUI: Use checkboxes, sliders, and buttons directly in your Jupyter Notebook to configure your dataset.
* Relational Integrity: Later fields reference previously generated values in the same row to maintain logical realism (e.g., shipping dates always follow order dates).
* Extensive Data Domains: Supports Demographics, Health Metrics, Geography, Products, Commerce, and IT/System Data.
* Instant Export: Automatically generates a timestamped CSV file containing your customized dataset.
* Preview Integration: Displays a sample of the generated DataFrame directly within the notebook output.

## Requirements

To use the generator, you need Python installed along with the following libraries:

* pandas
* numpy
* Faker
* ipywidgets
* IPython

You can install these dependencies using pip and the provided `requirements.txt` file:

```bash
pip install -r requirements.txt
```

## Usage

1. Open a Jupyter Notebook.
2. Copy and paste the generator class and UI code into a single cell.
3. Run the cell to display the interactive widget.
4. Expand the categories to select the specific fields you need for your dataset.
5. Adjust the "Row Count" slider to define the size of your dataset (from 10 to 10,000 rows).
6. Click "Generate & Export". The script will create the data, save it as a CSV in your current working directory, and display a preview.

## Data Domains and Fields

The generator currently supports the following fields grouped by domain:

* Demographics: Customer ID, Name, Age, Gender, Education Level, Occupation, Email, Registered Date
* Health Metrics: Height (cm), Weight (kg), BMI, Blood Type, Heart Rate (bpm)
* Geography: Country, City, State, Zip Code, Latitude, Longitude, Timezone
* Products: SKU, Product Name, Category, Model, Size, Color, Ratings, Review Count
* Commerce: Price, Quantity, Discount (%), Total, Order Status, Order Date, Shipping Date, Shipping Carrier, Payment Method
* IT/System Data: IP Address, MAC Address, User Agent, OS, UUID

## The Golden Rules (Relational Logic)

This tool is designed to produce realistic data by enforcing strict rules:

* Temporal Integrity: Registered dates precede order dates. Shipping dates logically follow order dates based on order status (e.g., Cancelled orders have no shipping date).
* Identity Correlation: Email addresses are derived directly from the generated Name.
* Financial Accuracy: The Total price is strictly calculated from Price, Quantity, and Discount.
* Biological Consistency: BMI is mathematically derived from Height and Weight. Health metrics adjust based on Age and BMI.
* Product Constraints: Product models, sizes, and names are bound to the selected product Category.
* Geographical Specifics: Payment methods adapt to regional preferences.

## Extensibility

The code utilizes a class-based approach (`UniversalGenerator`). You can easily add custom data domains by updating the `self.domains` dictionary in the `__init__` method and adding the corresponding generation logic in the `_generate_row` method.
