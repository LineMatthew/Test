# Test
while True:
    try:
        code = int(input("Введите код http для проверки "))
        break
    except ValueError as ex:
        print('You have entered incorrect value')
