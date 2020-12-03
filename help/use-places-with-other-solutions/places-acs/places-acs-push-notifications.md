---
title: 通过Places Service推送通知
description: 本节提供有关如何在Campaign Standard中将Places Service与推送通知一起使用的信息。
translation-type: tm+mt
source-git-commit: fd469358845e14c47a58b40bb18c9144828a8996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 2%

---


# 通过Places服务推送通知 {#push-notifications}

在本节中，您将学习如何使用历史地理位置信息来目标通过Adobe Campaign Standard发送的推送通知。

## 先决条件

开始之前，请完成以下任务:

* 使用Adobe Experience Platform移动SDK配置移动应用程序，包括 [Adobe Campaign Standard扩展](Https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 将Adobe Experience Platform [移动SDK集](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 成到您的应用程序中。
* 将Adobe Campaign Standard [扩展添加](Https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 到您的移动应用程序配置。

* [在Places Service](/help/poi-mgmt-ui/create-a-poi-ui.md) POI管理界面中创建POI。

* 启用并安装 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。


## 在Experience Platform Launch中创建数据元素

验证“地点”扩展和“地点监视器”扩展在应用程序中是否正常工作后，您需要在Experience Platform Launch中创建数据元素。 数据元素允许您读取通过Mobile SDK事件中心提供的扩展提供的信息，并充当从客户端应用程序检索数据的别名。 要从Places扩展检索数据并将Places服务信息发送给活动，您需要创建一些数据元素。

创建数据元素:

1. 在Experience Platform Launch移动属性中，单击选 **[!UICONTROL Data Elements]** 项卡并单击 **[!UICONTROL Add Data Element]**。
1. 在下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places Service]**。
1. 从下 **[!UICONTROL Data Element Type]** 拉列表中，选择 **[!UICONTROL Name]**。
1. 在右侧窗格中，可以选 **[!UICONTROL Current POI]** 择检索用户当前所在POI的名称。

   **[!UICONTROL Last Entered]** 检索用户上次输入的POI的名称 **[!UICONTROL Last Exited]** ，并提供用户上次离开的POI的名称。 在此示例中，我们选 **[!UICONTROL Last Entered]** 择并键入数据元素的名称，如并 **[!UICONTROL Last Entered POI Name]** 单击 **[!UICONTROL Save]**。

   ![“Campaign Standard推送消息”](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

除了Places Service的数据元素之外，请确保为App ID和 *Experience CloudID创* 建 *Mobile Core数据元素*。

## 创建规则以将位置数据发送到Adobe Campaign Standard

Experience Platform Launch中的规则允许您根据事件触发器创建复杂的多解决方案工作流。 利用规则，您可以创建新规则或修改现有规则，并将更新动态部署到移动应用程序。 在以下示例中，当用户进入一个地理围栏的POI时，将触发该规则。 在触发规则后，会向Campaign Standard发送更新，以根据Experience CloudID记录特定用户的特定POI的条目。

1. 在Experience Platform Launch移动属性的选项卡 **[!UICONTROL Rules]** 上，单击 **[!UICONTROL Add Rule]**。
1. 在部分 **[!UICONTROL Events]** 下，单 **[!UICONTROL +]** 击并选择 **[!UICONTROL Places Service]** 作为扩展名。
1. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
1. 将规则命名为，例如， **用户输入POI**。
1. 单击 **[!UICONTROL Keep Changes]**。
1. 将部分 **[!UICONTROL Conditions]** 留空。

   此部分允许您过滤或限制此规则何时触发。

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. 在下 **[!UICONTROL Extension]** 拉列表中，选 **[!UICONTROL Mobile Core]** 择，在下 **[!UICONTROL Action Type]** 拉列表中，选择 **[!UICONTROL Send Postback]**。
1. 在中 **[!UICONTROL URL]**，您需要构建Campaign Standard位置端点。

   URL应类似于 `https:///rest/head/mobileAppV5//locations/`。
确保使用之前为活动服务器和pKey创建的正确数据元素。

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
1. 输入 **[!UICONTROL Content Type]**，键入 **[!UICONTROL application/json]**。
1. 单击 **[!UICONTROL Keep Changes]**。

>[!IMPORTANT]
>
>* 将SlackWeb挂接设置为附加操作，以验证是否正在触发条目以及是否正在收集正确的数据可能会有所帮助。
>* 请记住将最近的更改发布到您的应用程序，以确保将规则和所有数据元素作为配置的一部分进行部署。 发布后，再次启动移动应用程序以获取最新配置更新。


## 使用位置数据目标活动消息

现在，我们在活动中填充了位置数据，因此可以将POI用作受众段工具。

1. 在您的Adobe Campaign Standard实例中，单击 **[!UICONTROL Create Push Notification]**。
1. 对于推送通知类型，请选择 **[!UICONTROL Send push to Campaign profiles]**。
1. 单击 **[!UICONTROL Next]** 并键入常规详细信息。
1. 在受众屏幕上，单 **[!UICONTROL Count]** 击以确定发送推送通知的估计用户数。

   >[!TIP]
   >
   >在本例中，计数将为3，因为有三个已安装的设备正在测试应用程序。

1. 在左窗格中，展开选 **[!UICONTROL Profile]** 项卡，然后将滤 **[!UICONTROL POI location]** 镜拖动到主区域。
1. 在POI过滤器窗口中，输入要目标的POI的确切名称。

   >[!TIP]
   >
   >您可以进行其他选择以确定自用户上次访问此POI以来的时间段。

   ![&quot;ACS中的推送消息2&quot;](/help/assets/ACS_push2.png)

1. 单击 **[!UICONTROL Confirm]**。
1. 再次在顶部运行计数以查看受众大小的更改。

   如果看不到计数更新，则可能已输入POI名称，其中没有设备触发过条目。 在这种情况下，使用SlackWeb挂接变得很有价值，因为您可以看到来自各种测试设备的POI条目列表。

1. 您可以拖出其他POI位置过滤器，在消息中包含多个POI。
1. Click **[!UICONTROL Next]** to finish creating the push notification for delivery.

   ![&quot;ACS中的推送消息3&quot;](/help/assets/ACS_push3.png)

将Places Service与Adobe Campaign Standard结合使用，为您提供了一个强大的工具，根据地理围栏条目和退出将消息细分并目标给用户。 此集成可帮助您构建更个性化和情境化的使用案例。