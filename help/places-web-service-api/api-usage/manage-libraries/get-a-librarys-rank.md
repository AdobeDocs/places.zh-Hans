---
title: 获取图书馆的排名
seo-title: 获取图书馆的排名
description: 使用Places REST API获取库的排名。
seo-description: 使用Places REST API获取库的排名。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# 获取图书馆的排名

允许您对库进行排名的GET方法。

## 请求

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## 标题

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## 示例响应

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURL命令

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>用实际值替 `<API KEY>`换 `<TOKEN>`、 `<ORGID>` 和等变量。

