## Project
The aim of this project is develop a 3-statement model completely inputting historical data and assumptions to project out financial statements from **APPLE INC.** using Python and Google Sheets.

**Advantages** of using Python & GS:

* There's no need to input historical data mannually. This code uses Scrapy and BS4 to read Financial Statements from SEC
* Spreadsheet cells are linked. This model is robust, so any change in key variables will modify the output
* Iterative Calcultaion. With GS, Pandas static dataframes will never be a problem again
* There are unique variables (named ranges): Calculation in cells shows the name of the variables, so it's really easy to follow the financial modelling

### Google Spreadsheet
[Click Here ](https://docs.google.com/spreadsheets/d/1oLiIFFNvMJMZeQ2VnxjL87y4xQOg0CwDKgdUCr-ERFo/edit?usp=sharing) to see spreadsheet

### Connecting to Google Sheets
![](/images/auth.PNG)

### Contents of the project
![](/images/contents.PNG)

### Automatic generation of Ranges
![](/images/gif4.gif){:height="100%" width="100%"}  

### Selecting Named Ranges
![](/images/ranges.PNG)

### Paste Values and Formulas from Python 
![](/images/gif1.gif){:height="100%" width="100%"}  

![](/images/gif3.gif){:height="100%" width="100%"}  

### Cells contain formulas with the name of the variables
![](/images/cells formula.PNG)

### Balance Check
![](/images/balance.PNG)
