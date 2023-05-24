---
title: 删除POI
description: 使用Places REST API删除POI。
exl-id: 0325eb3b-f9b2-4b21-bed8-e318e8072a69
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 9%

---

# 删除POI {#delete-a-poi}

允许您删除POI的DELETE方法。

## 请求

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## 标头

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## 示例响应

```text
If successful a Status of "204 No Content" is returned.
```

## CURL命令

使用以下CURL命令测试API：

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Replace `<POIID>`， `<API KEY>`， `<TOKEN>`、和 `<ORGID>` 具有实际值。
