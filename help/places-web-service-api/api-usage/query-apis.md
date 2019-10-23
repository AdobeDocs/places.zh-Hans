---
title: 概述
seo-title: 查询API
description: 了解和使用查询API。
seo-description: 了解和使用查询API。
translation-type: tm+mt
source-git-commit: 26b0cab7bdada26a7598b20623095b72f7c8d334

---



# 查询API

一种GET方法，它允许您查询最接近呼叫者的POI。

## 请求

```text
GET https://query.places.adobe.com/placesedgequery
```

通过以下输入，服务会返回最接近呼叫者的POI列表：

* 调用者的位置\(latitude, longitude\)。
* 要包含在搜索中的POI库的ID。
* 要返回的最大POI数。  默认值为 100。

   呼叫者与POI之间的距离定义为从呼叫者到POI地理围栏边缘的距离。 在响应中，包含呼叫者的POI将被标为有呼叫者。

参数将作为以下查询参数提供：

* (**Required**) `latitude`

   拨叫者的纬度，必须介于-85到85之间。
* (**Required**) `longitude`

   调用者的经度，它必须介于-180和180之间。

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

下面的POI `places.pois` 按从呼叫者到POI边缘的距离排序。 POI下包 `places.userWithin` 含调用者，这些POI按排名排序，然后按增加radius排序。

## 示例调用

以下是调用的示例：

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
