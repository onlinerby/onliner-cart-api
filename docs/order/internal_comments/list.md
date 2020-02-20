## Получить список внутренних комментариев для магазина по заказу

### GET /orders/{orderKey}/shop-comments

### Пример запроса

```http
GET /orders/1A4E94/shop-comments
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```

### Пример ответа

```http request
HTTP/2 200 OK
Content-Type: application/json; charset=utf-8
```
```json
{
    "internal_comments" : [
        {
            "id": 1,
            "user_login": "User1",
            "comment": "Текст комментария",
            "created_at": "2020-01-01 00:00:00"
        },
        {
            "id": 2,
            "user_login": "User2",
            "comment": "Текст комментария 2",
            "created_at": "2020-01-02 00:00:00"
        }
    ]
}
```

### Описание полей ответа

|Параметр|Тип|Описание|
|---|---|---|
|internal_comments|array|список комментариев для магазина|
|internal_comments.*.id|int|id комментария|
|internal_comments.*.user_login|string|Логин пользователя, автора комментария|
|internal_comments.*.comment|string|текст комментария для магазина|
|internal_comments.*.created_at|string|дата и время создания комментария|

### Ответ при попытке получить комментарии неавторизованным пользователем или без необходимых прав

```http
HTTP/2 403 Forbidden
```
```json
{
    "message": "Access denied"
}
```
