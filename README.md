# Excel Data Science Salary Dashboard

![full view](https://github.com/user-attachments/assets/265679ae-386c-4060-b160-10a510e50696)


## Introduction

This interactive Excel dashboard analyzes salary trends for data science and related roles, helping job seekers and professionals evaluate compensation based on job titles, countries, and employment types. Built as part of an Excel for Data Analytics course, it leverages real-world job data to provide insights into median salaries, job counts, and top platforms.

The dashboard allows users to filter by job title (e.g., Data Scientist, Data Engineer), country (e.g., United States, Sudan), and job type (e.g., Full-time, Part-time), dynamically updating visualizations and key metrics.

## Dashboard File

The complete dashboard is available in the repository:  
[Salary_Dashboard_Project.xlsx](Salary_Dashboard_Project.xlsx)

To interact with the dashboard:  
- Open the file in Microsoft Excel.  
- Use the dropdown menus for Job Title, Country, and Type to filter data.  
- Note: For optimal performance, ensure calculations are set to automatic (Formulas > Calculation Options > Automatic).

## Excel Skills Demonstrated

This project showcases a range of Excel skills for data analysis and visualization:  
- 📊 **Charts and Visualizations**: Bar charts for job title comparisons, map charts for geographic salary distribution, and optimization for clarity.  
- 🧮 **Formulas and Functions**: Array formulas (e.g., MEDIAN with IF conditions), FILTER, SORT, UNIQUE, and COUNTIFS for dynamic calculations.  
- ❎ **Data Validation**: Dropdown lists with filtered unique values to ensure user-friendly inputs.  
- 🔄 **Data Management**: Table conversions, data cleaning (e.g., removing combined values like "Full-time and Part-time"), and protection of sheets to prevent unintended changes.  
- ⚙️ **Optimization**: Named ranges, formula indentation for readability, and performance tweaks (e.g., replacing array multiplication with COUNTIFS for faster computation).

## Dataset Overview

The dataset contains over 32,000 entries from 2023 data science job postings, sourced from the course materials. Key columns include:  
- **Job Title Short**: Simplified titles (e.g., Data Scientist, Data Engineer).  
- **Job Country**: Location of the job (e.g., United States, Sudan).  
- **Job Schedule Type**: Employment type (e.g., Full-time, Part-time).  
- **Salary Year Avg**: Annual salary (used for median calculations).  
- **Job Via**: Platform where the job was posted (e.g., Indeed, LinkedIn).  

Data cleaning involved extracting unique values, handling combined schedule types, and excluding zeros or invalid entries.

## Dashboard Components

### 📉 Charts

#### Job Title Median Salaries - Horizontal Bar Chart
- **Description**: Compares median salaries across job titles, highlighting the selected title in a darker shade for emphasis.  
- **Excel Features**: Bar chart with custom formatting (e.g., $K for thousands), conditional columns to highlight selections, and SORT for descending order.  
- **Formula Example** (Median Salary Calculation):  
  ```
  =MEDIAN(IF((jobs[job_title_short]=A2)*(jobs[job_country]=country)*(ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*(jobs[salary_year_avg]<>0), jobs[salary_year_avg]))
  ```  
- **Insights**: Senior roles (e.g., Senior Data Scientist) command higher salaries, with Engineers often outpacing Analysts.  
- **Screenshot**:  
  ![job title - median bar chart](https://github.com/user-attachments/assets/890f0bc2-3d35-4e8f-a0e5-803c9ca33cb1)
 (Excerpt from full dashboard)

#### Country Median Salaries - Map Chart
- **Description**: Visualizes median salaries by country on a world map.  
- **Excel Features**: Map chart with color gradients, FILTER and SORT for data preparation, and handling of partial data matches (e.g., 74% confidence for locations).  
- **Formula Example** (Filtered Country List):  
  ```
  =SORT(FILTER(A2:B#, ISNUMBER(B2#)), 2, -1)
  ```  
- **Insights**: Highlights global disparities, e.g., higher salaries in the US and Russia compared to emerging markets.  
- **Screenshot**:  
 ![map chart](https://github.com/user-attachments/assets/7dfd3acb-b6a7-4527-a58d-84a886168b98)
  (Excerpt from full dashboard)

#### Job Type Median Salaries - Horizontal Bar Chart
- **Description**: Breaks down salaries by employment type, with the selected type emphasized.  
- **Excel Features**: Similar to the job title chart, with SEARCH for partial matches in schedule types.  
- **Insights**: Full-time roles typically offer higher median salaries than part-time or contract positions.

### 🧮 Formulas and Functions

#### Unique Job Schedule Types
- **Formula**:  
  ```
  =FILTER(UNIQUE(jobs[job_schedule_type]), (NOT(ISNUMBER(SEARCH("and", UNIQUE(jobs[job_schedule_type])))))*(UNIQUE(jobs[job_schedule_type])<>0))
  ```  
- **Purpose**: Generates a cleaned list of schedule types (e.g., excluding "Full-time and Part-time") for data validation.

#### Top Job Platform
- **Formula** (Using COUNTIFS for efficiency):  
  ```
  =COUNTIFS(jobs[job_via]=A2, jobs[job_title_short]=title, jobs[job_country]=country, jobs[job_schedule_type]=type)
  ```  
- **Purpose**: Identifies the platform with the most job postings (e.g., Indeed) based on filters.

#### Job Count
- **Formula**:  
  ```
  =XLOOKUP(title, A2:A#, B2:B#, "No Results")
  ```  
- **Purpose**: Returns the count of jobs matching the selected filters.

### ❎ Data Validation

- **Dropdowns**: Sourced from sorted unique lists (e.g., job titles, countries, types) using UNIQUE and SORT.  
- **Implementation**: Ensures inputs are valid and dynamic, with sheet protection to lock non-editable cells.

## Build Process

1. **Data Preparation**: Imported dataset, converted to table, cleaned schedule types, and created unique lists in a validation sheet.  
2. **Calculations**: Built median salary formulas with multi-condition IF arrays, then optimized for performance.  
3. **Visualizations**: Created charts, applied custom formatting, and used named ranges (e.g., "title", "country", "type") for dynamic updates.  
4. **Interactivity**: Added data validation dropdowns and protected the sheet.  
5. **Optimization**: Replaced slow array formulas with COUNTIFS, hid supporting sheets, and removed gridlines/headers for a clean UI.

## Conclusion

This project demonstrates my ability to transform raw job data into an interactive, user-friendly dashboard using Excel's core and advanced features. It highlights salary trends, aiding career decisions in data science. For collaboration or questions, feel free to open an issue or connect on LinkedIn.

Explore the Excel file to interact with the dashboard and review the supporting sheets for detailed formulas.  
check out my other repositories for more projects!

## Contact

For questions or feedback, please open an issue on this GitHub repository or email me at `esterabimobina@gmail.com`.
