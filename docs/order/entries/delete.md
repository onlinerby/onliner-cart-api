## Удалить позицию из заказа

### DELETE /orders/{orderId}/entries/{entryId}

Нельзя удалить последнюю позицию из заказа
Удалять можно позиции только у заказов в статусе "Новый"

### Пример запроса

```http
DELETE /orders/qz2wa/entries/1
Authorization: bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```

### Пример ответа

```http
HTTP/1.1 204 No Content
```

### Oтвет при попытке изменить несуществующий заказ

```http
HTTP/1.1 404 Not Found
```
```json
{
    "message": "Order qz2wa not found"
}
```

### Ответ при попытке удалить позицию из заказа в другом статусе

```http
HTTP/1.1 422 Unprocessable Entity
Content-Type: application/json; charset=utf-8
```
```json
{
    "message": "Validation failed",
    "errors": {
        "status": [
            "Недопустимый статус заказа"
        ]
    }
}
```

### Ответ при попытке удалить последнюю позицию из заказа

```http
HTTP/1.1 422 Unprocessable Entity
Content-Type: application/json; charset=utf-8
```
```json
{
    "message": "Нельзя удалить последнюю позицию из заказа"
}
```


### Возможные ошибки для полей:

|Параметр|Ошибки|
|---|---|
|status|Недопустимый статус заказа|
