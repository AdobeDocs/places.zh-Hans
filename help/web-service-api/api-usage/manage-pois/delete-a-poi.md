---
title: 删除POI
description: 使用Places REST API删除POI。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 6%

---


# 删除POI {#delete-a-poi}

一种DELETE方法，可让您删除POI。

## 请求

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
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
If successful a Status of "204 No Content" is returned.
```

## CURL命令

使用以下CURL命令测试API:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>用实 `<POIID>`际 `<API KEY>`值替 `<TOKEN>`换、 `<ORGID>` 和、和。

