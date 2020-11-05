## Получить детальную информацию о населенном пункте по ID

### GET https://geo.api.onliner.by/towns/{id}

### Пример запроса

```http
GET https://geo.api.onliner.by/towns/17030
Accept: application/json; charset=utf-8
```

### Ответ при успешном запросе

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```json
{
    "id":17030,
    "name":"Минск",
        "type":{
        "id":"city",
        "short_name":"г.",
        "full_name":"город"
    },
    "village_council":"",
    "is_district_center":true,
    "is_region_center":true,
    "center":{
        "lat":53.904639,
        "lon":27.553556
    },
    "district":{
        "id":636,
        "name":"Минский",
        "type":{
          "id":"district",
          "short_name":"р-н",
          "full_name":"район"
        }
    },
    "region":{
        "id":6,
        "name":"Минская",
        "type":{
            "id":"region",
            "short_name":"область",
            "full_name":"обл."
        }
    }
}
```

### Описание полей ответа

|Параметр|Тип|Описание|
|---|---|---|
|id|integer|ID населенного пункта|
|name|string|Название населенного пункта|
|type.id|string|Строковый ID типа|
|type.short_name|string|Краткое название типа|
|type.full_name|string|Полное название типа|
|village_council|string|Сельсовет|
|is_district_center|boolean|True, если город - центр района|
|is_region_center|boolean|True, если город - центр области|
|center|object &#124; null|Координаты центра населенного пункта|
|center.lat|float|Широта|
|center.lon|float|Долгота|
|district.id|integer|ID района|
|district.name|string|Название района|
|district.type.id|string|Строковый ID типа|
|district.type.short_name|string|Краткое название типа|
|district.type.full_name|string|Полное название типа|
|region.id|integer|ID области|
|region.name|string|Название области|
|region.type.id|string|Строковый ID типа|
|region.type.short_name|string|Краткое название типа|
|region.type.full_name|string|Полное название типа|

### Ответ в случае, если населенный пункт не найден

```http
HTTP/1.1 404 Not Found
Content-Type: application/json; charset=utf-8
```
```json
{
    "message":"Not Found"
}
```
