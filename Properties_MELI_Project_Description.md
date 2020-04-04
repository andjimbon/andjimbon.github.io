## Real state Market in Colombia

**Project description:** With this code you will be abble to compare market prices (sell/rent) from diferent neighboorhoods or cities in Colombia, and get the information from each property publication (Rooms, bathrooms, M2, House Expenses, etc.)

Scrape data from [Mercadolibre](https://www.mercadolibre.com.co/inmuebles) and create a database with property items and their Google geogrpahical location. 


### 1. Define locations

Enter the link locations inside the "start_request" function by filtering in the web page 

```javascript
def start_requests(self):
        yield scrapy.Request(
            'https://listado.mercadolibre.com.co/inmuebles/apartamentos/venta/bogota-dc/suba/acacias/_DisplayType_LF',
            self.parse)
```

### 2. Run Spider

Run the script and automatically the file will be save in the folder where the script is. Modify the file's name in the "custom_settings":

```javascript
 custom_settings = {
        'FEED_URI': 'inmuebles_' + str(datetime.today().strftime('%Y-%m-%d')) + '.csv',
        'FEED_FORMAT': 'csv',
        'FEED_EXPORTERS': {
            'json': 'scrapy.exporters.CsvItemExporter',
        }
```
Once finished the process, you'll receive and email with the stats:

<img src="images/scrape.PNG?raw=true"/>

### 4. Table

Here is an example that shows the structured data:

<img src="images/Table.png?raw=true"/>

