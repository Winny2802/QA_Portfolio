## UX не отрабатывает невалидную Due Date

### Steps:
1. Создать задачу и заполнить строку (Due Date) значением с невалидной датой (например 31.06.2026/ 29.02.2026 и тд)
2. Нажать Create

### Actual Result 
Ничего не происходит - задача не сохраняется, сообщения от UX нет

В консоли: Uncaught RangeError: Invalid time value
    at Date.toISOString

### Expected Result
UX отрисовывает сообщение об ошибке - введите корректную дату

### Screenshots

