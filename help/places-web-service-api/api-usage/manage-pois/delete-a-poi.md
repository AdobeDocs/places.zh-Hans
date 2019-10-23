---
title: 删除POI
seo-title: 删除POI
description: 使用Places REST API删除POI。
seo-description: 使用Places REST API删除POI。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# 删除POI

允许删除POI的DELETE方法。

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
>将 `<POIID>`、 `<API KEY>``<TOKEN>`和替换 `<ORGID>` 为实际值。

