## Изменить заказ

### PATCH /orders/{orderId}

Таблица допустимых переходов для заказов, оформленных по новому сценарию:

| Текущий статус заказа | Возможные новые статусы заказа |
|---|---|
| `new` | `processing`, `shop_canceled` |
| `processing` | `confirmed`, `shop_canceled` |
| `confirmed` | `shipping`, `shop_canceled` |
| `shipping` | `delivered`, `shop_canceled` |

Для новых заказов доступна возможность уменьшения стоимости доставки заказа, до момента передачи в доставку (пока заказ находится в статусах `processing`, `confirmed`).

В момент передачи заказа в доставку для новых заказов можно указать комментарий к доставке, который увидит покупатель.

### Параметры запроса

|Параметр|Тип|Описание|
|---|---|---|
|status|string|Статус заказа|
|reason|object|Причина изменения статуса|
|reason.id|integer|ID причины изменения статуса. Обязательное при отмене заказа магазином|
|reason.comment|string|Описание причины. Опциональное|
|delivery_price|object|Новая стоимость доставки заказа|
|delivery_price.amount|string|Новое значение стоимости доставки заказа (копейки обязательно передаются двумя цифрами после точки)|
|delivery_price.currency|string|Валюта нового значения стоимости доставки (доступно только `BYN`)|
|delivery_comment|string|Комментарий к доставке для пользователя. Опциональное. Можно передавать только вместе со статусом `shipping`|

### Пример запроса

```http
PATCH /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```
```json
{
    "status": "confirmed"
}
```

### Пример отмены заказа магазином

```http
PATCH /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```
```json
{
    "status": "shop_canceled",
    "reason": {
        "id": 1,
        "comment": "товара нет в наличии"
    }
}
```

### Пример запроса на изменение стоимости доставки

```http
PATCH /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```
```json
{
    "delivery_price": {
        "amount": "1.00",
        "currency": "BYN"
    }
}
```

### Пример запроса с указанием комментария к доставке при переводе в статус `shipping`

```http
PATCH /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
Content-Type: application/json; charset=utf-8
```
```json
{
    "status": "shipping",
    "delivery_comment": "Курьер будет у вас с 15:00 до 18:00"
}
```

### Пример ответа

```json
{
    "key": "qz2wa",
    "promocode": {
        "id": 1,
        "name": "test1"
    },
    "user_id": 1,
    "contact": {
        "name": "Пользователь Тестовый",
        "first_name": "Пользователь",
        "last_name": "Тестовый",
        "email": "test@onliner.by",
        "phone": "+375291234567"
    },
    "delivery": {
        "city": "г. Минск",
        "geo_town_id": 17030,
        "address": "пр-т Дзержинского, д. 55, к. 1a, под. 2, эт. 16, кв. 607",
        "address_fields": {
            "street": "пр-т Дзержинского",
            "building": "55",
            "apartment": "607",
            "block": "1a",
            "entrance": "2",
            "floor": "16",
            "comment": "Рабочий адрес"
        },
        "type": "courier_delivery",
        "price": {
            "amount": "3.00", 
            "currency": "BYN"
        },
        "days": 3,
        "comment": "Курьер прибудет с 17:00 - 21:00",
        "is_fake": false
    },
    "payment": {
        "type": "cash"
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-20T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "is_new_flow": true,
    "status": "confirmed",
    "positions_count": 2,
    "total_quantity": 3,
    "shop_comments_count": 0,
    "order_cost": {
        "amount": "21.00",
        "currency": "BYN"
    },
    "order_price": {
        "amount": "27.00",
        "currency": "BYN"
    },
    "order_discount": {
        "amount": "6.00",
        "currency": "BYN"
    },
    "totals": {
        "delivery": {
            "price": {
                "amount": "2.00",
                "currency": "BYN"
            },
            "discount": null,
            "cost": {
                "amount": "2.00",
                "currency": "BYN"
            }
        },
        "original": {
            "positions": {
                "price": {
                    "amount": "25.00",
                    "currency": "BYN"
                },
                "discount": {
                    "amount": "6.00",
                    "currency": "BYN"
                },
                "cost": {
                    "amount": "19.00",
                    "currency": "BYN"
                }
            },
            "price": {
                "amount": "27.00",
                "currency": "BYN"
            },
            "discount": {
                "amount": "6.00",
                "currency": "BYN"
            },
            "cost": {
                "amount": "21.00",
                "currency": "BYN"
            }
        },
        "delivered": {
            "positions": {
                "price": {
                    "amount": "0.00",
                    "currency": "BYN"
                },
                "discount": null,
                "cost": {
                    "amount": "0.00",
                    "currency": "BYN"
                }
            },
            "price": {
                "amount": "2.00",
                "currency": "BYN"
            },
            "discount": null,
            "cost": {
                "amount": "2.00",
                "currency": "BYN"
            }
        }
    },
    "delivered_order_cost": {
        "amount": "2.00",
        "currency": "BYN"
    },
    "comment": "Доставка с 9 до 18",
    "installment_info": null
}
```

### Описание полей ответа

Базовый набор полей заказа + статус заказа <kbd>status</kbd> ([Описание базового набора полей](show.md))

### Ответ при попытке изменить несуществующий заказ

```http
HTTP/1.1 404 Not Found
```
```json
{
    "message": "Заказ не найден"
}
```

### Ответ при попытке изменить заказ, который временно заблокирован по иным техническим причинам

```http
HTTP/1.1 409 Conflict
```

Исключительная ситуация.
В данном через несколько минут необходимо повторить запрос, однако за это время статус заказа может измениться. 

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
|status|Укажите статус<br/>Значение поля должно быть строкой<br/>Недопустимый статус заказа<br/>Недопустимый переход статусов|
|reason.id|Значение поля должно быть целым числом<br>Укажите причину<br>Некорректная причина|
|reason.comment|Значение поля должно быть строкой<br>Максимум 255 символов|
|delivery_comment|Значение поля должно быть строкой<br>Максимум 255 символов|
|delivery_price|Поле обязательно для заполнения<br>Значение поля должно быть массивом|
|delivery_price.amount|Поле обязательно для заполнения<br>Значение поля должно быть строкой<br>Недопустимое значение стоимости доставки<br>Стоимость доставки можно изменить только в меньшую сторону|
|delivery_price.currency|Поле обязательно для заполнения<br>Значение поля должно быть строкой<br>Выбранное значение поля ошибочно|
