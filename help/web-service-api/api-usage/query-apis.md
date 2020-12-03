---
title: 概述
description: 了解和使用查询API。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---



# 查询API

一种GET方法，允许您查询最接近呼叫者的POI。

## 请求

```text
GET https://query.places.adobe.com/placesedgequery
```

通过以下输入，服务返回最接近呼叫者的POI的列表:

* 呼叫者的位置（经纬度）。
* 要包含在搜索中的POI库的ID。
* 要返回的最大POI数。  默认值为 100。

   呼叫者与POI之间的距离定义为从呼叫者到POI地序边缘的距离。 在响应中，包含呼叫者的POI将被标记为有呼叫者。

参数作为以下查询参数提供：

* (**Required**) `latitude`

   呼叫者的纬度，必须介于-85和85之间。
* (**Required**) `longitude`

   调用者的经度，必须介于-180和180之间。

* (**可选**) `limit`

   要返回的最大POI数。

* (**Required**) `library`

   要查询的库的ID。 要查询多个库，请确保在查询中包含库参数的多个副本。

以下是成功返回的JSON格式的示例：

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

下面的 `places.pois` POI按呼叫者到POI边缘的距离排序。 下的POI `places.userWithin` 包含调用者，这些POI按排名排序，然后按增加radius排序。

## 示例调用

以下是调用的示例：

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
