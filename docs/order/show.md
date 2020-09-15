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

### Пример запроса с курьерской доставкой

```http
GET /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```
```json
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
        "city": "г. Минск",
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
        "type": "courier",
        "price": {
            "amount": "3.00", 
            "currency": "BYN"
        },
        "days": 3,
        "comment": "Курьер прибудет с 17:00 - 21:00",
        "is_fake": false,
        "date_range": {
            "from": "2020-06-17",
            "to": "2020-07-17"
        },
        "date_from": "2020-06-17T00:01:00+03:00",
        "date_to": "2020-06-17T23:59:59+03:00"
    },
    "payment": {
        "type": "cash"
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "is_new_flow": true,
    "status": "new",
    "positions_count": 1,
    "total_quantity": 2,
    "shop_comments_count": 0,
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
    "comment": "Доставка с 9 до 18"
}
```

### Пример запроса с доставкой в ПВЗ

```http
GET /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```
```json
{
    "key": "qz2wa",
    "user_id": 1,
    "contact": {
        "name": "Имя Фамилия",
        "first_name": "Имя",
        "middle_name": "Отчество",
        "last_name": "Фамилия",        
        "email": "test@onliner.by",
        "phone": "+375291234567"
    },
    "delivery": {
        "city": null,
        "address": null,
        "address_fields": null,
        "pickup_point": {
            "id": 1,
            "name": "ПВЗ 1",
            "address": {
                "geo_town": "г. Минск",
                "geo_town_id": 1,
                "summary": "ул. Ленина, д. 183, к. 1, под. 1, эт. 1, пом. 1",
                "street": "ул. Ленина",
                "building": "183",
                "apartment": "1",
                "block": "1",
                "entrance": "1",
                "floor": "1",
                "coordinates": {
                    "lat": 53.8846196,
                    "long": 27.5233293
                }
            },
            "comment": "Комментарий к ПВЗ",
            "contacts": {
                "phones": [
                    "+375291111111"
                ]
            },
            "store_term": 1,
            "schedule": {
                "monday": {
                    "from": "09:00",
                    "till": "18:00"
                },
                "tuesday": {
                    "from": "09:00",
                    "till": "18:00"
                },
                "wednesday": {
                    "from": "09:00",
                    "till": "18:00"
                },
                "thursday": {
                    "from": "09:00",
                    "till": "18:00"
                },
                "friday": {
                    "from": "09:00",
                    "till": "18:00"
                },
                "saturday": null,
                "sunday": null
            },
            "delivery_confirmed": true,
            "delivery_confirmed_at": "2020-01-23T00:01:00+03:00",
            "delivery_comment": "Ваш заказ прибыл в пункт выдачи"
        },
        "type": "pickup_point",
        "price": {
            "amount": "3.00", 
            "currency": "BYN"
        },
        "days": 3,
        "comment": "Комментарий к доставке",
        "is_fake": false,
        "date_range": {
            "from": "2020-06-17",
            "to": "2020-07-17"
        },
        "date_from": "2020-06-17T00:01:00+03:00",
        "date_to": "2020-06-17T23:59:59+03:00"
    },
    "payment": {
        "type": "cash"
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "is_new_flow": true,
    "status": "new",
    "positions_count": 1,
    "total_quantity": 2,
    "shop_comments_count": 0,    
    "installment_info": null,
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
    "delivered_order_cost": {
        "amount": "20.00",
        "currency": "BYN",
        "converted": {
            "BYN": {
                "amount": "20.00",
                "currency": "BYN"
            }
        }
    },
    "comment": "Доставка с 9 до 18"
}

```
### Пример запроса для заказа, оплаченного картой рассрочки

```http
GET /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```
```json
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
        "type": "halva",
        "status": "captured"
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "is_new_flow": true,
    "status": "delivered",
    "positions_count": 1,
    "total_quantity": 2,
    "shop_comments_count": 0,    
    "installment_info": {
        "amount_per_month": {
            "amount": "11.00",
            "currency": "BYN"
        },
        "term": 3
    },
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
    "delivered_order_cost": {
        "amount": "30.00",
        "currency": "BYN",
        "converted": {
            "BYN": {
                "amount": "30.00",
                "currency": "BYN"
            }
        }
    },
    "comment": "Доставка с 9 до 18"
}
```

### Пример запроса с информацией о позициях и магазине

```http
GET /orders/qz2wa?include=shop,positions,status_change_log
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```
```json
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
        "is_fake": false,
        "date_range": {
            "from": "2020-06-17",
            "to": "2020-07-17"
        },
        "date_from": "2020-06-17T00:01:00+03:00",
        "date_to": "2020-06-17T23:59:59+03:00"
    },
    "payment": {
        "type": "cash"
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "is_new_flow": true,
    "status": "new",
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
    "delivered_order_cost": {
        "amount": "20.00",
        "currency": "BYN",
        "converted": {
            "BYN": {
                "amount": "20.00",
                "currency": "BYN"
            }
        }
    },
    "positions_count": 1,
    "total_quantity": 2,
    "shop_comments_count": 0,
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
|contact.name|string|__(deprecated)__ Имя пользователя (Недоступно, если заказ находится в некоторых статусах)|
|contact.first_name|string|Имя покупателя|
|contact.last_name|string|Фамилия покупателя|
|contacts.middle_name|string|Отчество покупателя|
|contact.email|string|Контакный e-mail пользователя (Недоступно, если заказ находится в некоторых статусах)|
|contact.phone|string|Контактный телефон пользователя (Недоступно, если заказ находится в некоторых статусах)|
|delivery.city|string|Город доставки|
|delivery.address|string|Полный адрес доставки (Недоступно, если заказ находится в некоторых статусах)|
|delivery.address_fields|object|Детализированная информация об адресе доставке (Недоступно, если заказ находится в некоторых статусах)|
|delivery.address_fields.street|string|Название улицы|
|delivery.address_fields.building|string or null|Номер дома|
|delivery.address_fields.apartment|string or null|Номер квартиры|
|delivery.address_fields.block|string or null|Номер корпуса| 
|delivery.address_fields.entrance|string or null|Номер подъезда|
|delivery.address_fields.floor|string or null|Номер этажа| 
|delivery.address_fields.comment|string or null|Комментарий к адресу|
|delivery.pickup_point|object|Доставка в ПВЗ|
|delivery.pickup_point.id|int|ID ПВЗ|
|delivery.pickup_point.name|string|Название ПВЗ|
|delivery.pickup_point.address|object|Информация об адресе|
|delivery.pickup_point.address.geo_town_id|int|ID города из geo api|
|delivery.pickup_point.address.town|string|Название города|
|delivery.pickup_point.address.street|string|Название улицы|
|delivery.pickup_point.address.building|string|Номер дома|
|delivery.pickup_point.address.block|string|Корпус|
|delivery.pickup_point.address.entrance|string|Подъезд|
|delivery.pickup_point.address.floor|string|Этаж|
|delivery.pickup_point.address.apartment|string|Квартира|
|delivery.pickup_point.address.coordinates|object|Координаты ПВЗ|
|delivery.pickup_point.address.coordinates.lat|float|Широта|
|delivery.pickup_point.address.coordinates.long|float|Долгота|
|delivery.pickup_point.address.summary|string|Полное значение адреса|
|delivery.pickup_point.comment|string|Комментарий к ПВЗ|
|delivery.pickup_point.contacts.phones|array|Список телефонов ПВЗ|
|delivery.pickup_point.contacts.phones.*|string|Телефон ПВЗ|
|delivery.pickup_point.store_term|int|Срок хранения заказа в днях. От 1 до 10 (включительно)|
|delivery.pickup_point.schedule|object|Режим работы ПВЗ|
|delivery.pickup_point.schedule.`<week_day>`|object &#124; null|Параметры режима работы ПВЗ для конкретного для недели. Если в этот день ПВЗ не работает(выходной) указывается null|
|delivery.pickup_point.schedule.`<week_day>`.from|string|Время начала работы. Формат "ЧЧ:ММ"|
|delivery.pickup_point.schedule.`<week_day>`.till|string|Время окончания работы. Формат "ЧЧ:ММ"|
|delivery.pickup_point.delivery_confirmed|bool|Пометка о доставке заказа в ПВЗ|
|delivery.pickup_point.delivery_confirmed_at|string|Время когда был доставлен заказ в ПВЗ (если была оставлена пометка о доставке). Формат ATOM|
|delivery.pickup_point.delivery_comment|string|Дополнительный комментарий к пометке о доставке в ПВЗ|
|delivery.type|string or null|Тип доставки. Возможные значения:`courier`, `pickup_point`)|
|delivery.price|object or null|Стоимость доставки|
|delivery.price.amount|string|Сумма стоимости доставки|
|delivery.price.currency|string|Валюта стоимости доставки _(только BYN)_|
|delivery.days|int or null|Срок доставки (количество дней)|
|delivery.comment|string or null|Комментарий от магазина к доставке|
|delivery.is_fake|boolean|Признак ложной доставки, `true`, если пользователь после доставки пожаловался, что доставка не была осуществлена|
|delivery.date_from|string (optional)|Начало предполагаемого магазином диапазона времени доставки. Формат ATOM|
|delivery.date_to|string (optional)|Конец предполагаемого магазином диапазона времени доставки. Формат ATOM|
|delivery.date_range|object|Диапазон дат для доставки (только в статусе "processing")|
|delivery.date_range.from|string|Дата от YYYY-MM-DD|
|delivery.date_range.to|string|Дата до YYYY-MM-DD|
|is_new_flow|boolean|Признак нового заказа (заказ по старому сценарию - false, заказ по новому сценарию - true)|
|shop_comments_count|integer|Количество внутренних комментариев магазина к заказу|
|payment|object or null|Блок с информацией о способе оплаты и ее статусе|
|payment.type|string|Способ оплаты, выбранный пользователем|
|payment.status|string|Статус онлайн-оплаты|
|comment|string|Общий комментарий к данному заказу|
|order_cost|object|Информация о стоимости заказа|
|order_cost.amount|string|Стоимость заказа|
|order_cost.currency|string|Валюта|
|delivered_order_cost|object|Информация о стоимости заказа с учётом фактически доставленных товаров и стоимости доставки|
|delivered_order_cost.amount|string|Стоимость заказа|
|delivered_order_cost.currency|string|Валюта|
|installment_info|object or null|Информация о рассрочке|
|installment_info.amount_per_month|object|Информация о сумме ежемесячного платежа|
|installment_info.amount_per_month.amount|string|Сумма ежемесячного платежа|
|installment_info.amount_per_month.currency|string|Валюта|

#### Описание блока с информацией о ценовой позиции (каждый объект в массиве positions)

|Параметр|Тип|Описание|
|---|---|---|
|entry_id|integer|Идентификатор позиции в заказе|
|article|string or null|Артикул товара|
|quantity|integer|Количество товаров, заказанных в рамках данной позиции|
|original_quantity|integer|Количество товаров в рамках данной позиции, которое запросил покупатель при оформлении заказа|
|position_price.amount|string|Цена в основной валюте|
|position_price.currency|string|Основная валюта цены _(по умолчанию BYN)_|
|position_price.converted|object| __(deprecated)__ Массив цен во всех поддерживаемых валютах, где ключ - код валюты, значение - объект цены с указанием валюты и значением в данной валюте. В данный момент доступна только BYN|
|is_credit|boolean|Флаг доступности покупки в кредит (1 - можно, 0 - нет)|
|is_cashless|boolean|Флаг предложения для юридических лиц (1 - для юридических, 0 - для физических)|
|warranty|integer|Срок гарантии на товар (в месяцах)|
|comment|string|Комментарий продавца к данному предложению|
|producer|string|Сведения о производителе товара|
|importer|string|Сведения об импортере товара на территорию РБ|
|service_centers|string|Сведения о сервисном центре|
|delivery.town.delivery_price|object|__(deprecated)__ Стоимость доставки в пределах г. Минска (если null - бесплатно)|
|delivery.town.delivery_price.amount|string|__(deprecated)__ Стоимость доставки в пределах г. Минска в основной валюте|
|delivery.town.delivery_price.currency|string|__(deprecated)__ Основная валюта стоимости доставки в пределах г. Минска|
|delivery.town.delivery_price.converted|object| __(deprecated)__ Массив цен доставки в пределах г. Минска во всех поддерживаемых валютах, где ключ - код валюты, значение - объект цены с указанием валюты и значением в данной валюте. В данный момент доступна только BYN|
|delivery.town.time|integer|__(deprecated)__ Срок доставки в пределах г. Минска (в днях) (если не указано - доставка не осуществляется)|
|delivery.country.delivery_price|object|__(deprecated)__ Стоимость доставки в пределах РБ (если null - бесплатно)|
|delivery.country.delivery_price.amount|string|__(deprecated)__ Стоимость доставки в пределах РБ в основной валюте|
|delivery.country.delivery_price.currency|string|__(deprecated)__ Основная валюта стоимости доставки в пределах РБ|
|delivery.country.delivery_price.converted|object| __(deprecated)__ Массив цен доставки в пределах РБ во всех поддерживаемых валютах, где ключ - код валюты, значение - объект цены с указанием валюты и значением в данной валюте. В данный момент доступна только BYN|
|delivery.country.time|integer|__(deprecated)__ Срок доставки в пределах РБ (в днях) (если не указано - доставка не осуществляется)|

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
    "message": "Заказ не найден"
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
