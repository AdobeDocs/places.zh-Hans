---
title: 地点事件参考
description: '由Places扩展处理的列表的事件。 '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---


# 地点事件参考 {#places-event-reference}

以下是由Places扩展处理的列表事件。

## GetCurrentPointsOfInterest

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 地点 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**事件描述**

此事件是检索设备当前所在的POI的请求。

**数据有效负载定义**

n/a

## GetEnxordPointsOfInterest

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 地点 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**事件描述**

此事件是一个请求，它需要考虑当前设备位置和配置的Places库，以获取附近的POI。

**数据有效负载定义**

| 键 | 值类型 | 必需 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| latitude | 多次 | true | n/a | 保留搜索附近POI的中心的纬度值。 |
| longitude | 多次 | true | n/a | 保存附近POI的搜索中心的经度值。 |
| 半径 | 整数 | false | n/a | 搜索附近的POI所用的半径（以米为单位）。 |
| count | 整数 | false | 10 | 返回结果响应事件的最大POI数。 |

## ProcessRegionEvent

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 地点 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**事件描述**

此事件导致“地点”扩展处理地理围栏进入或退出事件。

**数据有效负载定义**

| 键 | 值类型 | 必需 | 描述 |
| :--- | :--- | :--- | :--- |
| 区域id | 字符串 | true | 生成事件的区域的ID。 |
| 区域事件类型 | int | true | 正在生成的区域事件的类型。 1表示进入，2表示退出。 |

## 事件由Places扩展分派

此信息当前正在进行中。

