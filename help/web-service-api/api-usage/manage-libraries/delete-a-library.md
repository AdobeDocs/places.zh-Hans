---
title: 删除库
description: 使用Places REST API删除库。
exl-id: ad45ea38-9e12-43d7-b05f-17d3e40abaf5
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 8%

---

# 删除库 {#delete-a-library}

一种DELETE方法，可让您删除库。

## 请求

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

使用以下CURL命令测试此API：

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>替换变量，例如 `<lIBRARYID>`， `<API KEY>`， `<TOKEN>`、和 `<ORGID>`具有实际值。
