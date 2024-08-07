---
title: 更新库
description: 使用Places REST API更新库。
exl-id: 37ca2be2-39e1-4f8e-87c2-ef4cb366db0d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 6%

---

# 更新库 {#update-a-library}

一种PUT方法，可让您更新库。

## 请求

```text
PUT https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
```

## 标头

```text
-H' Content-Type: application/json'  -H 'Authorization: bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 正文

```text
{"name": "<NEW_LIBRARY_NAME>"}
```

## 示例响应

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL命令

使用以下CURL命令测试此API：

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>将变量（如`<lIBRARYID>`、`<API KEY>`、`<TOKEN>`和`<ORGID>`）替换为实际值。
