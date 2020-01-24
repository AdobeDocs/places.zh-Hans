---
title: 通过Places service推送通知
description: 本节提供有关如何在Campaign standard中将Places service与推送通知结合使用的信息。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# 通过Places service推送通知 {#push-notifications}

在本节中，您将学习如何使用历史地理位置信息来定位通过Adobe Campaign standard提供的推送通知。

## 先决条件

在开始之前，请完成以下任务：

* 使用Adobe Experience Platform Mobile SDK配置移动应用程序，包括 [Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 将 [Adobe Experience Platform Mobile SDK集成到您的应用程序](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
* 将 [Adobe Campaign Standard Extension添加到您的移动应用程序配置中](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。

* [在Places Service](/help/poi-mgmt-ui/create-a-poi-ui.md) POI管理界面中创建POI。

* 启用并安装 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。


## 在Experience Platform Launch中创建数据元素

在验证“地点”扩展和“地点监视器”扩展在您的应用程序中是否正常工作后，您需要在Experience Platform Launch中创建数据元素。 数据元素允许您读取通过Mobile SDK事件中心提供的扩展提供的信息，并充当别名，从客户端应用程序检索数据。 要从Places扩展检索数据并将Places service信息发送到Campaign，您需要创建一些数据元素。

要创建数据元素，请执行以下操作：

1. 在Experience Platform Launch移动属性中，单击选项卡， **[!UICONTROL Data Elements]**然后单击“添**[!UICONTROLA&#x200B;加数据元素”]**。
1. 在下 **[!UICONTROL Extension]**拉列表中，选择**[!UICONTROL Places Service]**。
1. 从下 **[!UICONTROL Data Element Type]**拉列表中，选择**[!UICONTROL Name]**。
1. 在右侧窗格中，您可以选择 **[!UICONTROL Current POI]**检索用户当前所在的POI的名称。

   **[!UICONTROL Last Entered]**检索用户上次输入的POI的名称，并**[!UICONTROL Last Exited]** 提供用户上次离开的POI的名称。 在此示例中，我们选 **[!UICONTROL Last Entered]**择并键入数据元素的名称，如并**[!UICONTROL Last Entered POI Name]** 单击 **[!UICONTROL Save]**。

   ![“Campaign Standard中的推送消息”](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

除了Places service的数据元素之外，请确保为App ID和 *Experience Cloud ID创建Mobile Core**数据元素*。

## 创建规则以将位置数据发送到Adobe Campaign Standard

Experience Platform Launch中的规则允许您基于事件触发器创建复杂的多解决方案工作流。 利用规则，您可以创建新规则或修改现有规则，并将更新动态部署到移动应用程序。 在以下示例中，当用户进入一个地理围栏的POI时，将触发该规则。 触发规则后，将向Campaign Standard发送更新，以根据Experience Cloud ID为特定用户记录特定POI的条目。

1. 在您的Experience Platform Launch移动属性中，单击 **[!UICONTROL Rules]**选项卡**[!UICONTROL Add Rule]**。
1. 在部分 **[!UICONTROL Events]**下，单击并**[!UICONTROL +]** 选择 **[!UICONTROL Places Service]**作为扩展名。
1. For the **[!UICONTROL Event Type]**, select**[!UICONTROL Enter POI]**.
1. 将规则命名为，例如， **用户输入POI**。
1. 单击 **[!UICONTROL Keep Changes]**。
1. 将部分 **[!UICONTROL Conditions]**留空。

   此部分允许您过滤或限制此规则何时触发。

1. 在部分 **[!UICONTROL Actions]**下，单击**[!UICONTROL +]**。
1. 在下 **[!UICONTROL Extension]**拉列表中，选择**[!UICONTROL Mobile Core]** 并在下 **[!UICONTROL Action Type]**拉列表中选择**[!UICONTROL Send Postback]**。
1. 在中， **[!UICONTROL URL]**您需要构建您的Campaign standard位置端点。

   URL应类似于 `https:///rest/head/mobileAppV5//locations/`。
确保使用您之前为Campaign服务器和pKey创建的正确数据元素。

1. 单击该框以添加帖子正文并发送以下内容：

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

1. 确保使用您在上一节中创建的数据元素。
1. 在中 **[!UICONTROL Content Type]**键入**[!UICONTROL application/json]**。
1. 单击 **[!UICONTROL Keep Changes]**。

>[!IMPORTANT]
>
>* 将Slack web挂接设置为其他操作，以验证是否正在触发条目以及是否正在收集正确的数据，这可能会很有帮助。
>* 请记住将最近的更改发布到您的应用程序，以确保将规则和所有数据元素作为配置的一部分进行部署。 发布后，再次启动移动应用程序以获取最新的配置更新。


## 使用位置数据定位营销活动消息

现在，我们在Campaign中填充了位置数据，因此可以将POI用作受众细分工具。

1. 在您的Adobe Campaign standard实例中，单击 **[!UICONTROL Create Push Notification]**。
1. 对于推送通知类型，请选择 **[!UICONTROL Send push to Campaign profiles]**。
1. 单击 **[!UICONTROL Next]**并键入常规详细信息。
1. 在“受众”屏幕上，单 **[!UICONTROL Count]**击以确定将发送推送通知的估计用户数。

   >[!TIP]
   >
   >在本例中，计数将为3，因为有三台已安装的设备正在测试应用程序。

1. 在左侧窗格中，展开选 **[!UICONTROL Profile]**项卡，然后将滤镜拖**[!UICONTROL POI location]** 动到主区域。
1. 在POI过滤器窗口中，输入要定位的POI的确切名称。

   >[!TIP]
   >
   >您可以进行其他选择以确定自用户上次访问此POI以来的时间段。

   ![“ACS中的推送消息2”](/help/assets/ACS_push2.png)

1. 单击 **[!UICONTROL Confirm]**。
1. 再次在顶部运行计数，以查看受众规模的变化。

   如果看不到计数更新，则可能已输入POI名称，其中没有设备触发了条目。 在这种情况下，使用Slack web挂钩将变得很有价值，因为您可以看到来自各种测试设备的POI条目列表。

1. 您可以拖出其他POI位置过滤器，以在消息中包含多个POI。
1. Click **[!UICONTROL Next]**to finish creating the push notification for delivery.

   ![“ACS中的推送消息3”](/help/assets/ACS_push3.png)

将Places service与Adobe Campaign standard结合使用，为您提供了一个功能强大的工具，可根据地域围栏条目和退出情况将消息细分和定向给用户。 此集成可帮助您构建更个性化的情境式使用案例。