## Ошибка при попытке skip задачи без due date

### Summary 


### Steps:
1. Создать задачу без конкретного срока (поле due date оставить пустым)
2. Нажать на задачу, выполнить действие «Skip»

### Actual Result 
Отображается белый экран.
В консоли DevTools: POST /api/v1/chores/{id}/skip 
возвращает: 502 Bad Gateway.
Затем фронтенд выдает: TypeError: не удалось получить данные за которой следует минимизированная ошибка React #31 

### Expected Result
Действие должно либо успешно выполняться, либо завершаться с ошибкой без сбоев в работе пользовательского интерфейса 

### Screenshots

![Header](https://github.com/Winny2802/QA_Portfolio/blob/main/assets/баг%20skip%201.png)

![Header](https://github.com/Winny2802/QA_Portfolio/blob/main/assets/баг%20skip%202.png)
