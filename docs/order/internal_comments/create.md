## Создать внутренний комментарий для магазина

### POST /orders/{order_key}/shop-comments

### Параметры запроса

|Параметр|Тип|Описание|
|---|---|---|
|comment|string|Текст комментария|

### Пример запроса

```http
POST /orders/1A4E94/shop-comments
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```
```json
{
  "comment": "Текст комментария"
}
```

### Пример ответа

```json
{
    "id": 1,
    "user_login": "Kate",
    "comment": "Текст комментария",
    "created_at": "2020-01-01 00:00:00"
}
```

### Ответ при запросе от пользователя без необходимых прав

```http
HTTP/2 403 Forbidden
```
```json
{
    "message": "Access denied"
}
```

### Возможные ошибки:

|Ошибки|
|---|
|Access denied<br>Invalid credentials|

### Ответ при невалидном запросе

```http
HTTP/2 422 Unprocessable Entity
Content-Type: application/json; charset=utf-8
```
```json
{
    "message": "Validation failed",
    "errors": {
        "comment": [
            "Поле обязательно для заполнения"
        ]
    }
}
```

### Возможные ошибки для полей:

|Параметр|Ошибки|
|---|---|
|comment|Значение поля должно быть строкой<br>Поле обязательно для заполнения<br>Максимум 255 симоволов|

### Ответ при возникновении логических ошибок

```http
HTTP/2 422 Unprocessable Entity
Content-Type: application/json; charset=utf-8
```
```json
{
    "message": "Добавлено максимальное количество комментариев"
}
```

### Возможные ошибки
|Текст ошибки|
|---|
|Добавлено максимальное количество комментариев|
|Невозможно добавить комментарий к заказу|
