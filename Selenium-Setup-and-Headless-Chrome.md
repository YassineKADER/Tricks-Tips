# Selenium Setup and Headless Chrome
This code snippet demonstrates how to set up Selenium and run headless Chrome using Python. It includes the necessary steps to install dependencies and configure the Selenium driver.
## Installation and Setup
To run this code, follow these steps:
Install the Selenium package:
```
pip install selenium
```
Update the system:
```
apt-get update
```
Install additional dependencies:
```
apt-get install -y wget curl unzip xvfb libxi6 libgconf-2-4
```
Download and extract the latest stable version of ChromeDriver:
```
wget https://chromedriver.storage.googleapis.com/93.0.4577.63/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
chmod +x chromedriver
```
Download and install Chrome:
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
dpkg -i google-chrome-stable_current_amd64.deb
```
# Running Headless Chrome
```
from selenium import webdriver

# Configure the driver to use headless Chrome
options = webdriver.ChromeOptions()
options.add_argument('--headless')
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')
chrome_path = '/usr/local/bin/chromedriver'
driver = webdriver.Chrome(chrome_path, options=options)

# Open Google's homepage
driver.get('https://www.google.com')

# Print the page title
print(driver.title)

# Close the browser
driver.quit()
```
