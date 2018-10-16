## Получение информации о заказе

### GET /orders/{orderKey}

### Параметры запроса

|Параметр|Тип|Описание|
|---|---|---|
|include|string|Дополнительные группы данных о заказе|

##### Допустимые группы с дополнительной информацией:

- <kbd>shop</kbd> - Краткая информация о магазине
- <kbd>positions</kbd> - Информация о позициях и товарах заказа
- <kbd>status_change_log</kbd> - Информация об изменениях статусов заказа

### Пример запроса

```http
GET /orders/qz2wa
Authorization: bearer <token>
Accept: application/json; charset=utf-8
```
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
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "status": "new",
    "positions_count": 1,
    "total_quantity": 2,
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

### Пример запроса с информацией о позициях и магазине

```http
GET /orders/qz2wa?include=shop,positions,status_change_log
Authorization: bearer <token>
Accept: application/json; charset=utf-8
```
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
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "status": "new",
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
    "positions_count": 1,
    "total_quantity": 2,
    "comment": "Доставка с 9 до 18",
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
            "price": {
                "amount": 17400000
            },
            "position_price": {
                "amount": "17400000",
                "currency": "BYR",
                "converted": {
                    "BYR": {
                        "amount": "17400000",
                        "currency": "BYR"
                    },
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
                    "price": 0,
                    "delivery_price": {
                        "amount": "0",
                        "currency": "BYR",
                        "converted": {
                            "BYR": {
                                "amount": "0",
                                "currency": "BYR"
                            },
                            "BYN": {
                                "amount": "0.00",
                                "currency": "BYN"
                            }
                        }
                    },
                    "time": 1
                },
                "country": {
                    "price": 50000,
                    "delivery_price": {
                        "amount": "50000",
                        "currency": "BYR",
                        "converted": {
                            "BYR": {
                                "amount": "50000",
                                "currency": "BYR"
                            },
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
        }
    ],
    "status_change_log": [
        {
            "status": "new",
            "status_text": "Новый",
            "created_at": "2015-10-14 16:54:01"
        },
        {
            "status": "shop_canceled",
            "status_text": "Отменен магазином",
            "created_at": "2015-10-14 17:04:01"
        }
    ]
}
```

### Описание полей ответа

|Параметр|Тип|Описание|
|---|---|---|
|key|string|Уникальный код заказа, 5 символов, формируется случайным образом из букв латинского алфавита и цифр, исключая 0, o, 1, i, l|
|created_at|string|Время создания заказа|
|updated_at|string|Время изменения заказа|
|process_deadline|datetime|Время, до которого магазин должен обработать заказ|
|process_time_left|integer|Сколько секунд осталось до окончания обработки заказа или 0, если время обработки истекло|
|shop_id|integer|ID магазина|
|contact.name|string|Имя пользователя (Недоступно, если заказ находится в статусах, отличных от "В обработке" или "Доставлен")|
|contact.email|string|Контакный e-mail пользователя (Недоступно, если заказ находится в статусах, отличных от "В обработке" или "Доставлен")|
|contact.phone|string|Контактный телефон пользователя (Недоступно, если заказ находится в статусах, отличных от "В обработке" или "Доставлен")|
|delivery.city|string|Город доставки|
|delivery.address|string|Адрес доставки (Недоступно, если заказ находится в статусах, отличных от "В обработке" или "Доставлен")|
|comment|string|Общий комментарий к данному заказу|

#### Описание блока с информацией о ценовой позиции (каждый объект в массиве positions)

|Параметр|Тип|Описание|
|---|---|---|
|entry_id|integer|Идентификатор позиции в заказе|
|article|string or null|Артикул товара|
|quantity|integer|Количество товаров, заказанных в рамках данной позиции|
|original_quantity|integer|Количество товаров в рамках данной позиции, которое запросил покупатель при оформлении заказа|
|price.amount|integer| __(deprecated)__ Цена в белорусских рублях (BYR) |
|position_price.amount|string|Цена в основной валюте|
|position_price.currency|string|Основная валюта цены _(по умолчанию BYN)_|
|position_price.converted|object| __(deprecated)__ Массив цен во всех поддерживаемых валютах, где ключ - код валюты, значение - объект цены с указанием валюты и значением в данной валюте. В данный момент доступны валюты BYN и BYR|
|is_credit|boolean|Флаг доступности покупки в кредит (1 - можно, 0 - нет)|
|is_cashless|boolean|Флаг предложения для юридических лиц (1 - для юридических, 0 - для физических)|
|warranty|integer|Срок гарантии на товар (в месяцах)|
|comment|string|Комментарий продавца к данному предложению|
|producer|string|Сведения о производителе товара|
|importer|string|Сведения об импортере товара на территорию РБ|
|service_centers|string|Сведения о сервисном центре|
|delivery.town.price|integer| __(deprecated)__ Стоимость доставки в пределах г. Минска в бел. руб. (BYR) (если не указано - бесплатно)|
|delivery.town.delivery_price|object|Стоимость доставки в пределах г. Минска (если null - бесплатно)|
|delivery.town.delivery_price.amount|string|Стоимость доставки в пределах г. Минска в основной валюте|
|delivery.town.delivery_price.currency|string|Основная валюта стоимости доставки в пределах г. Минска|
|delivery.town.delivery_price.converted|object| __(deprecated)__ Массив цен доставки в пределах г. Минска во всех поддерживаемых валютах, где ключ - код валюты, значение - объект цены с указанием валюты и значением в данной валюте. В данный момент доступны валюты BYN и BYR|
|delivery.town.time|integer|Срок доставки в пределах г. Минска (в днях) (если не указано - доставка не осуществляется)|
|delivery.country.price|integer| __(deprecated)__ Стоимость доставки в пределах РБ в бел. руб. (BYR) (если не указано - бесплатно)|
|delivery.country.delivery_price|object|Стоимость доставки в пределах РБ (если null - бесплатно)|
|delivery.country.delivery_price.amount|string|Стоимость доставки в пределах РБ в основной валюте|
|delivery.country.delivery_price.currency|string|Основная валюта стоимости доставки в пределах РБ|
|delivery.country.delivery_price.converted|object| __(deprecated)__ Массив цен доставки в пределах РБ во всех поддерживаемых валютах, где ключ - код валюты, значение - объект цены с указанием валюты и значением в данной валюте. В данный момент доступны валюты BYN и BYR|
|delivery.country.time|integer|Срок доставки в пределах РБ (в днях) (если не указано - доставка не осуществляется)|

#### Описание блока с информацией о товаре (объект product в теле объекта position) 

|Параметр|Тип|Описание|
|---|---|---|
|id|integer|Числовой идентификатор товара|
|key|string|Строковый идентификатор товара|
|name|string|Краткое наименование товара|
|full_name|string|Полное наименование товара|
|images|object|Объект со ссылками на главное изображение товара|
|images.header|string|URL к изображению товара|
|images.icon|string|URL к изображению товара|
|description|string|Описание товара (краткая строка)|
|micro_description|string|Краткая-краткая строка)|
|html_url|string|Ссылка на страницу товара|
|reviews.create_html_url|string|Ссылка на страницу создания отзыва на товар|
|url|string|Ссылка на catalog.api для получения информации о товаре|

Если получить информацию о товаре не удалось, блок будет содержать только числовой и строковый идентификаторы товара.

- Блок с информацией о магазине содержит номер магазина, его название и ссылку на логотип. В некоторых случаях блок будет содержать только номер магазина.

### Oтвет при попытке получить несуществующий заказ

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
        "include": [
            "Поле обязательно для заполнения"
        ]
    }
}
```

### Возможные ошибки для полей:

|Параметр|Ошибки|
|---|---|
|include|Поле обязательно для заполнения|
|include|Значение поля должно быть строкой|
|include|Неправильный набор названий групп дополнительной информации|
