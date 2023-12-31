# VBA-challenge
Module 2 Challenge - UWA/edX Data Analytics Bootcamp

Github repository at: https://github.com/alyssahondrade/VBA-challenge.git

## Table of Contents
1. [Introduction](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#introduction)
    1. [Goal](https://github.com/alyssahondrade/VBA-challenge/tree/main#goal)
    2. [Source Code](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#source-code)
    3. [Repository Structure](https://github.com/alyssahondrade/VBA-challenge#repository-structure)
    4. [Technology](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#technology)
    5. [Dataset](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#dataset)
2. [Approach](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#approach)
3. [Results](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#results)
    1. [Calculated Values (2018)](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#calculated-values-2018)
    2. [Calculated Values (2019)](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#calculated-values-2019)
    3. [Calculated Values (2020)](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#calculated-values-2020)
5. [References](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#references)
    1. [VBA Code](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#vba-code)
    2. [README](https://github.com/alyssahondrade/VBA-challenge/blob/main/README.md#readme)

## Introduction
### Goal
The goal of the project is to create a script that summarises a list of stock data to get the following:
1. Yearly change, from the opening price at the start of the year, to the closing price at the end of the year
2. Percent change (as above with yearly change)
3. Total stock volume

As well as the calculated values of the summarised results:
1. Greatest percentage increase
2. Greatest percentage decrease
3. Greatest total stock volume

### Source code
The source code for this project is [`vba-challenge.vbs`](https://github.com/alyssahondrade/VBA-challenge/blob/main/vba-challenge.vbs).

### Repository Structure
`Screenshots/` directory contains the screenshots of the results.

### Technology
VBA code was written using **Microsoft Excel for Mac** (Version 16.75.2).

### Dataset
The dataset was created by Trilogy Education Services (2U Inc. brand).

Initial testing for the code was conducted on [`alphabetical_testing.xlsx`](https://github.com/alyssahondrade/VBA-challenge/blob/main/alphabetical_testing.xlsx), with the final testing conducted on `multiple_year_stock_data.xlsx` (not provided due to file size).

## Approach
1. Understand the provided dataset prior to conducting any data wrangling. The following observations were made: 
    - Multiple spreadsheets with identically structured data, meaning the code would need to be looped for all spreadsheets.
    - Each spreadsheet had a different number of rows, meaning a function is required to either:
        - Loop through until the first "empty" row is found.
        - Find the last row for each sheet.
      
2. Prior to writing the VBA script, results were manually calculated in the initial test file to compare against script output.
    - Confirmed the number of unique tickers using `Data > Remove Duplicates`.
    - Used `SUMIF()` to get the total volume for each ticker.
    - Manually calculated samples of yearly change by referencing cells (i.e. the first 3 unique tickers).
      
3. Pseudocode produced to identify strategy:
    - What variables are required? What data type for each?
    - What outputs are required?
    - What loop method is appropriate to acquire summarised results?
    - What needs to be incremented through?
    - What relevant equations are required (i.e. yearly change and percent change)?
      
4. Staged Process
    1. Find the last row of the spreadsheet.
        1. Initial method: while-loop and `Not IsEmpty()` as the condition.
        2. Final method: for-loop and comparing an increment ahead.
    2. Loop through each row and get the unique ticker name.
    3. Get the correct value for `open_price`.
    4. Get the correct value for `close_price`.
    5. Calculate and set `yearly_change` and `percent_change`.
    6. Write code for calculated values.
       1. An if-block for `greatest_increase` and `greatest_decrease`, due to mutual exclusivity.
       2. An if-block for `total_greatest_volume`.
    7. Conditional formatting on `yearly_change` and `percent_change` columns.
    8. Add formatting and headings.
    9. Alter the code to run for multiple spreadsheets, updating required references (i.e. `fy.Range()` instead of `Range()`).
    10. Run the code on the final test data.
        1. Update data type for counters to `Long` or `LongLong` as required.
        2. Confirm correct results and formatting in each spreadsheet.

## Results
Screenshots of the results, using the final test data, are given below:

### Calculated Values (2018)
![Calculated Values (2018)](https://github.com/alyssahondrade/VBA-challenge/blob/main/Screenshots/Calculated%20Values%20-%202018.png)

### Calculated Values (2019)
![Calculated Values (2019)](https://github.com/alyssahondrade/VBA-challenge/blob/main/Screenshots/Calculated%20Values%20-%202019.png)

### Calculated Values (2020)
![Calculated Values (2020)](https://github.com/alyssahondrade/VBA-challenge/blob/main/Screenshots/Calculated%20Values%20-%202020.png)

## References
Code derived from Week 2, Day 3 of the bootcamp:
1. The for-loop concept incrementing one counter ahead.
2. The equation to find the last row.

The following references were accessed to produce the source code.

### VBA Code
- [1] Check empty cell
  [https://excelchamps.com/vba/check-empty-cell/](https://excelchamps.com/vba/check-empty-cell/)

- [2] Check cell address
  [https://stackoverflow.com/questions/47515141/cell-address-in-a-loop](https://stackoverflow.com/questions/47515141/cell-address-in-a-loop)

- [3] While-Wend statement
  [https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/whilewend-statement](https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/whilewend-statement)

- [4] Format to Percentage
  [https://excelchamps.com/vba/functions/formatpercent/](https://excelchamps.com/vba/functions/formatpercent/)

- [5] Data Type Summary
  [https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/data-type-summary](https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/data-type-summary)

- [6] Background Colours
  [https://www.excel-easy.com/vba/examples/background-colors.html](https://www.excel-easy.com/vba/examples/background-colors.html)

- [7] Format to 2 decimal places
  [https://www.mrexcel.com/board/threads/vba-change-number-of-decimal-places-of-a-percentage.521221/](https://www.mrexcel.com/board/threads/vba-change-number-of-decimal-places-of-a-percentage.521221/)

### README
- [8] Information on README files
  [https://datamanagement.hms.harvard.edu/collect-analyze/documentation-metadata/readme-files](https://datamanagement.hms.harvard.edu/collect-analyze/documentation-metadata/readme-files)

- [9] Example of a Data Analysis Project README
  [https://github.com/elizabethdaly/data-analysis-project/blob/master/README.md](https://github.com/elizabethdaly/data-analysis-project/blob/master/README.md)

- [10] README file format for Data Analysis projects
  [https://skillsforall.com/course/data-analytics-essentials?courseLang=en-US](https://skillsforall.com/course/data-analytics-essentials?courseLang=en-US)

- [11] README formatting
  [https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

- [12] Markdown Handybilly
  [https://github.com/fefong/markdown_readme](https://github.com/fefong/markdown_readme)
