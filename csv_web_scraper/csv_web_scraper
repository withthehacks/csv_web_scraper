from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import csv
import pandas as pd
import time

option = webdriver.ChromeOptions()
option.add_argument('headless')
driver = webdriver.Chrome(options=option)

col_list = ["id"]
df = pd.read_csv(" *insert path for file here* ", usecols=col_list) 
#print(df)
df_no_index = df.to_string(index = False, header=False).split("\n")
df_split_rows = [",".join(ele.split()) for ele in df_no_index]
plugin_ids = len(df_split_rows)
print(df_split_rows)

# url to webscrap
url = " "

count = 0

new_url = (url + str(df_split_rows[count]))

while len(df_split_rows) <= plugin_ids:
    new_url = (url + str(df_split_rows[count]))
    count = count + 1
    #time.sleep(1)
    driver.get(new_url)
    try: 
        cves = driver.find_elements_by_xpath("//*[contains(text(), ' *ENTER TEXT TO SEARCH FOR* ')]")
        for cve in cves:
            print(str(df_split_rows[count - 1]), cve.text)
    except:
        print('Not Found')
