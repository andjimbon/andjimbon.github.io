## what is the average price of printed books and eBooks in Colombian Market?

**Project description:** The main objective of this project, is to calculate the average price of new printed books and ebooks in Colombia. To do so, it takes as reference one of the best library online in Colombia - Libreria de la U (https://www.libreriadelau.com/) - to scrape thousends of book items.

Scraping Date: March 2020

### 1. Pagination

This website doesn't have pagination and the request method is GET. To scrape the book items, we need to load the data into a json format and iterate over the pages

```javascript
data = json.loads(response.text)
}
```
