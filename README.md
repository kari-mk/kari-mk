
# PORTFOLIO
## Сайт "Книгарня Є"
### :white_check_mark: [CHECKLIST](https://docs.google.com/spreadsheets/d/15rwsFT-eN2xsFHd1iTMjEu-pdFwzt4YH/edit?usp=drive_link&ouid=105481740879973415403&rtpof=true&sd=true) 
### :memo: [TEST CASES](https://docs.google.com/document/d/1eEU6IAqchAW9SRXQsSGvxSDHjCSm4kY_/edit?usp=drive_link&ouid=105481740879973415403&rtpof=true&sd=true)
### :rotating_light: [BUG REPORTS](https://docs.google.com/document/d/1oMP1t3MqMKWisq-lP89qHE_OVGoRXxwyQSZ5xhWfF8s/edit?usp=drive_link)
## API restful-booker
### :technologist: [API TESTING] 
You can download this Postman collection [here](https://github.com/kari-mk/postman/blob/main/Booking.postman_collection.json)
1. CreateToken - Creates a new auth token to use for access to the PUT and DELETE /booking
```
https://restful-booker.herokuapp.com/auth
```
Request body:
 ```JSON
{
    "username": "admin",
    "password": "password123"
}
```
Response:
```JSON
{
    "token": "b67cb4a7b057b74"
}
```
![image](https://github.com/kari-mk/kari-mk/assets/152392473/8a0fd1ad-7f0c-4010-8211-d4c76a2db217)


2. CreateBooking - Creates a new booking in the API
```
https://restful-booker.herokuapp.com/booking
```
Request body:
 ```JSON
{
    "firstname" : "Jim",
    "lastname" : "Brown",
    "totalprice" : 111,
    "depositpaid" : true,
    "bookingdates" : {
        "checkin" : "2023-12-01",
        "checkout" : "2024-01-01"
    },
    "additionalneeds" : "Breakfast"
}
```
Response:
```JSON
{
    "bookingid": 1127,
    "booking": {
        "firstname": "Jim",
        "lastname": "Brown",
        "totalprice": 111,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2023-12-01",
            "checkout": "2024-01-01"
        },
        "additionalneeds": "Breakfast"
    }
}
```
![image](https://github.com/kari-mk/kari-mk/assets/152392473/036c53a3-5284-4ba1-8599-b403a5338a1f)

3. UpdateBooking - Updates a current booking
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Request body:
 ```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Breakfast"
}
```
Response:
```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Breakfast"
}
```
![image](https://github.com/kari-mk/kari-mk/assets/152392473/202dda7d-2cab-43a4-a880-7adb8bd9c152)

4. GetBooking - Returns a specific booking based on the booking id provided
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Response:
```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Breakfast"
}
```
![image](https://github.com/kari-mk/kari-mk/assets/152392473/a493e241-c82a-4e05-bfd5-17f35d13f44f)

5. PartialUpdateBooking - Updates a current booking with a partial payload
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Request body:
 ```JSON
{
    "additionalneeds": "Supper"
}
```
Response:
```JSON
{
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 131,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2023-12-01",
        "checkout": "2024-01-15"
    },
    "additionalneeds": "Supper"
}
```
![image](https://github.com/kari-mk/kari-mk/assets/152392473/cc5129fd-ca0b-49c7-86da-33cc6d69f39e)

6. DeleteBooking - Delete a booking with that id.
```
https://restful-booker.herokuapp.com/booking/{{id}}
```
Response:
```JSON
{
    201
}
```
![image](https://github.com/kari-mk/kari-mk/assets/152392473/9fe4ba8d-bfd8-405b-b606-1e37573fd9d1)

## Test automation
### :technologist: [SELENIUM]

Creating a simple positive login test for a login form on testspracticetestautomation.com
![image](https://github.com/kari-mk/kari-mk/assets/152392473/40ff8ca8-15c7-461b-bc02-fa462f1df1da)
```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service as ChromeService
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.by import By
import time


driver = webdriver.Chrome(service=ChromeService(ChromeDriverManager().install()))
driver.get("https://practicetestautomation.com/practice-test-login/")

email = driver.find_element(by=By.ID, value="username")
password = driver.find_element(by=By.ID, value="password")
submit_button = driver.find_element(by=By.ID, value="submit")
successful_login_text = "Logged In Successfully"

email.send_keys("student")
password.send_keys("Password123")
submit_button.click()
get_source = driver.page_source

print(successful_login_text in get_source)

time.sleep(5)
driver.close()
driver.quit()
```
