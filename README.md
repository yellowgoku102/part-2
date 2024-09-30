# part-2


from bs4 import BeautifulSoup

import os
d = {'title': [1, 2], 'price': [3, 4], "link" :[1,2]}
for file in os.listdir("data"):
    with open(f"data/{file}") as f:
        html_doc = f.read()
    soup = BeautifulSoup(html_doc, 'html.parser')
    t = soup.find('href')
    title = t.get_text()
    print (title)
    break
