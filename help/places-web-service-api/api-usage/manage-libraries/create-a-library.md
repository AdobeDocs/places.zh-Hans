---
title: 创建库
seo-title: 创建库
description: 使用Places REST API创建库。
seo-description: 使用Places REST API创建库。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---


# 创建库

允许您创建库的POST方法。

## 请求

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## 标题

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 身体

```text
{"name": "<LIBRARY_NAME>"}
```

## 示例响应

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL命令

使用以下CURL命令测试此API:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>用实际值替 `<API KEY>`换 `<TOKEN>`、 `<ORGID>` 和等变量。

