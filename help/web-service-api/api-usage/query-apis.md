---
title: 概述
description: 了解并使用查询API。
exl-id: cc61a49c-1cf2-407f-b81a-3d38fcb622cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 3%

---

# 查询API

一种GET方法，允许您查询最接近调用方的POI。

## 请求

```text
GET https://query.places.adobe.com/placesedgequery
```

使用以下输入，服务将返回最接近调用方的POI列表：

* 调用方的位置（纬度、经度）。
* 要包含在搜索中的POI库的ID。
* 要返回的最大POI数。  默认值为 100。

  主叫方和POI之间的距离定义为从主叫方到POI地理围栏边缘的距离。 在响应中，包含呼叫者的POI将标记为具有呼叫者。

参数作为以下查询参数提供：

* （**必需**） `latitude`

  呼叫者的纬度，必须介于–85和85之间。
* （**必需**） `longitude`

  调用方的经度，必须介于–180和180之间。

* （**可选**） `limit`

  要返回的最大POI数。

* （**必需**） `library`

  要查询的库的ID。 要查询多个库，请确保在查询中包含库参数的多个副本。

以下是成功返回的JSON格式示例：

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

`places.pois`下的POI按调用方到POI边缘的距离排序。 `places.userWithin`下的POI包含调用方，这些POI先按等级排序，然后按半径递增。

## 示例调用

以下是调用的示例：

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
