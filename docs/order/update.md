## Изменить заказ

### PATCH /orders/{orderId}

В данный момент доступно только изменение статуса заказа.

Таблица допустимых переходов статусов для магазина:
| Текущий статус заказа | Возможные новые статусы заказа |
| new | confirmed, shop_canceled |
| confirmed | delivered, shop_canceled |

### Параметры запроса

|Параметр|Тип|Описание|
|---|---|---|
|status|string|Статус заказа|

### Пример запроса

```http
PATCH /orders/qz2wa
Authorization: bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```
```json
{
    "status": "confirmed"
}
```

### Пример ответа

```json
{
    "key": "qz2wa",
    "user_id": 1,
    "contact": {
        "name": "Тестовый пользователь",
        "email": "test@onliner.by",
        "phone": "+375291234567"
    },
    "delivery": {
        "city": "Минск",
        "address": "пр-т Дзержинского, 5"
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-20T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "status": "confirmed",
    "positions_count": 2,
    "total_quantity": 3,
    "total_cost": 200000,
    "order_cost": {
        "amount": "20.00",
        "currency": "BYN",
        "converted": {
            "BYN": {
                "amount": "20.00",
                "currency": "BYN"
            },
            "BYR": {
                "amount": "200000",
                "currency": "BYR"
            }
        }
    },
    "comment": "Доставка с 9 до 18"
}
```

### Описание полей ответа

Базовый набор полей заказа + статус заказа <kbd>status</kbd> ([Описание базового набора полей](show.md))

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
        "status": [
            "Укажите статус"
        ]
    }
}
```

### Возможные ошибки для полей:

|Параметр|Ошибки|
|---|---|
|status|Укажите статус|
|status|Значение поля должно быть строкой|
|status|Недопустимый статус заказа|
|status|Недопустимый переход статусов|
