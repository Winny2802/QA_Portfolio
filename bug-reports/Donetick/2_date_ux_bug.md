## UI не отрабатывает невалидную Due Date

### Steps:
1. Создать задачу и заполнить строку (Due Date) значением с несуществующей датой (например 31.06.2026/ 29.02.2026 и тд)
2. Нажать Create

### Actual Result 
Ничего не происходит - задача не сохраняется, сообщения от UI нет

В консоли: Uncaught RangeError: Invalid time value
    at Date.toISOString

![Header](https://github.com/Winny2802/QA_Portfolio/blob/main/assets/duedate%20bug.png)


### Expected Result
Пользователю выводится сообщение об ошибке - ввода некорректной (несуществующей) даты