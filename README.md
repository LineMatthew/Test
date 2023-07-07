# Test
import requests
from requests import HTTPError

def send_request(status_code=200):
    response = requests.get("https://httpstat.us/%d" % status_code)
    response.raise_for_status()
    return response.status_code

response_code = None
try:
    while True:
        try:
            code = int(input("Введите код http для проверки "))
            break
        except ValueError as ex:
            print(f"Вы ввели некорректные данные \n \nВведите, пожалуйста, число")
    response_code = send_request(code)
except HTTPError as ex:
    print("\nПроизошла ошибка HTTP кода, при отправке запроса: %s" % str(ex))
    response_code = ex.response.status_code
finally:
    print(f'\nПолученный код: {response_code}')
