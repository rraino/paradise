# paradise
#!/usr/bin/env python
# -*- coding:utf-8 -*-

from selenium import webdriver
import datetime
import time

driver = webdriver.Firefox()
# http://gate.jd.com/InitCart.aspx?pid=4993737&pcount=1&ptype=1

def login(username, password):
    driver.get("https://passport.jd.com/new/login.aspx")
    time.sleep(2)
    driver.find_element_by_link_text("账户登录").click()
    driver.find_element_by_name("loginname").send_keys("")
    driver.find_element_by_name("nloginpwd").send_keys("")
    driver.find_element_by_id("loginsubmit").click()
    time.sleep(3)
    driver.get("https://cart.jd.com/cart.action")
    time.sleep(3)
    driver.find_element_by_link_text("去结算").click()
    now = datetime.datetime.now()
    now_time = now.strftime('%Y-%m-%d %H:%M:%S')
    print(now.strftime('%Y-%m-%d %H:%M:%S'))
    print('login success!')

def buy_on_time(buytime):
    while True:
        now = datetime.datetime.now()
        if now.strftime('%Y-%m-%d %H:%M:%S') == buytime:
            driver.find_element_by_name('checkShop').click()
            driver.find_element_by_id('order-submit').click()
            time.sleep(0.5)
            print(now.strftime('%Y-%m-%d %H:%M:%S'))
            print('purchase success')
        time.sleep(0.5)

login('your_jd_username', 'your_jd_password')
buy_on_time('2017-12-26 13:29:01')
