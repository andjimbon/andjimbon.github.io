## what is the average price of printed books and eBooks in Colombian Market?

**Project description:** The main objective of this project, is to calculate the average price of new printed books and ebooks in Colombia. To do so, it takes as reference one of the best library online in Colombia - Libreria de la U (https://www.libreriadelau.com/) - to scrape thousends of book items.

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

### 1. Loading data in Pandas

Load data into a structured table

```javascript
f = pd.DataFrame(data=[autor,editorial,edicion,pag,ISBN,tipo,formato,titulo,categoria,precio,file,size,peso,tamano,acabado,link], index=None)
df=f.transpose()
df.columns=['Autor','Editorial','Edicion','Paginas','ISBN','Tipo','Formato','Titulo','Categoria','Precio','File','Size-MB','Peso','Tamaño','Acabado','Link']
```

### 1. Data Analysis

Here is an example what you can do with Pandas:
