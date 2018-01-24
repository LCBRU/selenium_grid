# Selenium Grid

## Facilities

This Selenum grid contains one Google Chrome and one Firefox
node for running tests.

## Usage (in Python)

To use the hub connect from python like this:

```python
from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities

TEST_URL = 'https://www.example.com'
SELENIUM_URL = 'http://127.0.0.1:4444/wd/hub'

desired_capabilities = DesiredCapabilities.FIREFOX
# desired_capabilities = DesiredCapabilities.CHROME

driver = webdriver.Remote(
    command_executor=SELENIUM_URL
    desired_capabilities=desired_capabilities
)
driver.implicitly_wait(10)

driver.get(TEST_URL)

...

driver.quit()

```

## Remote Connection

To utilise the Selenium grid from a remote machine, first
create an SSH tunnel to the Selenium grid server.

```bash
ssh uhlbriccsapp02 -L 4444:127.0.0.1:4444 -N
```

## Certificate Errors

If the target site has a self-signed certiifcate, and hence would
produce a certificate error, you will have to define the chrome
browser in the `desired_capabilities`.
