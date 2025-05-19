# CITS4407 - Assignment 2

## Project Overview

This project focuses on processing and analyzing real world data from the BoardGameGeek dataset using foundational Bash scripting. It demonstrates automation, data cleaning, and exploratory analysis via shell scripting.

The project consists of three scripts, each handling a different stage in the data workflow:

1. `empty_cells` – Inspects missing values in the dataset.
2. `preprocess` – Cleans and formats raw board game data for analysis.
3. `analysis` – Extracts insights such as popular mechanics, domains, and statistical correlations.

---

## Script Descriptions

### 1. `empty_cells`

- **Purpose:**  
  This script checks for **missing or empty cells** in each column of the dataset. Missing values are a common issue in real world data, and identifying them is essential before any cleaning or analysis can be done. It trims white spaces and removes quotes to accurately count truly empty fields.

- **How it works:**
  - Accepts a delimited text file (CSV/TSV/etc.) and its delimiter (e.g., `;` or `\t`).
  - Reads the header to identify column names.
  - Iterates over each cell, checking for emptiness after cleaning up white spaces and special characters.
  - Outputs a count of empty cells per column.

- **Usage:**  
  ```bash
  ./empty_cells <filename> <separator>

---

### 2. `preprocess`

- **Purpose:**  
  Cleans a semicolon-separated raw dataset by performing the following operations:
  - Converts semicolons (`;`) to tab characters (`\t`) for standard TSV formatting.
  - Normalizes line endings from Windows style (CRLF) to Unix style (LF).
  - Replaces decimal commas (e.g., `8,79`) with decimal points (`8.79`) for numeric consistency.
  - Removes all non ASCII characters to avoid encoding issues.
  - Automatically fills in missing game IDs with new unique numeric values.
  - Ensures that the `Mechanics` and `Domains` fields are quoted and consistently comma separated.

- **Usage:**  
  ```bash
  ./preprocess <raw_file>

---

### 3. `analysis`

- **Purpose:**  
  Performs basic exploratory analysis on the cleaned BoardGameGeek dataset. This script automates the discovery of key trends and statistical insights, including:
  - Identifying the most frequently occurring game mechanics across the dataset.
  - Identifying the most common game domains.
  - Calculating the Pearson correlation between:
    - Year of publication and average rating.
    - Game complexity and average rating.

- **Usage:**  
  ```bash
  ./analysis <cleaned_file.tsv>

---