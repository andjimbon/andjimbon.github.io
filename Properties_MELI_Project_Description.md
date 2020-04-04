## Creating a structured table from Mercadolibre publications

**Project description:** The main objective of this project, is to calculate the average price of new printed books and ebooks in Colombia. To do so, it takes as reference one of the best library online in Colombia - [Libreria de la U](https://www.libreriadelau.com/)- to scrape thousends of book items.

Scraping Date: March 2020

### 1. Pagination

This website doesn't have pagination, instead it has a button at the end of the page to load new items. To scrape the book items, we need to load the data into a json format and iterate over it.

```javascript
try:
            data = json.loads(response.text)
        
            if len(data)==0:
                pass

            else:
                for i in data:
                    try: autor.append(i['Autor'][0])
                    except Exception: autor.append(None)

                    try: editorial.append(i['Editorial'][0])
                    except Exception: editorial.append(None)
                    
                   ...
```

### 1. Data Analysis

With the price of the books, we can plot a Distributionn price and plot the price by Category of books:

<img src="images/Distribution.JPG?raw=true"/>

<img src="images/Category.PNG?raw=true"/>
