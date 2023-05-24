---
title: 删除多个POI
description: 使用批处理API删除多个POI。
exl-id: f170b722-e6f4-42a2-b3a6-1bf56965eb17
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 8%

---

# 删除多个POI {#delete-multiple-pois}

一种POST方法，可让您删除多个POI。

## 请求

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## 标头

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## 正文

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## 示例响应

```text
If successful a Status of "204 No Content" is returned.
```

## CURL命令

使用以下CURL命令测试此API：

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Replace `<API KEY>`， `<TOKEN>`， `<ORGID>`、和 `<PATHTOBATCHDELETEJSONFILE>` 实数值。

## 示例JSON文件

以下是的示例JSON文件 `batchDelete` API：

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
