# Netflix Movies and TV Shows Content Dashboard

## Overview

This Power BI dashboard provides a comprehensive analysis of Netflix's movie and TV show catalog.
It offers insights into various aspects of the content, such as genre distribution, ratings, release year trends, and the number of seasons for TV shows. 
The visualizations aim to help users understand the trends in Netflix's offerings.

## Key Features

1. **High-Level Metrics:**
   - Total number of movies and shows (8,789).
   - Number of unique directors (4,525).
   - Number of genres (37).

2. **Content Trends:**
   - Maximum content added in a single year (2021).
   - Minimum content added in a single year (2008).

3. **Visualizations:**
   - **Top 10 Genres** by count of movies and TV shows.
   - Distribution of movies vs. TV shows.
   - Number of TV shows by the number of seasons.
   - Count of movies and TV shows by ratings.

## Data Source

This dashboard is based on a dataset containing Netflix's catalog information. It includes attributes like title, release year, genre, director, type (movie or TV show), number of seasons, and rating.
Here are the detailed steps for cleaning the data for a Netflix dashboard in Power BI or any data preparation tool:

---

## **Steps to Clean Netflix Dataset**

### **1. Import the Dataset**
- Load the dataset into Power BI (or a tool like Excel, Python, or Power Query).
  - In Power BI: Use **Home > Get Data > [Data Source]** to load the file.

---

### **2. Handle Missing Values**
- **Identify Missing Data:**
  - Go to **Transform Data** in Power BI.
  - Check for null or blank fields in columns like `Director`, `Genre`, or `Rating`.
- **Clean Missing Data:**
  - Replace missing values with appropriate placeholders (e.g., "Unknown" for missing `Director` or `Genre`).
  - For numerical fields (e.g., `Year Released`), you can replace nulls with a default value, like the median or average year.

---

### **3. Standardize Genres**
- **Remove Duplicates:**
  - Split multi-genre columns (e.g., "Drama, Thriller") into separate rows or columns if needed.
- **Standardize Naming:**
  - Correct inconsistencies (e.g., "Sci-fi" → "Science Fiction").
  - Merge similar genres (e.g., "Children & Family Movies" and "Kids' TV" can be grouped under "Family").

---

### **4. Format Dates**
- Check for consistency in date formats:
  - Convert `Year Added` and `Year Released` to a `Date` data type.
  - Extract `Year`, `Month`, or `Day` components if needed for analysis.
  - Ensure `Year Added` is later than or equal to `Year Released`.

---

### **5. Deduplicate Data**
- **Identify Duplicate Rows:**
  - Check for rows with the same `Title`, `Director`, `Year Released`, and `Type`.
- **Remove Duplicates:**
  - Keep the first instance or prioritize based on another column (e.g., latest `Year Added`).

---

### **6. Validate Numeric Data**
- Ensure columns like `Seasons` have valid values:
  - Remove or correct invalid entries (e.g., `0 seasons` for a TV show).
  - Convert text-based numbers (e.g., "One" → 1).

---

### **7. Standardize Ratings**
- Normalize rating formats:
  - Merge similar ratings (e.g., "TV-MA" and "MA").
  - Replace missing ratings with "NR" (Not Rated) or "Unknown".

---

### **8. Remove Irrelevant Columns**
- Identify and remove columns that are not needed for the analysis, such as:
  - `Cast` or `Description` (if not relevant to the dashboard).

---

### **9. Add Derived Columns**
- **Content Type:**
  - Create a column to classify content as "Movie" or "TV Show" based on the `Type` column.
- **Content Age:**
  - Add a column to calculate the age of the content:
    ```DAX
    Content Age = YEAR(TODAY()) - 'Table'[Year Released]
    ```
- **Genre Categories:**
  - Group similar genres into broader categories (e.g., "Action & Adventure" → "Action").

---

### **10. Verify Data Quality**
- Validate the data integrity:
  - Check for unrealistic values (e.g., `Year Released` in the future).
  - Ensure all categorical fields are correctly labeled.

---

### **11. Load Cleaned Data into Power BI**
- After cleaning, load the dataset back into Power BI for modeling and visualization:
  - Save and apply transformations in Power Query.

---

By following these steps, your Netflix dataset will be well-prepared for analysis, ensuring accurate and meaningful insights in your dashboard.
## Steps to Recreate the Dashboard

Follow these steps to recreate this Power BI dashboard:

### 1. **Prepare the Dataset**
   - Use a Netflix dataset (CSV, Excel, or database) containing fields like `Title`, `Year Added`, `Year Released`, `Director`, `Genre`, `Rating`, and `Type`.
   - Clean the data to ensure consistency, such as handling missing values or standardizing genres.

### 2. **Import the Dataset**
   - Open Power BI Desktop.
   - Go to **Home > Get Data > [Your data format]**.
   - Load the Netflix dataset into Power BI.

### 3. **Model the Data**
   - Check the data relationships in the **Model View**.
   - Ensure that key fields like `Genre` and `Type` are properly linked.

### 4. **Create Measures**
   Use DAX (Data Analysis Expressions) to calculate metrics, such as:
   - **Total Content**: `Total Content = COUNTROWS('Table')`
   - **Movies Count**: `Movies Count = COUNTROWS(FILTER('Table', 'Table'[Type] = "Movie"))`
   - **TV Shows Count**: `TV Shows Count = COUNTROWS(FILTER('Table', 'Table'[Type] = "TV Show"))`

### 5. **Build Visualizations**
   - **Cards**: Show total content, number of directors, genres, and key years.
   - **Bar Charts**: Visualize genres, ratings, and seasons.
   - **Pie Chart**: Show the percentage distribution of movies vs. TV shows.

### 6. **Format the Dashboard**
   - Use a dark theme for aesthetics.
   - Add slicers for filtering by `Year Released` and `Year Added`.
   - Customize titles and labels for clarity.

### 7. **Publish to Power BI Service**
   - Save the report as `.pbix`.
   - Publish it to your Power BI workspace using **File > Publish > Publish to Power BI**.

## Files in This Repository

- `Netflix-Dashboard.pbix`: Power BI project file.
- `Netflix-Dataset.csv`: Dataset used for the analysis.
- `README.md`: Documentation file (this file).
- `Screenshots/`: Folder containing dashboard screenshots.

## How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/netflix-dashboard.git
   ```
2. Open the `.pbix` file in Power BI Desktop to view or modify the dashboard.
3. Use the dataset to explore the insights.

## Future Improvements

- Add trend analysis for popular genres over time.
- Include geographic distribution of Netflix's content.
- Use additional datasets for cross-platform comparisons.

---


