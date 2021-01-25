from selenium import webdriver
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
import smtplib
import os
import time

#load the webpage
browser = webdriver.Chrome("path to chrome driver (e.g. usr/local/share/chromedriver)")
browser.get("AMAZON-PS5-URL")

#refresh the page until the buy button becomes available
while True:
	try:
		Buy = browser.find_element_by_id("buy-now-button")
		if Buy.is_enabled():
			break
		else:
			stock += 1
			time.sleep(30)
	except:
		stock += 1
		time.sleep(30)
	

	browser.refresh()

#create the message for the email
msg = MIMEMultipart()
message = "AMAZON LINK" #you can change this to whatever you want
password = "[your password]"
msg['From'] = '[your email]'
msg['To'] = '[targets email]' #set this equal to ['From'] email to send yourself the stock alert
#msg['To2'] = 'additional email' to add another email
msg['Subject'] = "PS5 RESTOCK"
msg.attach(MIMEText(message, 'plain'))

#send email
server.sendmail(msg['From'], msg['To'], msg.as_string())
#server.sendmail(msg['From'], msg['To2'], msg.as_string()) (only if you have muliple targets)
server.quit()

print ("successfully sent email to: %s" % (msg['To']))
print ("successfully sent email to: %s" % (msg['To2']))
