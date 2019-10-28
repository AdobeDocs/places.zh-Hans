---
title: 包含位置服务的应用程序内消息
seo-title: 包含位置服务的应用程序内消息
description: 本节提供有关如何在Campaign standard中将推送消息与Campaign standard中的应用程序内消息结合使用的信息。
seo-description: '本节提供有关如何在Campaign standard中将“Push messaging in Campaign Standard”（营销活动标准中的推送消息）与应用程序内消息结合使用的信息。 '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# 与位置服务的应用程序内消息传递 {#in-app-messages-loc-service}

此信息可帮助您了解如何使用Adobe Experience Platform Location service信息发送应用程序内消息或本地通知。

>[!IMPORTANT]
>
>在开始之前，请完成以下任务：
>
>* 使用Adobe Experience Platform Mobile SDK配置移动应用程序，包括 [Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。
   >
   >
* 将 [Adobe Experience Platform Mobile SDK集成到您的应用程序](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
>* 将 [Adobe Campaign Standard Extension添加到您的移动应用程序配置中](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。
   >
   >
* [在Places POI管理界面中创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md) 。
   >
   >
* 在您的移动应用程 [序中安装和配置](/help/places-ext-aep-sdks/places-extension/places-extension.md)[Places扩展和Places Monitor扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) 。


## 根据地理围栏进入或退出发送应用程序内消息

1. 在您的Adobe Campaign standard实例中，单击 **[!UICONTROL Create In-App message]**。
2. 对于消息类型，请选择 **[!UICONTROL Target all users of a Mobile application]**。
3. 单击 **[!UICONTROL Next]** 并键入常规详细信息。
4. 在左侧窗格中，验证您现在可以使用与位置服务相关的各种触发器。

   * 如果用户已输入POI地理围栏，则可以选择显示应用程序内消息。
   * 您还可以使用在位置服务UI中定义的元数据来筛选受众。
   在下图的示例中，您可以触发应用程序内消息，该消息仅显示给进入其中一个参加免费饮料计划的度假胜地的用户，您希望在用户到达时向他们发送优惠券。

   ![“应用程序内消息放置元数据”](/help/assets/last-entered-vacation.png)

5. 单击以 **[!UICONTROL Next]** 完成创建要交付的应用程序内消息。

   ![“创建活动”](/help/assets/prepare-ACS.png)

   要测试应用程序内消息传送，请在Xcode或Android Studio中启动应用程序，并使用位置模拟器选择符合消息传送条件的POI。

   ![“饮料优惠券”](/help/assets/drink-coupon-on-app.png)


将位置服务与Adobe Campaign standard结合使用，为您提供了一个功能强大的工具，根据地理围栏条目和退出情况将消息细分并定向给用户。 这种简单的集成为构建更个性化、更符合情境的使用案例打开了大门。

## 在Campaign standard中基于地点元数据创建不同的触发器

（此信息是否即将发布？）