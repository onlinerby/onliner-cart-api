## Получить список доступных причин для отмены заказа магазином

### GET /resources/shop-cancel-reasons

Запрос не требует авторизации.

### Пример запроса

```http
GET /resources/shop-cancel-reasons
Accept: application/json
```

### Пример ответа

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```json
[
    {
        "id": 1,
        "text": "Товара нет в наличии",
        "comment_required": false
    }
]
```

### Описание полей ответа

|Параметр|Тип|Описание|
|---|---|---|
|id|integer|Идентификатор причины, который нужно будет передать при отмене заказа|
|text|string|Текст причины|
|comment_required|boolean|Флаг, указывающий необходимо ли передавать `reason.comment` при отмене заказа с указанием причины|
