---
title: 标题和参数
description: Places服务REST API中可用的标头和参数。
exl-id: 3c7e76de-f0ff-4966-a3ec-7f64d819c140
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 19%

---

# 标题和参数 {#headers-and-parameters}

以下是Places服务REST API中可用的标头和参数的详细信息：

## 支持的标头

| 标头 | 描述 | 方法 | 示例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | 您的持有者令牌 | 全部 |  |
| `x-api-key` | 您的API密钥 | 全部 | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 您的组织ID | 全部 | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 发送或接收内容的格式 | PUT、POST | `application/json` |
| `Accept-Language` | 用于错误消息的语言 | 可选 | `en-US` |

## 库参数

| 参数 | 描述 | 类型 | 限制 | 请求或响应 | 示例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | 库的ID | 已指定 | 不适用 | 响应 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | 库的名称 | 字符串 | 256 个字符 | 两者，在请求中必需 | `"name": "Amazing Places"` |
| `orgID` | 组织的Experience Cloud orgID | 已指定 | 不适用 | 响应 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | 库中的目标点数量 | 整数 | 最多150,000 | 响应 | `"poiCount": 25149` |
| `metadataDescriptors` | 每个唯一POI元数据键值对的计数 | 混合 | 不适用 | 响应 |  |
| `poiCountInCities` | 每个唯一POI城市值的计数 | 混合 | 不适用 | 响应 |  |

## POI参数

| 参数 | 描述 | 类型 | 限制 | 请求或响应 | 示例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi数据 | poi详细信息数组 | 不适用 | 两者 |  |
| `id` | POI ID | 已指定 | 不适用 | 响应 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POI的名称 | 字符串 | 512 个字符 | 二者，可选\* | `"name": "My Favorite Place"` |
| `description` | POI描述 | 字符串 | 512 个字符 | 二者，可选\* | `"description": "This is a very good place."` |
| `location` | POI的类型和坐标数组 | 数组（混合） | 不适用 | 两者 | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI类型 | 字符串 | 当前仅支持“点” | 两者，在请求中必需 | `"type": "Point"` |
| `coordinates` | POI的经度和纬度数组 | 数组（浮点数） | 经度：-180至180，纬度–85至85 | 两者，在请求中必需 | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI周围圆形地理围栏的大小 | float | 10 - 2000米 | 两者，在请求中必需 | `"radius": 100` |
| `country` | 目标国家/地区 | 字符串 | 32 个字符 | 二者，可选* | `"country": "United States"` |
| `state` | 目标点(POI)所在州 | 字符串 | 32 个字符 | 二者，可选* | `"state": "California"` |
| `city` | 目标城市 | 字符串 | 32 个字符 | 二者，可选* | `"city": "San Jose"` |
| `street` | POI的街道地址 | 字符串 | 256 个字符 | 二者，可选* | `"street": "122 Woz Way"` |
| `category` | POI的类别 | 字符串 | 100 个字符 | 二者，可选* | `"category": "cafe"` |
| `icon` | POI图标 | 字符串 | 50 个字符 | 二者，可选* | `"icon": "star"` |
| `color` | POI颜色 | 字符串 | 8 个字符 | 二者，可选* | `"color": "blue"` |
| `metadata` | POI的键/值对数组 | array(string) | 密钥：256个字符，值：256个字符，最多10对 | 二者，可选* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POI所在的库的ID | 不适用 | 不适用 | 两者，必需 | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* 如果未包含参数值，则数据库中将该值设置为`empty`。 如果不包含现有的键/值对，则会删除数据库中该POI的键/值对。
