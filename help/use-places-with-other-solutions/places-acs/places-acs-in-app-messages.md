---
title: 使用Places服务的应用程序内消息
description: 本节提供了有关如何在Campaign Standard中将推送消息与Campaign Standard中的应用程序内消息结合使用的信息。
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# 使用Places服务的应用程序内消息传递 {#in-app-messages-loc-service}

此信息可帮助您了解如何使用Places服务信息发送应用程序内消息或本地通知。

## 先决条件

在开始之前，请完成以下任务：

* 已使用Adobe Experience Platform Mobile SDK配置移动应用程序，包括[Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 将[Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)集成到您的应用程序中。
* 将[Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)添加到您的移动应用配置中。

* [在Places服务POI管理界面中创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。

* 在您的移动应用程序中安装和配置[Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)和区域监视解决方案([CoreLocation文档](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions)(适用于iOS)，或[Android位置文档](https://developer.android.com/training/location/geofencing))。

## 根据地理围栏进入或退出发送应用程序内消息

1. 在您的Adobe Campaign Standard实例中，单击&#x200B;**[!UICONTROL 创建应用程序内消息]**。
1. 对于消息类型，请选择&#x200B;**[!UICONTROL 定位移动应用程序的所有用户]**。
1. 单击&#x200B;**[!UICONTROL 下一步]**&#x200B;并键入常规详细信息。
1. 在左窗格中，验证是否可以使用与Places服务相关的各种触发器。

   * 如果用户输入了POI地理围栏，则可以选择显示应用程序内消息。
   * 您还可以使用Places Services UI中定义的元数据来筛选受众。

   在下面的示例中，您可以触发一个应用程序内消息，该消息仅向输入某个参与免费饮料计划的度假胜地的用户显示，并且您希望在那些用户到达时向他们发送优惠券。

   ![“应用程序内消息放置元数据”](/help/assets/last-entered-vacation.png)

1. 单击&#x200B;**[!UICONTROL 下一步]**&#x200B;以完成创建要交付的应用程序内消息。

   ![“创建事件”](/help/assets/prepare-ACS.png)

   要测试应用程序内消息投放，请在Xcode或Android studio中启动应用程序，然后使用位置模拟器选择符合消息传递条件的POI。

   ![“饮料优惠券”](/help/assets/drink-coupon-on-app.png)

通过将Places服务与Adobe Campaign Standard结合使用，您可以根据地域限制登录和退出来细分消息并将消息定位到用户。 此集成允许您构建更加个性化和情境化的用例。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

带有Campaign消息的[Adobe Experience Platform位置服务](https://www.youtube.com/watch?v=ikiTTQw9c-o)
