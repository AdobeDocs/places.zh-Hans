---
title: 推送通知
seo-title: 推送通知
description: 本节提供有关如何在Campaign standard中将地点与推送通知一起使用的信息。
seo-description: '本节提供有关如何在Campaign standard中将地点与推送通知一起使用的信息。 '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# 使用Experience Platform Location service推送通知 {#push-notifications}

在本指南中，我们将介绍如何使用历史地理位置信息来定位通过Adobe Campaign standard提供的推送通知。

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
* 启用并安装 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。



## 在Experience Platform Launch中创建数据元素

在验证位置服务的地点和地点监视器扩展是否在您的应用程序中正常工作后，请在Experience Platform Launch中创建数据元素。 数据元素允许您读取通过Mobile SDK事件中心提供的扩展提供的信息，并充当别名，从客户端应用程序检索数据。 让我们创建一些数据元素，以从Places扩展中检索数据，以便将Places信息发送到Campaign。

1. 在Experience Platform Launch移动属性中，单击“数据元素” **选项卡** ，然后单击“ **添加数据元素”**。
2. 在“扩 **展** ”下拉列表中，选择 **地点**。
3. 从“数 **据元素类型** ”下拉列表中，选择 **名称**。
4. 在右侧窗格中，可以选择 **Current POI** ，它检索用户当前所在POI的名称。

   **Last Entered** （最后输入）检索用户上次输入的POI的名称，而 **Last Excest（最后退出）** （提供用户上次离开的POI的名称）。 在此示例中，我们将选择“ **Last Entered** ”（最后输入），并键入数据元素的名称，如“ **Last Entered POI Name** ”（最后输入的POI名称） **，然后单击“**&#x200B;保存”(Save)。

   ![“Campaign Standard中的推送消息”](/help/assets/ACS_Push1.png)


5. 重复上述步骤，为“上次输入的POI纬度 _”、“上次输入的POI经度”_、“上次输入的POI _经度”和“上次输入的POI半径”创建数据元素___。

除了位置服务的数据元素之外，请确保为App ID和 _Experience Cloud ID创建Mobile Core__数据元素_。

## 创建规则以将位置数据发送到Adobe Campaign Standard

Experience Platform Launch中的规则允许您基于事件触发器创建复杂的多解决方案工作流。 规则的优点在于，您可以创建新规则或修改现有规则，并将更新动态部署到移动应用程序。 在此示例中，我们将创建一个规则，该规则将在用户进入地理围栏POI时触发。 触发规则后，将向Campaign发送更新，以根据Experience Cloud ID为特定用户记录特定POI的条目。

1. 在“启动”移动属性中，单击“规 **则** ”选项卡，然 **后单击添加规则**。
2. 在“事 **件** ”部分下，单 **击+** 并选 **择“地点** ”作为扩展。
3. 对于“事 **件类型** ”, **选择“输入POI**”。
4. 将规则命名为，例如， **用户输入POI**。
5. Click **Keep Changes**.
6. “条 **件** ”部分允许您过滤或限制此规则何时触发。  暂时留空。
7. 在“操 **作** ”部分下 **** ，单击+以创建新操作
8. 在“ **Extension** ”(扩展 **)下拉列表中** ，选择“ **Mobile Core”（移动核心）,** 在“ **Action Type**”（操作类型）下拉列表中，选择“Send Postback”（发送后退）。
9. 对于 **URL**，您需要构建Campaign standard位置端点。  该URL应类似于下面的URL。 确保使用您之前为Campaign服务器和pKey创建的正确数据元素。 `https:///rest/head/mobileAppV5//locations/`
10. 单击该框以添加帖子正文并发送以下内容：

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

11. 确保您使用的是您在上一节中创建的特定数据元素。
12. 在“ **内容类型**”中，键 **入application/json**。
13. 设置 **此设置后** ，单击“保留更改”。
14. 将Slack web挂钩设置为附加操作，以验证是否正在触发条目以及是否正在收集正确的数据，这很有帮助。


>不要忘记将最近的更改发布到应用程序，以确保将规则和所有数据元素作为配置的一部分进行部署。 发布后，您应再次启动移动应用程序以获取最新配置更新。

## 使用位置数据定位营销活动消息

现在，我们在Campaign中填充了位置数据，因此可以将POI用作受众细分工具。

1. 在Adobe Campaign standard实例中，单击“创 **建推送通知”**。
2. 对于推送通知类型，选择将推 **送到营销活动配置文件**。
3. 单击 **下一步** ，然后在下一个屏幕上键入常规详细信息。
4. 在“受众”屏幕上，单 **击“计数** ”以查看将发送推送通知的估计用户数。

   *在这种情况下，我的数量将等于3，因为我已安装了三台设备，用于测试应用程序。*

5. 在左侧提要栏上，展开“配 **置文件** ”选项卡，并将 **** POI位置筛选器拖到主区域
6. 在POI过滤器窗口中，输入要定位的POI的确切名称。

   *您可以进行其他选择以确定自用户上次访问此POI以来的时间范围。*

   ![“ACS中的推送消息2”](/help/assets/ACS_push2.png)


7. 单击“确认”****。
8. 再次在顶部运行计数，以查看受众规模的变化。  如果看不到计数更新，则可能已输入POI名称，其中没有设备触发了条目。 在这里，Slack Web Hook变得很有价值，因为您可以看到来自各种测试设备的POI条目列表。
9. 您可以拖出其他POI位置过滤器，以在消息中包含多个POI。
10. 单击 **下一步** ，以完成创建要传送的推送通知。

   ![“ACS中的推送消息3”](/help/assets/ACS_push3.html)

将位置服务与Adobe Campaign standard结合使用，为您提供了一个功能强大的工具，可根据地理围栏条目和扩展将消息细分和定向给用户。 这种简单的集成为构建更个性化、更符合情境的使用案例打开了大门。