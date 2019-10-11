---
title: 在库上设置排名
seo-title: 在库上设置排名
description: 使用Places REST API在库上设置排名。
seo-description: 使用Places REST API在库上设置排名。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 在库上设置排名

一种PUT方法，它允许您在所有库上设置排名顺序。

## 请求

`PUT https://api-places-dev.adobe.io/places/placesapi/v1/libraries/rank`

## 标题

```-H Content-Type: application/json'
-H 'Authorization: Bearer <TOKEN>`  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## PUT数据

```
"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]  
}
```

## 示例响应

```
{"library_rank_order" ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}
```

## CURL命令

```
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"library_rank_order": ["dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b","ea45781f-26af-44b1-b4f8-43baf5f0fe28"]}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>用实际值替 `<API KEY>`换 `<TOKEN>`、 `<ORGID>` 和等变量。

