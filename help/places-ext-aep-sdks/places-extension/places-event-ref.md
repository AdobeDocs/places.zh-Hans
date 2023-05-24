---
title: 地标事件引用
description: 由Places扩展处理的事件列表。
exl-id: 98210ef4-5ff1-4792-b97b-2845ce02e78a
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 28%

---

# 地标事件引用 {#places-event-reference}

以下是Places扩展处理的事件列表。

## GetCurrentPointsOfInterest

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 位置 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**事件描述**

此事件是用于检索设备当前所在的POI的请求。

**数据有效负载定义**

不适用

## GetInnearlyPointsOfInterest

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 位置 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**事件描述**

此事件是获取附近POI的请求，需要考虑当前设备位置和配置的Places库。

**数据有效负载定义**

| 键 | 值类型 | 必需 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| latitude | 多次 | true | 不适用 | 保存搜索附近POI的中心位置的纬度值。 |
| longitude | 多次 | true | 不适用 | 保存搜索附近POI的中心的经度值。 |
| 半径 | 整数 | false | 不适用 | 搜索附近POI所使用的半径（以米为单位）。 |
| count | 整数 | false | 10 | 在生成的响应事件中返回的最大POI数。 |

## ProcessRegionEvent

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 位置 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**事件描述**

此事件会导致Places扩展处理地理围栏进入或退出事件。

**数据有效负载定义**

| 键 | 值类型 | 必需 | 描述 |
| :--- | :--- | :--- | :--- |
| regionid | 字符串 | true | 生成事件的区域的ID。 |
| regioneventtype | int | true | 正在生成的区域事件的类型。 1代表进入，2代表退出。 |

## 由Places扩展调度的事件

此信息目前正在处理中。
