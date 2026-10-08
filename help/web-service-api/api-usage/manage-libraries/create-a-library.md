---
title: 创建库
description: 使用Places REST API创建库。
exl-id: 155cc6e6-9254-4389-bb02-e526d15908f4
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 18%
---
# 创建库 {#create-a-library}

一种POST方法，可让您创建库。

## 请求

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## 标头

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 正文

```text
{"name": "<LIBRARY_NAME>"}
```

## 示例响应

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL命令

使用以下CURL命令测试此API：

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>将变量（如`<API KEY>`、`<TOKEN>`和`<ORGID>`）替换为实际值。
