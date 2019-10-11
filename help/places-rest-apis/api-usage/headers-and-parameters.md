---
title: 标题和参数
seo-title: 标题和参数
description: Places REST API中可用的标题和参数。
seo-description: Places REST API中可用的标题和参数。
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 标题和参数 {#headers-and-parameters}

以下是Places REST API中可用的标题和参数的详细信息：

## 支持的标题

| Header | 描述 | 方法 | 示例 |
| :--- | :--- | :--- | :--- |
| `Authorization` | 您的持牌令牌 | 所有 |  |
| `x-api-key` | 您的API密钥 | 所有 | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | 您的组织ID | 所有 | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | 发送或接收内容的格式 | PUT, POST | `application/json` |
| `Accept-Language` | 用于错误消息的语言 | 可选 | `en-US` |

## 库参数

| 参数 | 描述 | 类型 | 限制 | 请求或响应 | 示例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | 库的ID | 已分配 | 不适用 | 响应 | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | 库的名称 | 字符串 | 256 个字符 | 两者，请求中必需 | `"name": "Amazing Places"` |
| `orgID` | Experience cloud组织ID | 已分配 | 不适用 | 响应 | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | 图书馆的POI数量 | 整数 | 最多150,000 | 响应 | `"poiCount": 25149` |
| `metadataDescriptors` | 每个唯一POI元数据键值对的计数 | 混合 | 不适用 | 响应 |  |
| `poiCountInCities` | 计算每个唯一POI城市值 | 混合 | 不适用 | 响应 |  |

## POI参数

| 参数 | 描述 | 类型 | 限制 | 请求或响应 | 示例 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi数据 | POI详细信息的数组 | 不适用 | both |  |
| `id` | POI的ID | 已分配 | 不适用 | 响应 | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | POI的名称 | 字符串 | 512 个字符 | both, optional\* | `"name": "My Favorite Place"` |
| `description` | POI的说明 | 字符串 | 512 个字符 | both, optional\* | `"description": "This is a very good place."` |
| `location` | POI的类型和坐标阵列 | 数组（混合） | 不适用 | both | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | POI类型 | 字符串 | 当前仅支持“Point” | 两者，请求中必需 | `"type": "Point"` |
| `coordinates` | POI的经度和纬度阵列 | 数组（浮点） | 经度：-180至180,latitude -85至85 | 两者，请求中必需 | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | POI周围环形几何的大小 | 浮动 | 10 - 2000米 | 两者，请求中必需 | `"radius": 100` |
| `country` | POI的国家／地区 | 字符串 | 32 个字符 | both, optional* | `"country": "United States"` |
| `state` | POI的状态 | 字符串 | 32 个字符 | both, optional* | `"state": "California"` |
| `city` | POI的城市 | 字符串 | 32 个字符 | both, optional* | `"city": "San Jose"` |
| `street` | POI的街道地址 | 字符串 | 256 个字符 | both, optional* | `"street": "122 Woz Way"` |
| `category` | POI的类别 | 字符串 | 100 个字符 | both, optional* | `"category": "cafe"` |
| `icon` | POI的图标 | 字符串 | 50 个字符 | both, optional* | `"icon": "star"` |
| `color` | POI的颜色 | 字符串 | 8 个字符 | both, optional* | `"color": "blue"` |
| `metadata` | POI的键／值对数组 | array(string) | 键：256个字符，值：256个字符，最多10对 | both, optional* | `"metadata": {"region": "Equator"}` |
| `lib_id` | POI所在的库的ID | 不适用 | 不适用 | both, required | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* 如果未包含该参数值，则该值将设置为数 `empty` 据库中。 如果不包括现有键／值对，则会为数据库中的该POI删除键／值对。

