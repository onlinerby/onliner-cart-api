## Получить список заказов

### GET /orders

Информация о позициях фиксируется в заказе в момент оформления заказа и остается неизменной на протяжении всего жизненного цикла заказа.
Блоки данных `converted` с информацией о ценах использовались в течение переходного периода на время деноминации и могут быть удалены без предупреждения.

### Параметры запроса

|Параметр|Тип|Описание|
|---|---|---|
|page|integer|Номер страницы|
|limit|integer|Лимит записей на странице, по умолчанию - 50, максимально - 100|
|status|string|Строковый код статуса|
|include|string|Дополнительные группы данных о заказе [(такие же, как в методе получения информации о заказе)](show.md)|

### Пример запроса

```http
GET /orders
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```

### Пример ответа

```json
{
    "total": 3,
    "page": {
        "limit": 50,
        "items": 3,
        "current": 1,
        "last": 1
    },
    "orders" : [
        {
            "key": "shop1_4",
            "status": "new",
            "created_at": "2015-10-04T10:00:00+03:00",
            "updated_at": "2015-10-04T10:00:00+03:00",
            "process_deadline": "2015-10-04T10:20:00+03:00",
            "process_time_left": 60,
            "positions_count": 0,
            "order_cost": {
                "amount": "0",
                "currency": "BYN",
                "converted": {
                    "BYN": {
                        "amount": "0.00",
                        "currency": "BYN"
                    }
                }
            },
            "total_quantity": 0,
            "comment": "",
            "product_names": []
        },
        {
            "key": "shop1_2",
            "status": "confirmed",
            "created_at": "2015-10-02T10:00:00+03:00",
            "updated_at": "2015-10-02T10:00:00+03:00",
            "process_deadline": "2015-10-04T10:20:00+03:00",
            "process_time_left": 60,
            "positions_count": 2,
            "total_quantity": 2,
            "order_cost": {
                "amount": "30.00",
                "currency": "BYN",
                "converted": {
                    "BYN": {
                        "amount": "30.00",
                        "currency": "BYN"
                    }
                }
            },
            "comment": "Доставка с 9 до 18",
            "product_names": ["Apple iPhone 1", "Apple iPhone 2"]
        },
        {
            "key": "shop1_1",
            "status": "confirmed",
            "created_at": "2015-10-01T10:00:00+03:00",
            "updated_at": "2015-10-01T10:00:00+03:00",
            "process_deadline": "2015-10-04T10:20:00+03:00",
            "process_time_left": 60,
            "positions_count": 1,
            "total_quantity": 1,
            "order_cost": {
                "amount": "10.00",
                "currency": "BYN",
                "converted": {
                    "BYN": {
                        "amount": "10.00",
                        "currency": "BYN"
                    }
                }
            },
            "comment": "",
            "product_names": ["Apple iPhone 1"]
        }
    ]
}
```

### Пример запроса и ответа с информацией о позициях и магазине

```http
GET /orders?include=shop,positions
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```
```json
{
    "total": 3,
    "page": {
        "limit": 50,
        "items": 3,
        "current": 1,
        "last": 1
    },
    "orders" : [
        {
            "key": "qz2wa",
            "user_id": 1,
            "contact": {
                "name": "Пользователь Тестовый",
                "first_name": "Пользователь",
                "last_name": "Тестовый",
                "email": "test@onliner.by",
                "phone": "+375291234567"
            },
            "delivery": {
                "city": "Минск",
                "address": "пр-т Дзержинского, 55 д., 1a к., 607 кв., 2 под., 16 эт.",
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
            "updated_at": "2015-10-14T17:20:28+03:00",
            "process_deadline": "2015-10-14T17:40:28+03:00",
            "process_time_left": 60,
            "is_new_flow": true,
            "status": "new",
            "positions_count": 1,
            "total_quantity": 3,
            "order_cost": {
                "amount": "20.00",
                "currency": "BYN",
                "converted": {
                    "BYN": {
                        "amount": "20.00",
                        "currency": "BYN"
                    }
                }
            },
            "comment": "",
            "shop": {
                "id": 668,
                "url": "https://shop.api.onliner.by/shops/668",
                "title": "Тестовый магазин",
                "logo": "https://content.onliner.by/b2b/668/logotype/9be48fb27f5f8383ccb7a09c3336be8d.gif",
                "html_url": "http://668.shop.onliner.by",
                "reviews": {
                    "create_html_url": "http://668.shop.onliner.by/review/add"
                }
            },
            "positions": [
                {
                    "entry_id": 1,
                    "article": "NC900",
                    "position_price": {
                        "amount": "1740.00",
                        "currency": "BYN",
                        "converted": {
                            "BYN": {
                                "amount": "1740.00",
                                "currency": "BYN"
                            }
                        }
                    },
                    "quantity": 2,
                    "original_quantity": 2,
                    "is_credit": false,
                    "is_cashless": true,
                    "warranty": 12,
                    "comment": "Original. Запечатан. Never locked.Наличие цвета уточняйте. Полный заводской комплект. Поможем вырезать сим! Своевременная Доставка! Гарантия Минского СЦ!",
                    "producer": "Hon Hai Precision Industry Co. Ltd. (Foxconn) General Bonded Zone, East ZhenXing Rd., Zhengzhou Airport, Zhengzhou, Henan, China.",
                    "importer": "ООО ИМПОРТЕР",
                    "service_centers": "ООО Сервисный центр",
                    "delivery": {
                        "town": {
                            "delivery_price": {
                                "amount": "0.00",
                                "currency": "BYN",
                                "converted": {
                                    "BYN": {
                                        "amount": "0.00",
                                        "currency": "BYN"
                                    }
                                }
                            },
                            "time": 1
                        },
                        "country": {
                            "delivery_price": {
                                "amount": "5.00",
                                "currency": "BYN",
                                "converted": {
                                    "BYN": {
                                        "amount": "5.00",
                                        "currency": "BYN"
                                    }
                                }
                            },
                            "time": 2
                        }
                    },
                    "user_comment": "комментарий к заказу",
                    "product": {
                        "id": 607690,
                        "key": "iphone6plus128gb",
                        "name": "iPhone 6 Plus (128Gb)",
                        "full_name": "Apple iPhone 6 Plus (128Gb)",
                        "html_url": "http://catalog.onliner.by/mobile/apple/iphone6_128gb",
                        "images": {
                            "header": "https://content2.onliner.by/catalog/device/header/9ef7d6129330582a204ee2192b578c72.jpg",
                            "icon": "https://content2.onliner.by/catalog/device/icon/d75663217c0b89622d66faada19c2aa7.jpg"
                        },
                        "description": "Apple iOS, экран 5.5\" IPS (1080x1920), ОЗУ 1 ГБ, флэш-память 128 ГБ, камера 8 Мп, аккумулятор 2915 мАч",
                        "micro_description": "экран 5.5\" (1080x1920), ОЗУ 1 ГБ, флэш-память 128 ГБ",
                        "url": "https://catalog.api.onliner.by/products/iphone6plus128gb",
                        "reviews": {
                            "create_html_url": "http://catalog.onliner.by/mobile/apple/iphone6_128gb/reviews/create"
                        }
                    }
                },
                ...
            ]
        },
    ...
    ]
}
```

### Описание полей ответа

|Параметр|Тип|Описание|
|---|---|---|
|key|string|Уникальный код заказа|
|status|string|Строковый код статуса|
|created_at|string|Время создания заказа|
|updated_at|string|Время изменения заказа|
|process_deadline|datetime|Время, до которого магазин должен обработать заказ|
|process_time_left|integer|Сколько секунд осталось до окончания обработки заказа или 0, если время обработки истекло|
|positions_count|integer|Количество позиций в заказе|
|total_quantity|integer|Общее количество товаров в заказе|
|order_cost|object|Общая стоимость заказа|
|comment|string|Общий комментарий пользователя к данному заказу|
|product_names|array|Имена товаров в заказе|
|positions.entry_id|integer|ID позиции в заказе|

Для более подробного описания полей смотрите [описание метода для получения информации о конкретном заказе](show.md). 

### Ответ при невалидном запросе

```http
GET /orders?status=invalid_status
Authorization: bearer <token>
Accept: application/json; charset=utf-8
```
```http
HTTP/1.1 422 Unprocessable Entity
Content-Type: application/json; charset=utf-8
```
```json
{
    "message": "Validation failed",
    "errors": {
        "status": [
            "Выбранное значение поля ошибочно"
        ]
    }
}
```

### Возможные ошибки для полей:

|Параметр|Ошибки|
|---|---|
|page|Значение поля должно быть целым числом<br/> Значение поля должно быть не менее 1|
|limit|Значение поля должно быть целым числом<br/> Значение поля должно быть не менее 1<br/> Значение поля не может быть больше 100|
|status|Значение поля должно быть строкой<br/> Недопустимый статус|
|include|Поле обязательно для заполнения<br/>Значение поля должно быть строкой<br/>Неправильный набор названий групп дополнительной информации|
