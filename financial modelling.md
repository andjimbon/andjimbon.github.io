## Project
The aim of this project is develop a 3-statement model completely inputting historical data and assumptions to project out financial statements from **APPLE INC.** using Python and Google Sheets.

**Advantages** of using Python & GS:

* There's no need to input historical data mannually. This code uses **Scrapy** and **BS4** to read **10-K** Financial Statements from [*SEC*](https://www.sec.gov/cgi-bin/viewer?action=view&cik=320193&accession_number=0000320193-18-000145&xbrl_type=v#)
* Spreadsheet cells are **linked**. This model is robust, so any change in key variables will modify the output
* Iterative Calcultaion. With GS, **static dataframes from Pandas** will never be a problem again
* There are unique variables (**named ranges**): Calculation in cells shows the name of the variables, so it's really easy to follow the financial modelling

<p>&nbsp;</p>

### Google Spreadsheet
[Click Here ](https://docs.google.com/spreadsheets/d/1oLiIFFNvMJMZeQ2VnxjL87y4xQOg0CwDKgdUCr-ERFo/edit?usp=sharing) to see spreadsheet

<p>&nbsp;</p>

### Connecting to Google Sheets
![](/images/auth.PNG)
<p>&nbsp;</p>

### Contents of the project
![](/images/contents.PNG)
<p>&nbsp;</p>

### Automatic generation of Ranges
![](/images/gif4.gif){:height="100%" width="100%"}  
<p>&nbsp;</p>

### Selecting Named Ranges
![](/images/ranges.PNG)
<p>&nbsp;</p>

### Paste Values and Formulas from Python 
![](/images/gif1.gif){:height="100%" width="100%"}  

![](/images/gif3.gif){:height="100%" width="100%"}  
<p>&nbsp;</p>

### Cells contain formulas with the name of the variables
![](/images/cells formula.PNG)
<p>&nbsp;</p>

### Balance Check
![](/images/balance.PNG)
