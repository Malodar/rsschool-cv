# Artsiom Kunitsyn

### Contacts
- **Mobile/Viber:** +375 29 3838784
- **Skype:** temi4kunitsyn
- **Email:** kunitsyn-a-v@yandex.ru

### Summary
Since I've opened the world of programming for me, I got a huge stimulus to constantly learn new things, new technologies, new languages. I really enjoy creating new applications and scripts that make something useful for people. I consider this occupation as an artisan work -- you always see the result of what you are doing. And if this result is successful -- this gives me much more enthusiasm to continue my trainings of coding. 

### Skills
- Python:
  - web scraping (requests, Scrapy, Selenium, BeautifulSoup)
  - web automation (Selenium)
  - web application development with Django (basics)
  - file processing (JSON, CSV, XLS, PDF, TXT, etc.)
  - Automated file downloading
- HTML/CSS
- Git
- SQL (basics)

### Code examples
```python
import requests, re, json
from urllib.request import quote
from openpyxl import load_workbook
from bs4 import BeautifulSoup as bs


def read_excel(file):
    wb = load_workbook(file)
    try:
        sheet = wb.active
        raw_names = []
        for row in sheet.iter_rows(min_row=2):
            raw_names.append(str(row[0].value).strip())
        wb.close()
    finally:
        wb.close()
    return raw_names


def get_imdb_data(code):
    url = f'https://www.imdb.com/title/{code}/'
    r = requests.get(url)
    soup = bs(r.text, 'lxml')
    js = json.loads(soup.select_one("script[type='application/ld+json']").get_text())
    director = js['director']['name']
    rating = js["aggregateRating"]['ratingValue']
    vote_count = js["aggregateRating"]['ratingCount']
    actors = ", ".join([i['name'] for i in js['actor']])
    writers = ", ".join([i['name'] for i in js['creator'] if i['@type'] == 'Person'])
    age_rating = js['contentRating']
    data = {
        'director': director,
        'rating': rating,
        'vote_count': vote_count,
        'actors': actors,
        'writers': writers,
        'age_rating': age_rating,
    }
    return data
```

### Experience
All my experience in coding is based on making different tasks as freelancer. My account with some feedbacks from clients can be found here -- [my freelance account](https://www.freelancer.com/u/kunitsynartem?w=f). About 90% of tasks I made are related to web scraping/parsing area, other 10% -- to some boring stuff automation.

### Education
- Belarus State Economic University, 2002-2007, Faculty of International Economic Relations
- Courses:
  - An Introduction to Interactive Programming in Python (Part 1), by Coursera
  - Programming in Python, at Education center of Belhard
  - Web application development with Django, at Education center O.R. Media
  - HTML/CSS, at Education center MyFreedom

### English
I've been learning English during my studies in University. Then I practiced using it while working as procurement manager at different companies (my job was to communicate with suppliers from all over the world). Last 2 years I use English in conversation with my customers, mostly written, but oral as well.