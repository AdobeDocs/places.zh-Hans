---
title: 地点活动引用
seo-title: 地点活动引用
description: '由“地点”扩展处理的事件列表。 '
seo-description: '由“地点”扩展处理的事件列表。  '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# 地点活动引用 {#places-event-reference}

以下是由“地点”扩展处理的事件列表。

## GetCurrentPointsOfInterest

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 地点 | REQUEST_CONTENT | `requestgetuserwithinplaces` | True |

**事件描述**

此事件是检索设备当前所在POI的请求。

**数据有效负载定义**

不适用

## GetEncorredPointsOfInterest

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 地点 | REQUEST_CONTENT | `requestgetnearbyplaces` | True |

**事件描述**

此事件是一个请求，它通过考虑当前设备位置和配置的地点库来获取附近的POI。

**数据有效负载定义**

| 键 | 值类型 | 必需 | 默认值 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| 纬度 | 双精度 | true | 不适用 | 保留附近POI搜索中心的纬度值。 |
| 经度 | 双精度 | true | 不适用 | 保存附近POI的搜索中心的经度值。 |
| 半径 | 整数 | false | 不适用 | 搜索附近POI时使用的半径（以米为单位）。 |
| count（计数） | 整数 | false | 10 | 返回结果响应事件的最大POI数。 |

## ProcessRegionEvent

**事件详细信息**

| 类型 | 来源 | 名称 | 已配对 |
| :--- | :--- | :--- | :--- |
| 地点 | REQUEST_CONTENT | `requestprocessregionevent` | False |

**事件描述**

此事件会导致“地点”扩展处理地理围栏进入或退出事件。

**数据有效负载定义**

| 键 | 值类型 | 必需 | 描述 |
| :--- | :--- | :--- | :--- |
| 区域 | 字符串 | true | 生成事件的区域的ID。 |
| regitoneventtype | int | true | 正在生成的区域事件的类型。 1表示进入，2表示退出。 |

## 由Places扩展调度的事件

此信息当前正在进行中。

