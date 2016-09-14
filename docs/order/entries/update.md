## Изменить позицию в заказе

### PATCH /orders/{orderId}/entries/{entryId}

В данный момент доступно только изменение количества покупаемых товаров в рамках одного ценового предложения.
Изменять позицию можно только у заказов, находящихся в статусе "Новый".

### Параметры запроса

|Параметр|Тип|Описание|
|---|---|---|
|quantity|integer|Количество позиций в заказе|

### Пример запроса

```http
PATCH /orders/qz2wa/entries/1
Authorization: bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```
```json
{
    "quantity": 10
}
```

### Пример ответа

```json
{
    "quantity": 10
}
```

### Oтвет при попытке изменить несуществующий заказ

```http
HTTP/1.1 404 Not Found
```
```json
{
    "message": "Order %ORDER_ID% not found"
}
```

### Ответ при невалидном запросе

```http
HTTP/1.1 422 Unprocessable Entity
Content-Type: application/json; charset=utf-8
```
```json
{
    "message": "Validation failed",
    "errors": {
        "quantity": [
            "Укажите количество позиций"
        ]
    }
}
```

### Возможные ошибки для полей:

|Параметр|Ошибки|
|---|---|
|quantity|Укажите количество позиций|
|quantity|Должно быть не менее 1 позиции|
|quantity|Можно добавить не более 10 одинаковых позиций|
|quantity|Значение поля должно быть целым числом|
|status|Недопустимый статус заказа|
