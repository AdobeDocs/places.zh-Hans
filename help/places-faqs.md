---
title: 常见问题
description: 本主题提供有关一些常见问题的其他信息。
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
TQID: https://experienceleague.adobe.com/LL9eLMDJaq8ZmeiZxv28QZoqXL1A0QKZ-DvTDUx4Gnw
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 557
ht-degree: 1%

---

# 常见问题

以下是有关Places Service的一些信息和常见问题解答。

## 从v4 SDK中的trackLocation迁移

如果您要从v4 SDK迁移并查找`trackLocation` API的替代项，请参阅主题[不使用活动区域监视的Places服务](use-places-without-active-monitoring.md)。

## 大小和可靠性

请务必注意，无论使用的是Adobe还是其他服务，移动应用程序都在区域监视中使用所有地理围栏。 操作系统建议在创建地理围栏时要牢记的一些参数。 要获得最大的可靠性，地理围栏的半径应至少为100米。 可以创建较小的地理围栏，但可能不会生成进入和退出事件，或者可能在用户停止移动一段时间后生成进入和退出事件。

此外，可根据硬件条件（例如Wi-Fi被关闭或不可用）以及根据设备相对于阻碍GPS信号的位置来降低精度和可靠性。 例如，山区、城市设置和室内区域可能会降低iOS和Android操作系统的位置准确度。

## 退出事件如何触发？

实施的区域监视器应请求附近POI的列表。 收到后，应在操作系统中为每个POI注册一个区域。 现在，操作系统负责在设备跨越监视区域之一的边界（进入或退出）时通知SDK。 仅当操作系统通知SDK已发生退出事件时，SDK才会触发该事件。 此通知的主要原因是位置数据的时间敏感性。

如果操作系统无法在设备离开某个区域时投放退出事件，SDK只需忽略退出事件就更安全了。 如果SDK制造退出事件时操作系统未触发该事件，则存在这样的风险：即退出事件的处理时间可能远远超出设备接近POI的时段。

## POI数量

在Places服务POI管理界面中，客户可以在特定库中添加多达15万个目标点。 如果需要，客户可以定义多个库以分段POI分组。

## 有关位置更改和活动区域监视的一些说明

注册授权应用程序后，将立即开始监控地理区域。 但是，不要期望立即收到事件，因为只有边界交叉点才会生成事件。 特别是，如果在注册时用户的位置已经在区域内，则位置管理器不会自动生成事件。 相反，您的应用程序必须等待用户跨越区域边界，然后才能生成事件并将其发送到代理。

在指定要监视的区域集时务必谨慎。 区域是共享的系统资源，并且系统范围内可用的区域总数是有限的。 因此，核心位置将单个应用程序可同时监视的区域数量限制为20。 要解决此限制，请考虑仅注册用户紧邻的那些区域。

[查看Apple开发人员网站上的其他信息] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
