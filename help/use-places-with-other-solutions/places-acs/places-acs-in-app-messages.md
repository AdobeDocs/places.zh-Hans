---
title: Places service的应用程序内消息
description: 本节提供有关如何在Campaign standard中将推送消息与Campaign standard中的应用程序内消息结合使用的信息。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Places service的应用程序内消息传递 {#in-app-messages-loc-service}

此信息可帮助您了解如何使用Places service信息发送应用程序内消息或本地通知。

## 先决条件

在开始之前，请完成以下任务：

* 使用Adobe Experience Platform Mobile SDK配置移动应用程序，包括 [Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 将 [Adobe Experience Platform Mobile SDK集成到您的应用程序](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
* 将 [Adobe Campaign Standard Extension添加到您的移动应用程序配置中](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。

* [在Places Service](/help/poi-mgmt-ui/create-a-poi-ui.md) POI管理界面中创建POI。

* 在您的移动应用程 [序中安装和配置](/help/places-ext-aep-sdks/places-extension/places-extension.md)[Places扩展和Places Monitor扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) 。

## 根据地理围栏进入或退出发送应用程序内消息

1. 在您的Adobe Campaign standard实例中，单击 **[!UICONTROL Create In-App message]**。
1. 对于消息类型，选择 **[!UICONTROL Target all users of a Mobile application]**。
1. 单击 **[!UICONTROL Next]**并键入常规详细信息。
1. 在左窗格中，验证是否可以使用与Places services相关的各种触发器。

   * 如果用户已输入POI地理围栏，则可以选择显示应用程序内消息。
   * 您还可以使用在Places Services UI中定义的元数据筛选受众。
   在以下示例中，您可以触发仅向参加免费饮料计划的度假胜地之一的用户显示的应用程序内消息，并且您希望在这些用户到达时向其发送优惠券。

   ![“应用程序内消息放置元数据”](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]**to finish creating the In-app message for delivery.

   ![“创建活动”](/help/assets/prepare-ACS.png)

   要测试应用程序内消息传送，请在Xcode或Android Studio中启动应用程序，并使用位置模拟器选择符合消息传送条件的POI。

   ![“饮料优惠券”](/help/assets/drink-coupon-on-app.png)

将Places Services与Adobe Campaign standard结合使用，为您提供了一个功能强大的工具，可根据地理围栏条目和退出情况将消息细分和定向给用户。 此集成允许您构建更加个性化和情境化的使用案例。

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)