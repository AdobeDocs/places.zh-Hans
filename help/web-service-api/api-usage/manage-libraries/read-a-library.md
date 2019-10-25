---
title: 阅读库
seo-title: 阅读库
description: 使用Places REST API阅读库。
seo-description: 使用Places REST API阅读库。
translation-type: tm+mt
source-git-commit: 6ae0c8d90cad4c437e1db7f562a0bc9c6b072ce6

---



# 阅读库

返回库详细信息的GET方法。

## 请求

```text
GET https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>
```

## 标题

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## 示例响应

```text
{
    "id": "9aa7f663-35cc-4de6-8643-ae7779f3bb87",
    "name": "Facinating places",
    "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",
    "poiCount": 30,
    "metadataDescriptors": [
        {
            "key": "region",
            "type": "string",
            "value": "Equator",
            "count": 29
        },
        {
            "key": "ownership",
            "type": "string",
            "value": "LS",
            "count": 1
        },
        {
            "key": "brand",
            "type": "string",
            "value": "Coffee Cafe",
            "count": 1
        },
        {
            "key": "Color",
            "type": "string",
            "value": "Blue",
            "count": 1
        }
    ],
    "poiCountInCities": [
        {
            "country": "Ghana",
            "state": "Ghana",
            "city": "Accra",
            "count": 29
        },
        {
            "country": "CN",
            "state": "91",
            "city": "Hong Kong",
            "count": 1
        }
    ]
}
```

## CURL命令

使用以下CURL命令测试API:

```text
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>将 `<LIBRARYID>`、 `<API KEY>``<TOKEN>`和替换 `<ORGID>` 为实际值。

