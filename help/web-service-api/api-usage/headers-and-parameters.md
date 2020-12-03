---
title: 标题和参数
description: Places Service REST API中可用的标题和参数。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 11%

---


# Headers and parameters {#headers-and-parameters}

以下是Places Service REST API中可用的标题和参数的详细信息：

## 支持的标题

| Header | 描述 | 方法 | 示例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | 您的持牌令牌 | 所有 |  |
| `x-api-key` | 您的API密钥 | 所有 | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 您的组织ID | 所有 | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 发送或接收内容的格式 | PUT,POST | `application/json` |
| `Accept-Language` | 用于错误消息的语言 | 可选 | `en-US` |

## 库参数

| 参数 | 描述 | 类型 | 限制 | 请求或响应 | 示例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | 库的ID | 已分配 | n/a | 响应 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | 库的名称 | 字符串 | 256 个字符 | 两者，请求中必需 | `"name": "Amazing Places"` |
| `orgID` | 组织的Experience Cloud组织ID | 已分配 | n/a | 响应 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | 图书馆的POI数量 | 整数 | 最高150,000 | 响应 | `"poiCount": 25149` |
| `metadataDescriptors` | 每个唯一POI元数据键值对的计数 | 混合 | n/a | 响应 |  |
| `poiCountInCities` | 计算每个唯一POI城市值 | 混合 | n/a | 响应 |  |

## POI参数

| 参数 | 描述 | 类型 | 限制 | 请求或响应 | 示例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi数据 | POI详细信息的数组 | n/a | 两者 |  |
| `id` | POI的ID | 已分配 | n/a | 响应 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POI的名称 | 字符串 | 512 个字符 | 两者，可选\* | `"name": "My Favorite Place"` |
| `description` | POI的说明 | 字符串 | 512 个字符 | 两者，可选\* | `"description": "This is a very good place."` |
| `location` | POI的类型和坐标阵 | 数组（混合） | n/a | 两者 | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI类型 | 字符串 | 当前仅支持“Point” | 两者，请求中必需 | `"type": "Point"` |
| `coordinates` | POI的经纬度阵列 | 数组（浮点） | 经度：-180至180, latitude -85至85 | 两者，请求中必需 | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI周围圆形地震的大小 | 浮 | 10 - 2000米 | 两者，请求中必需 | `"radius": 100` |
| `country` | POI的国家／地区 | 字符串 | 32 个字符 | 两者，可选* | `"country": "United States"` |
| `state` | POI的状态 | 字符串 | 32 个字符 | 两者，可选* | `"state": "California"` |
| `city` | POI的城市 | 字符串 | 32 个字符 | 两者，可选* | `"city": "San Jose"` |
| `street` | POI的街道地址 | 字符串 | 256 个字符 | 两者，可选* | `"street": "122 Woz Way"` |
| `category` | 类别POI | 字符串 | 100 个字符 | 两者，可选* | `"category": "cafe"` |
| `icon` | POI的图标 | 字符串 | 50 个字符 | 两者，可选* | `"icon": "star"` |
| `color` | POI的颜色 | 字符串 | 8 个字符 | 两者，可选* | `"color": "blue"` |
| `metadata` | POI的键／值对的数组 | array(string) | 键：256个字符，值：256个字符，最多10对 | 两者，可选* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POI所在的库的ID | n/a | n/a | 两者，必填 | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* 如果未包含参数值，则该值将设置为数 `empty` 据库中。 如果不包括现有键／值对，则会在数据库中为该POI删除键／值对。

