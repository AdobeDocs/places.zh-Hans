---
title: 常见问题解答
description: 本主题提供了一些常见问题的其他相关信息。
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# 常见问题解答

以下是有关Places Service的一些信息和常见问题解答。

## 在v4 SDK中从trackLocation迁移

如果您从v4 SDK迁移，并正在查找 `trackLocation` API，请参阅主题 [不使用活动区域监控的Places服务](use-places-without-active-monitoring.md).

## 大小和可靠性

请务必注意，在从移动设备应用程序进行区域监控时，无论使用的是Adobe还是其他某些服务，都会使用所有地理围栏。 操作系统建议在创建地理围栏时应记住一些参数。 要获得最大可靠性，地理围栏的半径应至少为100米。 可以创建较小的地理围栏，但是可能不会生成登入和退出事件，或者可能会在用户停止移动一段时间后生成该事件。

此外，可基于诸如wi-fi被关闭或不可用等硬件条件以及基于设备相对于妨碍GPS信号的位置来降低精确度和可靠性。 例如，山区、城市设置和室内区域会降低iOS和Android操作系统的位置准确性。

## 退出事件如何触发？

实施的区域监视器应请求附近POI的列表。 收到后，应在操作系统中为每个POI注册一个区域。 现在，操作系统负责在设备跨越某个监控区域的边界（进入或退出）时通知SDK。 仅当操作系统通知SDK发生退出事件时，SDK才会触发退出事件。 此通知的主要原因是位置数据的时间敏感性。

如果设备离开区域时操作系统无法交付退出事件，则SDK更安全的做法是只忽略退出事件。 如果SDK制作退出事件，而且没有操作系统触发该事件，则可能会在设备接近POI的时间段之外，很好地处理退出事件。

## POI数量

在Places Service POI管理界面中，客户在特定库中最多可添加15万个目标点。 客户可以定义多个库，以根据需要对POI分组进行分段。

## 关于位置更改和活动区域监控的一些说明

在注册授权应用程序后，将立即开始监控地理区域。 但是，不要期望立即收到事件，因为只有边界交叉点才会生成事件。 特别是，如果用户的位置在注册时已位于区域内，则位置管理器不会自动生成事件。 而是，您的应用程序必须等待用户越过区域边界后，才能生成事件并将其发送到代理。

指定要监视的区域集时要谨慎。 区域是共享的系统资源，系统范围内可用区域的总数有限。 因此，核心位置限制为可由单个应用程序同时监控的区域数量为20个。 要绕过此限制工作，请考虑仅在用户附近注册这些区域。

[请参阅Apple开发人员网站上的其他信息] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
