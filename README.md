# SAS Intro & Importing Data
Getting Started with SAS Programming.

## Repo Overview
This repo provides an overview of SAS programming.
- https://www.coursera.org/learn/sas-programming-basics/home/welcome

SAS® OnDemand for Academics Dashboard
- https://welcome.oda.sas.com/home

Listendata Tutorial
- https://www.listendata.com/p/sas-tutorials.html

## Data Setup
For the initial data setup, I downloaded the zip file from coursera, and ran the SAS program CourseraStartupCode.SAS. Both are in the github repo.

## High-level look at the structure of SAS programs
A SAS program consists of a sequence of **steps**. Each step in the program performs a specific task. There are two kinds of steps in SAS programs: DATA steps and PROC or procedure steps. A SAS program can contain any combination of DATA steps and PROC steps depending on the tasks you want to perform. DATA and PROC steps get their name from the **key word** that begins the first statement in the step, DATA or Proc. Most apps end with a run statement, and a few PROC steps and with a quit statement. If you don't use a run statement at the end of a step, the beginning of a new DATA or PROC step signals the end of the previous step.

### What SAS Can Do
SAS Can:
- allow you to enter, retrieve, and manager your data easily
- read data from various external sources - Excel, CSV, Text Files, Databases, Webpages, etc.
- explore and manipulate data in SAS
- analyze your data statistically and mathematically. Includes various statistical techniques
- generate graphs and tables
- run SQL queries on SAS datasets
- automate repetitive tasks with SAS Macros
- develop new software applications

### DATA Steps
- Generally reads data from an input source, processes it, and creates a SAS table
- Might also filter rows, compute new columns, join tables, and perform other data manipulations

### PROC or Procedure Steps
- Process a SAS table in a specific a predefined wa
- Generate reports and graphs, managed data, or perform complex statistical analyses

![](Resources/SAS4.PNG)
### Statements
Each step consists of a sequence of **statements**, and most statements start with the **keyword** that's part of the SAS language. All statements must end with a semicolon.

![](Resources/SAS2.PNG)

Types of statements:
- Data statement
- Set statement
- Assignment statement
- Print statement
- Run statement
- Global statement 

Global statements typically define some option or setting for the SAS session. They can be outside of DATA and PROC steps, and do not need run statements.

![](Resources/SAS3.PNG)

## How to Import Data
### How to Upload Data to SAS Ondemand for Academics
Uploading files allows you to use files stored on your computer within the SAS program. The file can be in any format, and does not need to be in the SAS data file formate, .sas7bdat. 

To use a file saved on your computer, follow these two simple steps:
- First, upload the file to your SAS OnDemand for Academics account
- Second, import the uploaded file using either Import Data utility or PROC IMPORT procedure.

### Using the Import Data utility
1. Go to the desired folder where you want to import the file. It is located on the left-hand side of the screen under Server Files and Folders pane.
2. Right click on the folder and then click on Upload Files.
3. Click on Choose Files and then locate and select the file you want to import. Then click on Upload button
4. Once done, the file should be appeared in the folder you selected in step 1.
5. In the folder where file is imported, locate the imported datafile and then right click on it and select the Import Data option.
6. Click on the Run button to start importing.
7. SAS Studio will import the CSV file and create a new dataset. By default, the imported dataset will be available in the WORK library.


The Import Data utility automatically show the file information and generate SAS code for importing.

### Import Data using PROC IMPORT instead of Import Data utility
The basic syntax of PROC IMPORT is as follows. The following SAS code creates a SAS dataset named MYDATA in the temporary library called WORK.

![](Resources/SASImport.JPG)

## PROC IMPORT
PROC IMPORT is a powerful SAS procedure that allows you to import data from various external file formats into SAS datasets. It simplifies the process of importing data in SAS.

### Syntax: PROC IMPORT
Syntax of PROC IMPORT is defined below.

![](Resources/SASImport2.JPG)

Arguments of PROC IMPORT : Explanation

1. DATAFILE: Specify the location of the file to be imported.
2. OUT: Specify the name to assign to the dataset after it is imported into SAS
3. DBMS: Define the format of the file being imported. Some of the common values are CSV, EXCEL, TAB, DLM, ACCESS.
4. REPLACE: Determine whether to replace the existing SAS Dataset. Yes/No.
5. GETNAMES: Specify whether to use the first row as variable names. By default it it YES. If you set the option as NO, it will tell SAS not to use the first row of data as variable names. In this case SAS assigns variable names as VAR1, VAR2, VAR3 if there are 3 variables.

### File Formats supported in PROC IMPORT
Following is a list of file extensions supported in PROC IMPORT. Specify the value in DBMS=identifier option

![](Resources/SASImport3.JPG)

### Use PROC IMPORT to Import CSV Files
A simple example to import a CSV file into SAS.

![](Resources/CSVImport.JPG)

The above SAS Program creates a SAS dataset named READIN in the temporary library (WORK). DBMS=CSV tells SAS that the file being imported is a CSV file. To see the imported file in RESULTS window, you can use PROC PRINT procedure. See the SAS program below.

![](Resources/CSVImport2.JPG)

DBMS=XLSX informs SAS that the file being imported is a MS Excel file (with .xlsx extension).

Additional Options in PROC IMPORT to Import Excel File

### Use PROC IMPORT to import an Excel File
In the example below we are importing Excel file in SAS.

![](Resources/XLSXImport.JPG)

DBMS=XLSX informs SAS that the file being imported is a MS Excel file (with .xlsx extension).

Additional Options in PROC IMPORT to Import Excel File

![](Resources/XLSXImport2.JPG)
- SHEET: Specify the name of the sheet in the Excel file from which you want to import data. When you use PROC IMPORT without explicitly mentioning the SHEET option, SAS will automatically import the first sheet of the Excel file by default. If you want to import a specific sheet, you need to explicitly specify the sheet name.
- DATAROW: Specify the row number from which you want SAS to import data. If GETNAMES=YES, the DATAROW value must be greater than or equal to 2. If GETNAMES=NO, the DATAROW value must be greater than or equal to 1.
- RANGE: Specify the range of Excel file. For e.g. RANGE="Sheet1$A1:D50"

### Use PROC IMPORT to Import Delimited File, SPSS Files, etc.
For more information on importing delimited files, and SPSS files, etc., check out https://www.listendata.com/2023/05/proc-import.html, or search google.

## Importing EXCEL Data into SAS
PROC IMPORT is the SAS procedure used to read data from excel into SAS. This section goes more in-depth on how to import excel data to SAS with PROC IMPORT.

### PROC IMPORT Syntax
![](Resources/ExcelImport.JPG)
1. DATAFILE=option tells SAS where to find the Excel file that you want to import (Complete filename path). For example : DATAFILE = "C:\Desktop\age.xlsx"
- Note: Using SAS OnDemand for Academics follows different steps, syntax.
2. OUT= option tells SAS to create a dataset with any name of your choice. By default, the imported dataset is saved on WORK library (temporary library)
- Examples :
- OUT = Age . In this statement, PROC IMPORT uses the WORK library and dataset name is Age. Please note that OUT = Age is equivalent to OUT = Work.Age .
- OUT = Input.Age In this statement, PROC IMPORT uses the Input library (Permanent library).
3. DBMS=option tells SAS the type of file to read.
Examples :
- DBMS = XLS for Excel 97-2003 workbooks
- DBMS = XLSX for Excel 2007 and above workbooks
4. SHEET= option is used to specify which sheet SAS would import.
- Examples :
- SHEET = "Sheet1" - To import data from worksheet named sheet1.
- SHEET = "Goal" - To import data from worksheet named Goal.
5. GETNAMES= YES tells SAS to use the first row of data as variable names.
- By default, PROC IMPORT uses GETNAMES= YES. If you type GETNAMES= NO, SAS would not read variable names from first row of the sheet.
6. DATAROW= option is used to specify starting row from where SAS would import the data.
- For example : DATAROW =5 tells SAS to start reading data from row number 5.
- Note :
- i. When GETNAMES=YES, DATAROW must be greater than or equal to 2
- ii. When GETNAMES=NO, DATAROW must be greater than or equal to 1
7. RANGE= option is used to specify which range SAS would import.
- Examples :
- i. RANGE="Sheet1$B2:D10"
- This would tell SAS to import data from range B2:D10 from sheet1
- ii. RANGE="Information"
- This would tell SAS to import data from excel defined name range. In the example shown above, it is Information.

### Example Excel File Import into SAS
![](Resources/ExcelImport2.JPG)
1. DATAFILE= "C:\age.xlsx" tells SAS where to find the Excel file that you want to import. Use XLS for MS Excel 97-2003
2. Note: In SAS Studio, DATAFILE = "/home/username/age.xlsx"
3. OUT= WORK.age tells SAS to create a dataset named age stored in WORK library
4. DBMS= XLSX tells SAS the XLSX (Excel 2007 and above) format file to read.
5. REPLACE is used to overwrite the age dataset if it exists already.
6. SHEET= "Sheet1" tells SAS to import data from Sheet1.
7. GETNAMES="YES" tells SAS to use the first row of data as variable names.

### Importing an excel file from specified row
![](Resources/ExcelImport3.JPG)
- DATAROW=5 tells SAS to start reading data from row number 5.
- In this case, variable (column) names would be pulled from first row but column values would be extracted from row 5.

### Importing or removing variable name from other than first row
Suppose variable names are placed at second row in excel sheet.
![](Resources/ExcelImport4.JPG)
- NAMEROW=2 tells SAS to extract variable names from second row and STARTROW=3 is used to pull values from third row.
- NAMEROW only works with XLS but not with XLSX.

### Importing only specified columns from excel file
![](Resources/ExcelImport5.JPG)
- The OUT = filename followed by KEEP= statement is used to retain the desired variables.
- In the example shown above, we retained four variables ID,X,Y and Z.

In the same way, you can use DROP= statement to remove the variables that you don't want to retain.
![](Resources/ExcelImport6.JPG)

### Importing only rows that have non-missing data for all the variables
![](Resources/ExcelImport7.JPG)
- In the example shown above, WHERE= statement is used to delete all the rows that have only missing data on variables x,y and z.

### Importing Data from Excel based on Specified Range
![](Resources/ExcelImport8.JPG)
- RANGE="Sheet1$B4:E100" tells SAS to import data from range B4:E100 from sheet1.

### Importing Data from Excel based on Named Range
- Range Name: In MS Excel, it is a name that represents a cell, range of cells. You can create your own defined name.
- Creating a range name is very simple. Select a cell or range of cells and Click on the Name box above Column A and Type any name you want and Press Enter.
- Creating a range name is very simple. Select a cell or range of cells and Click on the Name box above Column A and Tye any name you want and Press Enter.

- In the example below, Range A1:C10 is selected and then type Info in the name box and Press Enter.
![](Resources/ExcelImport9.JPG)
- RANGE="Info" tells SAS to import data from excel using user defined named range Info.
![](Resources/ExcelImport10.JPG)

### Rename Columns while Importing
The variable names can be renamed using RENAME= option next to OUT= option.
![](Resources/ExcelImport11.JPG)

### Importing an Excel File from Website into SAS
![](Resources/ExcelImport12.JPG)
- SAS provides a method for extracting data from web pages by procedure named PROC HTTP.
- This method makes it easy to read data from web pages.
- In this case, variable name starts from row number 3 in datafile and data values start from row4 onwards.
- To import CSV file from website, you just need to change the DBMS=XLS to DBMS=CSV.

## How to Import CSV Files into SAS
This tutorial explains how to import CSV files into SAS, along with examples.

### Syntax to import CSV file into SAS
You can use PROC IMPORT to import a CSV files into SAS. The syntax of PROC IMPORT is as follows:
![](Resources/CSVImport3.JPG)
- OUT: Specify name of the dataset to be imported into SAS
- DATAFILE: File location of CSV file which you want to import
- DMBS: Specify CSV Format
- REPLACE: Optional argument. If the file already exists, replace it.
- GETNAMES: Optional argument. By default, it takes first row as variable names. If the file doesn't have a header,set GETNAMES=NO.

### Example 1: Import Data from CSV File into SAS
- Suppose you have data in CSV file named customers.csv. You can import it into SAS using the code below.
![](Resources/CSVImport4.JPG)
- The code above uses the PROC IMPORT procedure in SAS to import a CSV file located at "/home/deepanshu88us0/mydata/customers.csv".
- The imported data will be stored in a dataset named "newdata".
- The DBMS option is set to CSV, telling SAS the file format is CSV.
- The REPLACE option is specified, which means that if a dataset with the same name already exists, it will be replaced.
- The GETNAMES option is set to YES, indicating that the first row of the CSV file contains variable names. It is by default so you can exclude this option if you want.
- To view and print the dataset, you can use proc print data=newdata;

### Example 2: Import Data from CSV File without Header into SAS
- If your CSV file does not have header, you can use GETNAMES=NO option in PROC IMPORT.
![](Resources/CSVImport5.JPG)

## DATALINES Statements
The DATALINES statement in SAS is used to create a dataset. You can input data directly into a SAS program using the DATALINES statement, without the need for an external data file.

### Syntax of DATALINES statement
The syntax of DATALINES statement is as follows.

![](Resources/DatalinesImport.JPG)

1. DATA new_dataset;: This line starts the DATA step and defines a new dataset named new_dataset.
2. INPUT variable1 $ variable2 variable3;: This line specifies the variable names and their data types. In this case, variable1 is a character variable, while variable2 and variable3 are numeric variables.
3. DATALINES;: This line indicates the start of the data section.
4. The lines following DATALINES; represent the data values for each variable. Each line represents one observation, and the values for each variable are separated by spaces.
5. RUN;: This line marks the end of the DATA step and executes it, creating the "new_dataset" dataset.
6. Note: A dollar sign $ following a variable name indicates that the variable is a character variable.

- Use PROC PRINT procedure to print the dataset
![](Resources/DatalinesImport2.JPG)

### How to read a large character variable in SAS
By default, the length of a character variable is set at the first occurrence of the variable. If you want to read a large character variable, you can use colon modifier : which tells SAS to read variable until there is a space or other delimiter. The $20. indicates the length of the character variable.
![](Resources/DatalinesImport3.JPG)

## SAS CARDS STATEMENT: LEARN WITH EXAMPLES
The CARDS statement in SAS is used to create a dataset. You can directly enter data into a SAS program using the CARDS statement, without the need for an external data file.

The CARDS statement is an alternative to the DATALINES statement and serves the same purpose. It is used in the same way as DATALINES to specify inline data within the SAS program.

### Syntax of CARDS statement
The syntax of CARDS statement is as follows.
![](Resources/DatalinesImport4.JPG)
1. DATA new_dataset;: Starts the DATA step and defines a new dataset named new_dataset.
2. INPUT variable1 $ variable2 variable3;: Specifies the variable names and their data types. In this case, variable1 is a character variable, while variable2 and variable3 are numeric variables.
3. CARDS;: Indicates the start of the data section.
4. The lines following CARDS; are the data values for each variable. Each line represents one observation, and the values for each variable are separated by spaces.
5. RUN;: marks the end of the DATA step and executes it, creating the "new_dataset" dataset.

### Additional Raw Data Import Info
For more info on reading raw data into SAS, such as characters variables of varying length, visit https://www.listendata.com/p/sas-tutorials.html, or google it.

## How to Export Data
The following tutorials explain various ways to export SAS data.

## PROC EXPORT: Practical Guide
PROC EXPORT is used to export SAS datasets to external files in various different formats.

### PROC EXPORT Syntax
Below is the syntax for PROC EXPORT:

![](Resources/PROCExport.JPG)

- Explanation of PROC EXPORT Syntax
- data=sas-dataset-name: Name of SAS dataset you want to export.
- outfile: File location where you want to save file.
- dbms: File format to use for exported file.
- replace: Replaces the exported file if it already exists. It is optional argument.

You can use the following DBMS options to export data to different file formats:
- Specify dbms=XLSX to export data as an Excel file.
- Specify dbms=CSV to export data as a CSV file.
- Specify dbms=TAB to export data as a Text file.
- Specify dbms=SAV to export data as a SPSS file.
- Specify dbms=DTA to export data as a Stata file.
- Specify dbms=ACCESSCS to export data as a MS Access file.

### How to Export SAS Data to Excel File
