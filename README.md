# part-2



from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
query = "laptop"
file =0

for i in range(1,20):
    driver.get(f"https://www.flipkart.com/search?q={query}&page+=1&otracker=search&otracker1=search&marketplace=FLIPKART&as-show=on&as=off&page={i}")
    
    

    elems = driver.find_elements(By.CLASS_NAME, "_75nlfW")
    print(f"{len(elems)} items found")
    for elem in elems:
        d = elem.get_attribute("outerHTML")
        with open(f"data/{query}_{file}.html", "w", encoding = "utf-8") as f:
            f.write(d)
            file += 1


    # print(elem.get_attribute("outerHTML"))


    time.sleep(4)

driver.close()

#in diffrant .py file
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
