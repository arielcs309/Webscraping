
# Webscraping a Website
I did a Webscraping on a Website that I love of hair products. I used beautifulSoup package to get the information I needed.

## Getting on the website
This step involving setting the cabecalho variable as headers and passing it to the requests.get()
 function is crucial for web scraping, especially when you're making requests to websites.

``` bash
#important to show the website it isn't a robot
cabecalho = {'user-agent' : 'Mozilla/5.0'}
site = requests.get('https://www.belezanaweb.com.br/cabelos/tipos-de-cabelo/cacheados-ou-ondulados/',
                   headers = cabecalho)
site.text
```
## HTML Parser
Using the HTML parser provided by BeautifulSoup ('html.parser') is essential
for converting raw HTML into a structured format that can be easily navigated, 
searched, and manipulated, thus facilitating effective web scraping and data extraction tasks.
``` bash
#showing the html more organized
soup_2 = BeautifulSoup(soup_1, 'html.parser')
soup_2
```
## Cleaning the HTML 
Finding a pattern to get all the product names. 
In BeautifulSoup, attrs is short for "attributes," and it's used to specify 
additional attributes that you want to match when searching for elements in the parsed HTML tree.
The find_all() method is used to locate all <span> elements that have a class attribute equal to 'showcase-item-brand'.
``` bash
lista_item = soup_2.find_all('span', attrs ={'class':'showcase-item-brand'})                         
lista_item
```
## Transforming into a DF

``` bash
produto_cabelo = []
for produto, preco in zip (lista_item, lista_preco):
    nome_item = produto.contents[0].text
    valor_item = preco.contents[0].text
    valor_item = valor_item.replace('R$',"").replace(",",".").replace(" ","")
    nome_item = nome_item.replace('\n', '')
    
    produto_cabelo.append((nome_item, valor_item))

produto_cabelo
```
## Before 
![b4](https://github.com/arielcs309/Webscraping/blob/main/Before.png)
## During 
![during](https://github.com/arielcs309/Webscraping/blob/main/during.png)
## After
![DF](https://github.com/arielcs309/Webscraping/blob/main/Dataframe.png)
## Boxplot
![BP](https://github.com/arielcs309/Webscraping/blob/main/BOXPLOT.png)

# Author
Ariel Sousa. 
See my [Linkedin](https://www.linkedin.com/in/ariel-candido-22684578/) and my [Kaggle](https://www.kaggle.com/arielsousa)


