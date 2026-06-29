## Ошибка валидации поля **name** в API

### Summary

API позволяет создать задачу с пустым названием, несмотря на валидацию в веб-интерфейсе

### Preconditions

Пользователь авторизован

### Steps

1. Отправить POST-запрос на `/api/v1/chores/`.
2. Передать тело запроса:

```json
{
    "name": " ",
    "frequencyType": "once",
    "frequency": 1
}
```

### Expected Result

API возвращает ошибку валидации (например, 400 Bad Request) с сообщением о том, что поле **name** является обязательным.

### Actual Result

API возвращает **200 OK** и успешно создаёт задачу с пустым названием.

### Additional information

Через веб-интерфейс Donetick создать задачу без названия невозможно — отображается ошибка валидации. Таким образом, валидация между frontend и backend работает несогласованно

### Severity

Medium

### Priority

Medium

---

## API некорректно обрабатывает просмотр удаленной задачи

### Summary

API возвращает 500 Internal Server Error при запросе удалённой задачи.

### Preconditions

Пользователь авторизован

### Steps

1. Создать новую задачу.
2. Запомнить её идентификатор.
3. Удалить задачу.
4. Выполнить GET-запрос к `/api/v1/chores/{id}`.

### Expected Result

API возвращает **404 Not Found** с сообщением о том, что задача не найдена.

### Actual Result

API возвращает:

HTTP Status:

```
500 Internal Server Error
```

Тело ответа:

```json
{
    "error": "Failed to fetch chore details"
}
```

### Additional information

Отсутствие удалённого ресурса является ожидаемой ситуацией и не должно приводить к внутренней ошибке сервера.

### Severity

Medium

### Priority

Medium

---

## API принимает отрицательное значение поля priority без сообщения об ошибке

### Preconditions

Пользователь авторизован

### Steps

1. Отправить POST-запрос на `/api/v1/chores/`.
2. Передать:

```json
{
    "name": "API Test",
    "priority": -5,
    "frequencyType": "once",
    "frequency": 1
}
```

### Expected Result

API отклоняет запрос с ошибкой валидации (400 Bad Request) либо явно сообщает о недопустимом значении поля

### Actual Result

Запрос успешно выполняется (200 OK), задача создаётся, однако значение приоритета игнорируется и сохраняется как значение по умолчанию

### Additional information

API не уведомляет клиента о том, что переданное значение является некорректным, что может привести к неожиданному поведению

### Severity

Low

### Priority

Low

---

## API не валидирует допустимые значения поля frequencyType

### Preconditions

Пользователь авторизован

### Steps

1. Отправить POST-запрос на `/api/v1/chores/`.
2. Передать:

```json
{
    "name": "API Test",
    "frequencyType": "abracadabra",
    "frequency": 1
}
```

### Expected Result

API возвращает ошибку валидации (400 Bad Request), так как значение поля **frequencyType** не входит в перечень допустимых.

### Actual Result

API возвращает **200 OK** и успешно создаёт задачу.

### Additional information

В веб-интерфейсе пользователь может выбрать только допустимые варианты периодичности. API не выполняет аналогичную проверку, что свидетельствует о несогласованности валидации между frontend и backend.

### Severity

Medium

### Priority

Medium

