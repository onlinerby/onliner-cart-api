## Получение информации о заказе

### GET /orders/{orderKey}

### Параметры запроса

| Параметр | Тип    | Описание                              |
|----------|--------|---------------------------------------|
| include  | string | Дополнительные группы данных о заказе |

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
        "geo_town_id": 17030,
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
            "amount": "2.00", 
            "currency": "BYN"
        },
        "days": 3,
        "term": "17 октября",
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
    "status": "new",
    "positions_count": 1,
    "total_quantity": 1,
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
            },
            "overpayment": null,
            "overall": {
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
            },
            "overpayment": null,
            "overall": {
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
    "permissions": {
        "delete": false
    }
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
    "promocode": {
        "id": 1,
        "name": "test1"
    },
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
        "geo_town_id": 0,
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
            "amount": "2.00", 
            "currency": "BYN"
        },
        "days": 3,
        "term": "17 октября",
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
    "status": "new",
    "positions_count": 1,
    "total_quantity": 1,
    "shop_comments_count": 0,    
    "installment_info": null,
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
            },
            "overpayment": null,
            "overall": {
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
            },
            "overpayment": null,
            "overall": {
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
    "permissions": {
        "delete": false
    }
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
    "promocode": null,
    "user_id": 1,
    "contact": {
        "name": "Пользователь Тестовый",
        "first_name": "Пользователь",
        "last_name": "Тестовый",        
        "email": "test@onliner.by",
        "phone": "+375291234567"
    },
    "delivery": {
        "geo_town_id": 17030,
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
            "amount": "2.00", 
            "currency": "BYN"
        },
        "days": 3,
        "term": "17 октября",
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
    "status": "delivered",
    "positions_count": 1,
    "total_quantity": 1,
    "shop_comments_count": 0,    
    "installment_info": {
        "amount_per_month": {
            "amount": "9.00",
            "currency": "BYN"
        },
        "term": 3
    },
    "order_cost": {
        "amount": "27.00",
        "currency": "BYN"
    },
    "order_price": {
        "amount": "27.00",
        "currency": "BYN"
    },
    "order_discount": null,
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
                "discount": null,
                "cost": {
                    "amount": "25.00",
                    "currency": "BYN"
                }
            },
            "price": {
                "amount": "27.00",
                "currency": "BYN"
            },
            "discount": null,
            "cost": {
                "amount": "27.00",
                "currency": "BYN"
            },
            "overpayment": null,
            "overall": {
                "amount": "27.00",
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
            },
            "overpayment": null,
            "overall": {
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
    "permissions": {
        "delete": false
    }
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
        "city": "Минск",
        "geo_town_id": 17030,
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
            "amount": "2.00", 
            "currency": "BYN"
        },
        "days": 3,
        "term": "17 октября",
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
    "status": "new",
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
            },
            "overpayment": null,
            "overall": {
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
            },
            "overpayment": null,
            "overall": {
                "amount": "2.00",
                "currency": "BYN"
            }
        }
    },
    "delivered_order_cost": {
        "amount": "2.00",
        "currency": "BYN"
    },
    "positions_count": 1,
    "total_quantity": 1,
    "shop_comments_count": 0,
    "comment": "Доставка с 9 до 18",
    "permissions": {
        "delete": false
    },
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
                "currency": "BYN"
            },
            "regular_price": {
                "amount": "0.06",
                "currency": "BYN"
            },
            "position_discount": null,
            "cost": {
                "amount": "0.01",
                "currency": "BYN"
            },
            "price": {
                "amount": "0.06",
                "currency": "BYN"
            },
            "discount": {
                "amount": "0.05",
                "currency": "BYN"
            },
            "delivered_cost": {
                "amount": "0.00",
                "currency": "BYN"
            },
            "delivered_price": {
                "amount": "0.00",
                "currency": "BYN"
            },
            "delivered_discount": null,
            "undelivered_cost": {
                "amount": "0.01",
                "currency": "BYN"
            },
            "undelivered_price": {
                "amount": "0.06",
                "currency": "BYN"
            },
            "undelivered_discount": {
                "amount": "0.05",
                "currency": "BYN"
            },
            "quantity": 2,
            "delivered_quantity": 2,
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
                        "currency": "BYN"
                    },
                    "time": 1
                },
                "country": {
                    "delivery_price": {
                        "amount": "5.00",
                        "currency": "BYN"
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
                    "header": "https://imgproxy.onliner.by/sHBAJGlZLiZK9jgSF1VF40iYOx2gnu9bdpTOyY0MWIU/w:170/h:250/z:2/f:jpg/aHR0cHM6Ly9jb250/ZW50Lm9ubGluZXIu/dHYxL2NhdGFsb2cv/ZGV2aWNlL2hlYWRl/ci8xNWFiM2Y3NTI5/MWM0ZmFjMjhiN2Ni/YzRlNTVmNGVmZC5q/cGc"
                },
                "description": "Apple iOS, экран 5.5\" IPS (1080x1920), ОЗУ 1 ГБ, флэш-память 128 ГБ, камера 8 Мп, аккумулятор 2915 мАч",
                "micro_description": "экран 5.5\" (1080x1920), ОЗУ 1 ГБ, флэш-память 128 ГБ",
                "url": "https://catalog.api.onliner.by/products/iphone6plus128gb",
                "reviews": {
                    "create_html_url": "http://catalog.onliner.by/mobile/apple/iphone6_128gb/reviews/create"
                }
            },
            "position_id": "123123123123"
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

### Пример запроса для заказа с примененной акцией "Бесплатная доставка от MasterCard"

```http
GET /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```
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
        "geo_town_id": 17030,
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
            "amount": "2.00", 
            "currency": "BYN"
        },
        "days": 3,
        "term": "17 октября",
        "comment": "Курьер прибудет с 17:00 - 21:00",
        "is_fake": false
    },
    "payment": {
        "type": "online",
        "status": "captured"
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "status": "delivered",
    "positions_count": 1,
    "total_quantity": 1,
    "shop_comments_count": 0,    
    "installment_info": null,
    "order_cost": {
        "amount": "25.00",
        "currency": "BYN"
    },
    "order_price": {
        "amount": "25.00",
        "currency": "BYN"
    },
    "order_discount": null,
    "totals": {
        "delivery": {
            "price": {
                "amount": "2.00",
                "currency": "BYN"
            },
            "discount": {
                "amount": "2.00",
                "currency": "BYN"
            },
            "cost": {
                "amount": "0.00",
                "currency": "BYN"
            }
        },
        "original": {
            "positions": {
                "price": {
                    "amount": "25.00",
                    "currency": "BYN"
                },
                "discount": null,
                "cost": {
                    "amount": "25.00",
                    "currency": "BYN"
                }
            },
            "price": {
                "amount": "25.00",
                "currency": "BYN"
            },
            "discount": null,
            "cost": {
                "amount": "25.00",
                "currency": "BYN"
            },
            "overpayment": null,
            "overall": {
                "amount": "25.00",
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
                "amount": "0.00",
                "currency": "BYN"
            },
            "discount": null,
            "cost": {
                "amount": "0.00",
                "currency": "BYN"
            },
            "overpayment": null,
            "overall": {
                "amount": "0.00",
                "currency": "BYN"
            }
        }
    },
    "delivered_order_cost": {
        "amount": "0.00",
        "currency": "BYN"
    },
    "promotions": {
        "mastercard_free_delivery": {
            "order_cost": {
                "amount": "25.00",
                "currency": "BYN"
            },
            "order_price": {
                "amount": "25.00",
                "currency": "BYN"
            },
            "delivered_order_cost": {
                "amount": "0.00",
                "currency": "BYN"
            },
            "delivery": {
                "price": {
                    "amount": "0.00",
                    "currency": "BYN"
                }
            },
            "cobrand_info": {
                "use_loyalty_points": false,
                "cashback": {
                    "amount": "1.25",
                    "currency": "BYN"
                },
                "is_max_cashback": false
            }
        }
    },
    "comment": "Доставка с 9 до 18",
    "permissions": {
        "delete": false
    },
}
```

### Пример запроса со способом оплаты Minipay

```http
GET /orders/qz2wa
Authorization: Bearer <token>
Accept: application/json; charset=utf-8
```
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
        "geo_town_id": 17030,
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
            "amount": "2.00", 
            "currency": "BYN"
        },
        "days": 3,
        "term": "17 октября",
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
        "type": "by_parts"
    },
    "by_parts_info": {
        "term": 24,
        "monthly_payment": {
            "amount": "2.99",
            "currency": "BYN"
        }
    },
    "permissions": {
        "delete": false
    },
    "created_at": "2015-10-14T17:20:28+03:00",
    "updated_at": "2015-10-14T17:20:28+03:00",
    "process_deadline": "2015-10-14T17:40:28+03:00",
    "status": "new",
    "positions_count": 1,
    "total_quantity": 1,
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
                },
                "overpayment": {
                    "amount": "0.15",
                    "currency": "BYN"
                },
                "overall": {
                    "amount": "19.15",
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
            },
            "overpayment": {
                "amount": "0.01",
                "currency": "BYN"
            },
            "overall": {
                "amount": "2.01",
                "currency": "BYN"
            }
        }
    },
    "delivered_order_cost": {
        "amount": "2.00",
        "currency": "BYN"
    },
    "comment": "Доставка с 9 до 18"
}
```

### Все поля с типом "money" имеют следующую структуру:

| Параметр | Тип    | Описание |
|----------|--------|----------|
| amount   | string | Сумма    |
| currency | string | Валюта   |

### Описание полей ответа

| Параметр                                         | Тип                | Описание                                                                                                                                                                                                               |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| key                                              | string             | Уникальный код заказа, 5 символов, формируется случайным образом из букв латинского алфавита и цифр, исключая 0, o, 1, i, l                                                                                            |
| promocode                                        | object/null        | Промокод                                                                                                                                                                                                               |
| promocode.id                                     | integer            | Идентификатор промокода                                                                                                                                                                                                |
| promocode.name                                   | string             | Название промокода                                                                                                                                                                                                     |
| created_at                                       | string             | Время создания заказа                                                                                                                                                                                                  |
| updated_at                                       | string             | Время изменения заказа                                                                                                                                                                                                 |
| process_deadline                                 | datetime           | Время, до которого магазин должен обработать заказ                                                                                                                                                                     |
| process_time_left                                | integer            | Сколько секунд осталось до окончания обработки заказа или 0, если время обработки истекло                                                                                                                              |
| shop_id                                          | integer            | ID магазина                                                                                                                                                                                                            |
| contact.name                                     | string             | __(deprecated)__ Имя пользователя (Недоступно, если заказ находится в некоторых статусах)                                                                                                                              |
| contact.first_name                               | string             | Имя покупателя                                                                                                                                                                                                         |
| contact.last_name                                | string             | Фамилия покупателя                                                                                                                                                                                                     |
| contacts.middle_name                             | string             | Отчество покупателя                                                                                                                                                                                                    |
| contact.email                                    | string             | Контакный e-mail пользователя (Недоступно, если заказ находится в некоторых статусах)                                                                                                                                  |
| contact.phone                                    | string             | Контактный телефон пользователя (Недоступно, если заказ находится в некоторых статусах)                                                                                                                                |
| delivery.city                                    | string             | Город доставки                                                                                                                                                                                                         |
| delivery.geo_town_id                             | int                | ID населенного пункта из geo api. [Получение детальной информации по id](geo/get_town_by_id.md)                                                                                                                        |
| delivery.address                                 | string             | Полный адрес доставки (Недоступно, если заказ находится в некоторых статусах)                                                                                                                                          |
| delivery.address_fields                          | object             | Детализированная информация об адресе доставке (Недоступно, если заказ находится в некоторых статусах)                                                                                                                 |
| delivery.address_fields.street                   | string             | Название улицы                                                                                                                                                                                                         |
| delivery.address_fields.building                 | string/null        | Номер дома                                                                                                                                                                                                             |
| delivery.address_fields.apartment                | string/null        | Номер квартиры                                                                                                                                                                                                         |
| delivery.address_fields.block                    | string/null        | Номер корпуса                                                                                                                                                                                                          | 
| delivery.address_fields.entrance                 | string/null        | Номер подъезда                                                                                                                                                                                                         |
| delivery.address_fields.floor                    | string/null        | Номер этажа                                                                                                                                                                                                            | 
| delivery.address_fields.comment                  | string/null        | Комментарий к адресу                                                                                                                                                                                                   |
| delivery.pickup_point                            | object             | Доставка в ПВЗ                                                                                                                                                                                                         |
| delivery.pickup_point.id                         | int                | ID ПВЗ                                                                                                                                                                                                                 |
| delivery.pickup_point.name                       | string             | Название ПВЗ                                                                                                                                                                                                           |
| delivery.pickup_point.address                    | object             | Информация об адресе                                                                                                                                                                                                   |
| delivery.pickup_point.address.geo_town_id        | int                | ID населенного пункта из geo api. [Получение детальной информации по id](geo/get_town_by_id.md)                                                                                                                        |
| delivery.pickup_point.address.town               | string             | Название города                                                                                                                                                                                                        |
| delivery.pickup_point.address.street             | string             | Название улицы                                                                                                                                                                                                         |
| delivery.pickup_point.address.building           | string             | Номер дома                                                                                                                                                                                                             |
| delivery.pickup_point.address.block              | string             | Корпус                                                                                                                                                                                                                 |
| delivery.pickup_point.address.entrance           | string             | Подъезд                                                                                                                                                                                                                |
| delivery.pickup_point.address.floor              | string             | Этаж                                                                                                                                                                                                                   |
| delivery.pickup_point.address.apartment          | string             | Квартира                                                                                                                                                                                                               |
| delivery.pickup_point.address.coordinates        | object             | Координаты ПВЗ                                                                                                                                                                                                         |
| delivery.pickup_point.address.coordinates.lat    | float              | Широта                                                                                                                                                                                                                 |
| delivery.pickup_point.address.coordinates.long   | float              | Долгота                                                                                                                                                                                                                |
| delivery.pickup_point.address.summary            | string             | Полное значение адреса                                                                                                                                                                                                 |
| delivery.pickup_point.comment                    | string             | Комментарий к ПВЗ                                                                                                                                                                                                      |
| delivery.pickup_point.contacts.phones            | array              | Список телефонов ПВЗ                                                                                                                                                                                                   |
| delivery.pickup_point.contacts.phones.*          | string             | Телефон ПВЗ                                                                                                                                                                                                            |
| delivery.pickup_point.store_term                 | int                | Срок хранения заказа в днях. От 1 до 10 (включительно)                                                                                                                                                                 |
| delivery.pickup_point.schedule                   | object             | Режим работы ПВЗ                                                                                                                                                                                                       |
| delivery.pickup_point.schedule.`<week_day>`      | object &#124; null | Параметры режима работы ПВЗ для конкретного для недели. Если в этот день ПВЗ не работает(выходной) указывается null                                                                                                    |
| delivery.pickup_point.schedule.`<week_day>`.from | string             | Время начала работы. Формат "ЧЧ:ММ"                                                                                                                                                                                    |
| delivery.pickup_point.schedule.`<week_day>`.till | string             | Время окончания работы. Формат "ЧЧ:ММ"                                                                                                                                                                                 |
| delivery.pickup_point.delivery_confirmed         | bool               | Пометка о доставке заказа в ПВЗ                                                                                                                                                                                        |
| delivery.pickup_point.delivery_confirmed_at      | string             | Время когда был доставлен заказ в ПВЗ (если была оставлена пометка о доставке). Формат ATOM                                                                                                                            |
| delivery.pickup_point.delivery_comment           | string             | Дополнительный комментарий к пометке о доставке в ПВЗ                                                                                                                                                                  |
| delivery.type                                    | string/null        | Тип доставки. Возможные значения:`courier`, `pickup_point`)                                                                                                                                                            |
| delivery.price                                   | money/null         | Стоимость доставки                                                                                                                                                                                                     |
| delivery.days                                    | int/null           | Срок доставки (количество дней)                                                                                                                                                                                        |
| delivery.term                                    | string/null        | Время доставки в строковом формате                                                                                                                                                                                     |
| delivery.comment                                 | string/null        | Комментарий от магазина к доставке                                                                                                                                                                                     |
| delivery.is_fake                                 | boolean            | Признак ложной доставки, `true`, если пользователь после доставки пожаловался, что доставка не была осуществлена                                                                                                       |
| delivery.date_from                               | string             | (optional) Начало предполагаемого магазином диапазона времени доставки. Формат ATOM                                                                                                                                    |
| delivery.date_to                                 | string             | (optional) Конец предполагаемого магазином диапазона времени доставки. Формат ATOM                                                                                                                                     |
| delivery.date_range                              | object             | Диапазон дат для доставки (только в статусе "processing")                                                                                                                                                              |
| delivery.date_range.from                         | string             | Дата от YYYY-MM-DD                                                                                                                                                                                                     |
| delivery.date_range.to                           | string             | Дата до YYYY-MM-DD                                                                                                                                                                                                     |
| shop_comments_count                              | integer            | Количество внутренних комментариев магазина к заказу                                                                                                                                                                   |
| payment                                          | object/null        | Блок с информацией о способе оплаты и ее статусе                                                                                                                                                                       |
| payment.type                                     | string             | Способ оплаты, выбранный пользователем                                                                                     (возможные значения: online, cash, terminal, cashless, by_parts, halva, for_national_goods) |
| payment.status                                   | string             | Статус онлайн-оплаты                                                                                                                                                                                                   |
| by_parts_info                                    | object (optional)  | Информация об оплате частями, отсутствует если `payment.type` не равен `by_parts`                                                                                                                                      |
| by_parts_info.term                               | int                | Срок платежей                                                                                                                                                                                                          |
| by_parts_info.monthly_payment                    | money              | Информация о ежемесячном платеже                                                                                                                                                                                       |
| comment                                          | string             | Общий комментарий к данному заказу                                                                                                                                                                                     |
| order_cost                                       | money              | Общая стоимость заказа с доставкой с учетом скидок                                                                                                                                                                     |
| order_price                                      | money              | Общая стоимость заказа с доставкой без учета скидок                                                                                                                                                                    |
| order_discount                                   | money/null         | Общая скидка на весь заказ                                                                                                                                                                                             |
| totals                                           | object             | Информация о стоимости                                                                                                                                                                                                 |
| totals.delivery                                  | object             | Стоимость доставки                                                                                                                                                                                                     |
| totals.delivery.price                            | money              | Стоимость доставки без учета скидки                                                                                                                                                                                    |
| totals.delivery.discount                         | money              | Скидка на доставку                                                                                                                                                                                                     |
| totals.delivery.cost                             | money              | Стоимость доставки с учетом скидки                                                                                                                                                                                     |
| totals.original                                  | object             | Стоимость заказа                                                                                                                                                                                                       |
| totals.original.positions                        | object             | Инфомация о стоимости позиций без учета доставки                                                                                                                                                                       |
| totals.original.positions.price                  | money              | Стоимость позиций без учета скидки                                                                                                                                                                                     |
| totals.original.positions.discount               | money              | Скидка по позициям                                                                                                                                                                                                     |
| totals.original.positions.cost                   | money              | Стоимость позиций с учетом скидки                                                                                                                                                                                      |
| totals.original.price                            | money              | Общая стоимость заказа с доставкой без учета скидок                                                                                                                                                                    |
| totals.original.discount                         | money              | Общая скидка на весь заказ                                                                                                                                                                                             |
| totals.original.cost                             | money              | Общая стоимость заказа с доставкой с учетом скидок                                                                                                                                                                     |
| totals.original.overpayment                      | money              | Информация о переплате по заказу, если при оплате использован кредит                                                                                                                                                   |
| totals.original.overall                          | money              | Информация о стоимости заказа с учётом переплаты по кредиту                                                                                                                                                            |
| totals.delivered                                 | object             | Стоимость принятого заказа                                                                                                                                                                                             |
| totals.delivered.positions                       | object             | Инфомация о стоимости принятых позиций без учета доставки                                                                                                                                                              |
| totals.delivered.positions.price                 | money              | Стоимость принятых позиций без учета скидки                                                                                                                                                                            |
| totals.delivered.positions.discount              | money              | Скидка по принятым позициям                                                                                                                                                                                            |
| totals.delivered.positions.cost                  | money              | Стоимость принятых позиций с учетом скидки                                                                                                                                                                             |
| totals.delivered.price                           | money              | Общая стоимость принятого заказа с доставкой без учета скидок                                                                                                                                                          |
| totals.delivered.discount                        | money              | Общая скидка на весь принятый заказ                                                                                                                                                                                    |
| totals.delivered.cost                            | money              | Общая стоимость принятого заказа с доставкой с учетом скидок                                                                                                                                                           |
| totals.original.overpayment                      | money              | Информация о переплате по принятому заказу, если при оплате использован кредит                                                                                                                                         |
| totals.original.overall                          | money              | Информация о стоимости принятого заказа с учётом переплаты по кредиту                                                                                                                                                  |
| delivered_order_cost                             | money              | Общая стоимость принятого заказа с доставкой с учетом скидок                                                                                                                                                           |
| installment_info                                 | object/null        | Информация о рассрочке                                                                                                                                                                                                 |
| installment_info.amount_per_month                | money              | Информация о сумме ежемесячного платежа                                                                                                                                                                                |
| permissions                                      | object             | Права доступа для заказа                                                                                                                                                                                               |
| permissions.delete                               | bool               | Можно ли удалить заказ                                                                                                                                                                                                 |

#### Описание блока с информацией о ценовой позиции (каждый объект в массиве positions)

| Параметр                        | Тип         | Описание                                                                                                                                       |
|---------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| entry_id                        | integer     | Идентификатор позиции в заказе                                                                                                                 |
| article                         | string/null | Артикул товара                                                                                                                                 |
| quantity                        | integer     | Количество товаров, заказанных в рамках данной позиции                                                                                         |
| delivered_quantity              | integer     | Принятое покупателем количество единиц товара, если отличается от заказанного количества (если способ оплаты “Картой Online”, “Картой Клевер”) |
| position_price                  | money       | Информация о стоимости ценового предложения с учётом скидки                                                                                    |
| regular_price                   | money       | Информация о стоимости позиции (1 шт.) без учёта скидки                                                                                        |
| position_discount               | money/null  | Информация о скидке позиции (1 шт.)                                                                                                            |
| cost                            | money       | Информация о стоимости позиции с учётом количества единиц позиции и c учётом скидки                                                            |
| price                           | money       | Информация о стоимости позиции с учётом количества единиц позиции и без учёта скидки                                                           |
| discount                        | money/null  | Информация о скидке позиции с учётом количества единиц позиции                                                                                 |
| delivered_cost                  | money       | Информация о стоимости позиции с учётом количества доставленных единиц позиции и c учётом скидки                                               |
| delivered_price                 | money       | Информация о стоимости позиции с учётом количества доставленных единиц позиции и без учёта скидки                                              |
| delivered_discount              | money/null  | Информация о скидке позиции с учётом количества доставленных единиц позиции                                                                    |
| undelivered_cost                | money       | Информация о стоимости позиции с учётом количества недоставленных единиц позиции и c учётом скидки                                             |
| undelivered_price               | money       | Информация о стоимости позиции с учётом количества недоставленных единиц позиции и без учёта скидки                                            |
| undelivered_discount            | money/null  | Информация о скидке позиции с учётом количества недоставленных единиц позиции                                                                  |
| is_credit                       | boolean     | Флаг доступности покупки в кредит (1 - можно, 0 - нет)                                                                                         |
| is_cashless                     | boolean     | Флаг предложения для юридических лиц (1 - для юридических, 0 - для физических)                                                                 |
| warranty                        | integer     | Срок гарантии на товар (в месяцах)                                                                                                             |
| comment                         | string      | Комментарий продавца к данному предложению                                                                                                     |
| producer                        | string      | Сведения о производителе товара                                                                                                                |
| importer                        | string      | Сведения об импортере товара на территорию РБ                                                                                                  |
| service_centers                 | string      | Сведения о сервисном центре                                                                                                                    |
| delivery.town.delivery_price    | money       | __(deprecated)__ Стоимость доставки в пределах г. Минска (если null - бесплатно)                                                               |
| delivery.town.time              | integer     | __(deprecated)__ Срок доставки в пределах г. Минска (в днях) (если не указано - доставка не осуществляется)                                    |
| delivery.country.delivery_price | money       | __(deprecated)__ Стоимость доставки в пределах РБ (если null - бесплатно)                                                                      |
| delivery.country.time           | integer     | __(deprecated)__ Срок доставки в пределах РБ (в днях) (если не указано - доставка не осуществляется)                                           |
| position_id                     | string      | Идентификатор ценового предложения                                                                                                             |

#### Описание блока с информацией о товаре (объект product в теле объекта position) 

| Параметр                | Тип     | Описание                                                |
|-------------------------|---------|---------------------------------------------------------|
| id                      | integer | Числовой идентификатор товара                           |
| key                     | string  | Строковый идентификатор товара                          |
| name                    | string  | Краткое наименование товара                             |
| full_name               | string  | Полное наименование товара                              |
| images                  | object  | Объект со ссылками на главное изображение товара        |
| images.header           | string  | URL к изображению товара                                |
| description             | string  | Описание товара (краткая строка)                        |
| micro_description       | string  | Краткая-краткая строка)                                 |
| html_url                | string  | Ссылка на страницу товара                               |
| reviews.create_html_url | string  | Ссылка на страницу создания отзыва на товар             |
| url                     | string  | Ссылка на catalog.api для получения информации о товаре |

Если получить информацию о товаре не удалось, блок будет содержать только числовой и строковый идентификаторы товара.

- Блок с информацией о магазине содержит номер магазина, его название и ссылку на логотип. В некоторых случаях блок будет содержать только номер магазина.

#### Описание блока с информацией об акциях, примененных к заказу

| Параметр                                                                       | Тип    | Описание                                                                                                                        |
|--------------------------------------------------------------------------------|--------|---------------------------------------------------------------------------------------------------------------------------------|
| promotions                                                                     | object | Объект с информацией по акциям                                                                                                  |
| promotions.mastercard_free_delivery                                            | object | (optional) Объект с информацией по акции "Бесплатная доставка от мастеркард". Не возвращается, если акция не применена к заказу |
| promotions.mastercard_free_delivery.order_cost                                 | money  | Информация о стоимости заказа по акции                                                                                          |
| promotions.mastercard_free_delivery.delivered_order_cost                       | money  | Информация о стоимости заказа с учётом фактически доставленных товаров и стоимости доставки по акции                            |
| promotions.mastercard_free_delivery.delivery.price                             | money  | Стоимость доставки по акции                                                                                                     |
| promotions.mastercard_free_delivery.installment_info                           | object | (optional) Информация о рассрочке по акции. Возращается, если заказ создан с оплатой в рассрочку                                |
| promotions.mastercard_free_delivery.installment_info.amount_per_month          | money  | Информация о сумме ежемесячного платежа по акции                                                                                |

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

| Параметр | Ошибки                                                      |
|----------|-------------------------------------------------------------|
| include  | Поле обязательно для заполнения                             |
| include  | Значение поля должно быть строкой                           |
| include  | Неправильный набор названий групп дополнительной информации |
