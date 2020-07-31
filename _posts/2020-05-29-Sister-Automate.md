---
layout: post
published: true
title: Sister Automate
date: '2020-07-05'
image: /img/Automate/sister-logo.png
---
Implementasi python programming for automate @ **#4*.

## Automasi Kehadiran Sister Unej

Membuat script untuk automasi kehadiran di sister, hanya jalankan file python.
Penggunaan automasi harus dipantau untuk memastikan tidak ada yang error.

![1](/img/Automate/sister-login.png)



Berikut kode yang saya buat untuk automasi Sister Unej.

```
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time
import random
import sys

class UnejLog:

    def __init__(self, username, password):
        self.username = username
        self.password = password
        #app for automate with chrome
        self.driver = webdriver.Chrome('C:/Users/Phanatagama/Downloads/chromedriver.exe')

        #close browser
    def closeBrowser(self):
        self.driver.close()

        #login sister dashboard
    def login(self):
        driver = self.driver
        #visit login form and redirect to mmp
        driver.get("https://sso.unej.ac.id/cas/login?service=https%3A%2F%2Fmmp.unej.ac.id%2Flogin%2Findex.php")
        time.sleep(2)
        #put the username & password to field
        user_name_elem = driver.find_element_by_xpath("//input[@name='username']") #//input[@name='username']
        user_name_elem.clear()
        user_name_elem.send_keys(self.username)
        passworword_elem = driver.find_element_by_xpath("//input[@name='password']")	#//input[@name='password']
        passworword_elem.clear()
        passworword_elem.send_keys(self.password)
        passworword_elem.send_keys(Keys.RETURN)
        time.sleep(2)

    #present in mmp
    def attendance(self):
    	time.sleep(2)
    	driver = self.driver
    	click_button = lambda: driver.find_element_by_xpath('//a[@data-type="event"]').click()	#//span[@aria-label="Like"] #/html/body/div[1]/section/main/section/div[1]/div[2]/div/article[1]/div[2]/section[1]/span[1]/button/svg/path
    	click_button()
    	time.sleep(5)
    	Present_button = driver.find_element_by_xpath('/html/body/div[4]/div/div[3]/a')
    	Present_button.click()

#main program
if __name__ == "__main__":

    #put your account here
    username = "put your username"
    password = "put your pass"

    sister = UnejLog(username, password)
    sister.login()
    sister.attendance()
```

Sebelum menjalankan script diatas jangan lupa untuk mengubah beberapa parameter seperti username dan password dan juga lokasi file chromedriver.exe
Mungkin juga memerlukan tambahan/pendukung `(chardet,certifi, urllib,dll)`
