---
title: 使用Places服务推送通知
description: 本节提供了有关如何在Campaign Standard中使用Places服务及推送通知的信息。
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# 使用Places服务推送通知 {#push-notifications}

在此部分中，您将了解如何使用历史地理位置信息定位通过Adobe Campaign Standard交付的推送通知。

## 先决条件

在开始之前，请完成以下任务：

* 已使用Adobe Experience Platform Mobile SDK配置移动应用程序，包括[Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 将[Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk)集成到您的应用程序中。
* 将[Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)添加到您的移动应用配置中。

* [在Places服务POI管理界面中创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。

* 启用并安装[Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。


## 在Experience Platform Launch中创建数据元素

验证Places扩展和区域监视解决方案([CoreLocation文档](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) for iOS或[Android位置文档](https://developer.android.com/training/location/geofencing))在应用程序中是否正确工作后，您需要在Experience Platform Launch中创建数据元素。 数据元素允许您读取通过Mobile SDK事件中心访问的扩展提供的信息，并充当别名以从客户端应用程序中检索数据。 要从Places扩展检索数据并将Places Service信息发送到Campaign，您需要创建几个数据元素。

要创建数据元素，请执行以下操作：

1. 在Experience Platform Launch移动属性中，单击&#x200B;**[!UICONTROL 数据元素]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL 添加数据元素]**。
1. 在&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL Places服务]**。
1. 从&#x200B;**[!UICONTROL 数据元素类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 名称]**。
1. 在右侧窗格中，可以选择&#x200B;**[!UICONTROL 当前POI]**，这将检索用户当前所在的POI的名称。

   **[!UICONTROL 上次进入时间]**&#x200B;检索用户上次进入的POI名称，**[!UICONTROL 上次退出时间]**&#x200B;提供用户上次离开的POI名称。 在此示例中，我们选择了&#x200B;**[!UICONTROL 上次输入]**&#x200B;并键入了数据元素的名称，如&#x200B;**[!UICONTROL 上次输入的POI名称]**&#x200B;并单击&#x200B;**[!UICONTROL 保存]**。

   ![“Campaign Standard中的推送消息”](/help/assets/ACS_Push1.png)

1. 重复上述步骤1 - 4并为&#x200B;*上次进入的POI纬度*、*上次进入的POI经度*&#x200B;和&#x200B;*上次进入的POI半径*&#x200B;创建数据元素。

除了Places服务的数据元素之外，请确保为&#x200B;*应用程序ID*&#x200B;和&#x200B;*Experience CloudID*&#x200B;创建移动核心数据元素。

## 创建规则以将位置数据发送到Adobe Campaign Standard

Experience Platform Launch中的规则允许您根据事件触发器创建复杂的多解决方案工作流。 通过规则，您可以创建新规则或修改现有规则，并将更新动态部署到移动应用程序。 在以下示例中，当用户输入受地域保护的POI时，将触发规则。 触发规则后，将向Campaign Standard发送更新，以根据Experience CloudID将条目记录到特定用户的特定POI。

1. 在Experience Platform Launch移动属性的&#x200B;**[!UICONTROL 规则]**&#x200B;选项卡上，单击&#x200B;**[!UICONTROL 添加规则]**。
1. 在&#x200B;**[!UICONTROL 事件]**&#x200B;部分下，单击&#x200B;**[!UICONTROL +]**&#x200B;并选择&#x200B;**[!UICONTROL Places服务]**&#x200B;作为扩展。
1. 对于&#x200B;**[!UICONTROL 事件类型]**，请选择&#x200B;**[!UICONTROL 进入POI]**。
1. 命名规则，例如&#x200B;**用户输入的POI**。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。
1. 将&#x200B;**[!UICONTROL 条件]**&#x200B;部分留空。

   利用此部分，可筛选或限制应何时触发此规则。

1. 在&#x200B;**[!UICONTROL 操作]**&#x200B;部分下，单击&#x200B;**[!UICONTROL +]**。
1. 在&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 移动核心]**，然后在&#x200B;**[!UICONTROL 操作类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 发送回发]**。
1. 在&#x200B;**[!UICONTROL URL]**&#x200B;中，您需要构造Campaign Standard位置终结点。

   URL应类似于`https:///rest/head/mobileAppV5//locations/`。
确保您使用之前为Campaign服务器和pKey创建的正确数据元素。

1. 单击该框可添加帖子正文并发送以下内容：

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
1. 在&#x200B;**[!UICONTROL 内容类型]**&#x200B;中，输入 **[!UICONTROL application/json]**。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

>[!IMPORTANT]
>
>* 将SlackWeb挂接设置为附加操作以验证是否正在触发条目以及是否正在收集正确的数据可能会很有帮助。
>* 请记住将最近的更改发布到您的应用程序，以确保该规则和所有数据元素都作为配置的一部分进行部署。 发布后，请再次启动移动应用程序以获取最新的配置更新。

## 使用位置数据定位Campaign消息

现在，我们已在Campaign中填充位置数据，我们可以将POI用作受众区段工具。

1. 在Adobe Campaign Standard实例中，单击&#x200B;**[!UICONTROL 创建推送通知]**。
1. 对于推送通知类型，选择&#x200B;**[!UICONTROL 将推送发送到促销活动用户档案]**。
1. 单击&#x200B;**[!UICONTROL 下一步]**&#x200B;并键入常规详细信息。
1. 在“受众”屏幕上，单击&#x200B;**[!UICONTROL 计数]**&#x200B;以确定将发送推送通知的预计用户数。

   >[!TIP]
   >
   >在此示例中，计数将为3，因为有三个已安装的设备正在测试应用程序。

1. 在左窗格中，展开&#x200B;**[!UICONTROL 配置文件]**&#x200B;选项卡，并将&#x200B;**[!UICONTROL POI位置]**&#x200B;筛选器拖到主区域。
1. 在POI过滤器窗口中，输入要定位的POI的确切名称。

   >[!TIP]
   >
   >您可以进行其他选择以确定自用户上次访问此POI以来的时间段。

   ![“ACS中的推送消息2”](/help/assets/ACS_push2.png)

1. 单击&#x200B;**[!UICONTROL 确认]**。
1. 在顶部再次运行该计数以查看受众规模变化。

   如果未看到计数更新，则可能是输入的POI名称没有设备触发了输入。 在这种情况下，具有SlackWeb挂接变得很有用，因为您可以看到来自各种测试设备的POI条目列表。

1. 您可以拖出其他POI位置筛选器以在消息中包含多个POI。
1. 单击&#x200B;**[!UICONTROL 下一步]**&#x200B;以完成创建要交付的推送通知。

   ![“ACS中的推送消息3”](/help/assets/ACS_push3.png)

通过将Places Service与Adobe Campaign Standard结合使用，您可以获得一个功能强大的工具，根据地域限制登录和退出来细分消息并将消息定位到用户。 此集成可帮助您构建更加个性化和情境化的用例。
