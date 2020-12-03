---
title: 关于 Experience Cloud 核心服务
description: 本主题提供了有关一些常见问题的其他信息。
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 1%

---


# 关于 Experience Cloud 核心服务

以下是有关Places Service的一些信息和常见问题。

## 从v4 SDK中的trackLocation迁移

如果您是从v4 SDK迁移并正在寻找对API的替 `trackLocation` 换，请参阅主题“不使用活 [动区域监视的Places Service](use-places-without-active-monitoring.md)”。

## 大小和可靠性

注意，无论使用Adobe或其他服务，从移动应用程序进行区域监视时使用的所有地理围栏都很重要。 操作系统建议在创建地理围栏时记住一些参数。 为获得最高可靠性，地理围栏的半径至少应为100米。 可以创建较小的地理围栏，但进出事件可能不会生成，也可能在用户停止移动一段时间后生成。

此外，可基于诸如wi-fi被关闭或不可用等硬件条件，并且也基于与妨碍GPS信号有关的设备的位置，降低准确性和可靠性。 例如，山区、城市设置和室内区域可以降低iOS和Android操作系统的定位精度。

## 退出事件如何触发？

当位置监视器(SDK)获得附近POI的新列表时，它会为每个POI在操作系统中注册一个区域。 现在，操作系统负责在设备跨越一个监视区域的边界（入口或出口）时通知SDK。 仅当操作系统通知SDK事件已发生时，SDK才触发退出事件。 此通知的主要原因是位置数据的时间敏感性。

如果设备离开某个区域时操作系统无法传送退出事件，则SDK更安全的做法是忽略退出事件。 如果SDK制作退出事件，而事件未由操作系统触发，则存在在设备接近POI的时间段之外，可能会处理完毕的退出事件。

## POI数

在Places Service POI管理界面中，客户可以在特定库中添加多达15万个兴趣点。 客户可以定义多个库，以根据需要对POI分组进行细分。

## 关于位置变化和活动区域监控的注意事项

注册授权应用程序后，将立即开始监控地理区域。 但是，不要期望立即收到事件，因为只有边界交叉才会生成事件。 特别是，如果注册时用户的位置已在区域内，位置管理器不会自动生成事件。 而是，您的应用程序必须等待用户跨越区域边界，然后才能生成事件并将其发送到委托。

指定要监视的区域集时要谨慎。 区域是共享的系统资源，系统范围内可用区域总数有限。 因此，核心位置限制为单个应用程序可同时监视的区域数为20。 要绕过此限制，请考虑仅在用户附近注册这些区域。

[请参阅Apple开发人员站点上的其他信息] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
