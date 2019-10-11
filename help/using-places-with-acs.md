---
title: 将地点与Adobe Campaign Standard结合使用
seo-title: 将地点与Adobe Campaign Standard结合使用
description: 深入了解客户偏好和习惯是成功营销活动的关键。 知道用户是否访问过物理位置还可以添加一些非常有价值的上下文以与消费者建立关系。
seo-description: 深入了解客户偏好和习惯是成功营销活动的关键。 知道用户是否访问过物理位置还可以添加一些非常有价值的上下文以与消费者建立关系。
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# 将地点与Adobe Campaign Standard结合使用 {#places-with-acs}

*感谢您上周来访，我们很乐意为您提供一个惊喜，供您下次访问时使用！*

深入了解客户偏好和习惯是成功营销活动的关键。 用户搜索的项目和先前的购买历史记录在受众定位中起着重要作用。 知道用户是否访问过物理位置还可以添加一些非常有价值的上下文以与消费者建立关系。

根据来自eMarketer的最新报告，85%的高绩效零售商认为位置对于他们的营销工作非常重要。 此外，北美超过58%的零售商计划投资邻近／定位技术以增强其客户体验。

![](/help/assets/using-loc-services-acs_0.png)

想一想智能手机使用体验中的关键位置。 智能手机上的客人多久能找到附近的餐馆、加油站、杂货店或其他服务。

因此，作为品牌，您应该考虑如何将位置运用到营销活动中，这是有道理的。 在本指南中，我们将介绍如何利用Adobe Experience Platform Experience Platform Location service的强大功能，通过Adobe Campaign Standard将位置上下文添加到消息中，从而使您能够根据历史兴趣点(POI)条目发布个性化的推送通知或应用程序内消息。

在开始之前，本指南假定您已经配置了具有Adobe Campaign Standard扩展的Adobe Experience Platform Mobile SDK的移动应用程序。 除了Adobe Experience Platform Mobile SDK和Campaign Standard之外，您还应有权访问Experience Platform Location Service。

## 先决条件

1. 将 [Adobe Experience Platform Mobile SDK集成到您的应用程序](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 。
1. 将 [Adobe Campaign Standard Extension添加到您的移动应用程序配置中](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 。
1. [创建一个或多个POI](/help/places-database-management-1/managing-pois-in-the-places-ui.md)。

>[!TIP]
>
>如果您正在寻找批量上传或管理POI的方法，请查看此脚 [本以从CSV文件上传POI](https://github.com/adobe/places-scripts) 。 此外， [Places API](/help/places-rest-apis/api-usage/api-usage.md) 可用于创建或管理目标点。

如果您无权访问地点，则可以在此 [处请求访问](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)。

### 在应用程序中启用和安装Places扩展

在“地点”界面中创建兴趣点后，您需要将“地点”功能添加到应用程序中。

1. 按照说明在应用程序中启用地点和地点监视器扩展。
1. 在“地点”扩展中，确保您选择了之前创建的POI的相应库。

   可以随时将其他库添加到扩展配置。

1. 确保已将这些配置添加到库，并在启动项中发布了配置更改。
1. 在“ **[UICONTROL启动环境”选项卡中]** ，单击安装说明图标以查看有关将相应的CocoaPod和Gradle文件下载到应用程序项目的说明。
1. 在您的应用程序中，按照向应用程序添加位置背景模式的说明操作，并启动位置监视器。
1. 通过设备模拟器测试应用程序，以根据欺骗设备的位置查看应用程序在邻近的目标点请求。

### 在Experience Platform Launch中创建数据元素

在验证您的应用程序中是否有Places和Places Monitor扩展正常工作后，在Experience Platform Launch中创建数据元素以读取扩展提供并通过Mobile SDK事件中心提供的信息。 数据元素实质上充当从客户端应用程序检索数据的别名。 让我们创建一些数据元素，以从Places扩展中检索数据。

1. 在您的Experience Platform Launch移动属性中，在选项卡上 **[!UICONTROL Data Elements]** 单击，然后 **[!UICONTROL Add Data Element]**。
1. 从扩展菜单中，选择 **[!UICONTROL Places]**。
1. 从下 **[!UICONTROL Data Element]** 拉列表中，选 **择[!UICONTROL名称}**。
1. 在右侧的窗口中，您可以选择 **[!UICONTROL Current POI]** 将检索用户当前所在的POI的名称。

   * **[!UICONTROL Last Entered]** 检索用户上次输入的POI的名称
   * **[!UICONTROL Last Exited]** 将提供用户上次离开的POI的名称。

1. Select **[!UICONTROL Last Entered]**.
1. 键入数据元素的名称（如）, **[!UICONTROL Last Entered POI Name]**&#x200B;然后单击 **[!UICONTROL Save]**。


   ![](/help/assets/using-loc-services-acs_1.png)

1. 重复上述步骤，为“上次输入的POI纬度 *”、“上次输入的POI经度*”、“上次输入的POI *半径”创建数据元素***。

除了Places的数据元素之外，请确保您还为App ID和 *Experience Cloud ID创建了Mobile Core**数据元素*。

### 创建规则以将位置数据发送到Adobe Campaign Standard

Experience Platform Launch中的规则允许您基于事件触发器创建复杂的多解决方案工作流程。 您可以创建新规则或更改现有规则，并将更新动态部署到您的移动应用程序。 在此示例中，我们将创建一个规则，该规则在用户进入地理围栏的POI时触发。 触发规则后，会向Campaign Standard发送更新，以便为用户将条目记录到特定POI。 此POI基于Experience Cloud ID。

1. 在您的Experience Platform Launch移动属性中，单击选项 **[!UICONTROL Rules]** 卡并单击 **[!UICONTROL Add Rule]**。
1. 在部分 **[!UICONTROL Events]** 中，单击并 **[!UICONTROL +]** 选择 **[!UICONTROL Places]**。
1. 在中 **[!UICONTROL Event Type]**，选择 **[!UICONTROL Enter POI]**。
1. 输入规则的名称，例如 **[!UICONTROL User entered POI]**。
1. 单击 **[!UICONTROL Keep Changes]**。
1. 将部分 **[!UICONTROL Conditions]** 留空。

   此部分允许您过滤或限制此规则何时触发。

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. 在中 **[!UICONTROL Extension]**，选 **[!UICONTROL Mobile Core]** 择并在中 **[!UICONTROL Action Type]**&#x200B;选择 **[!UICONTROL Send Postback]**。

1. 对于该URL，您需要构建您的Campaign standard位置端点。

   该URL应类似于下面的URL。 确保使用您之前为Campaign服务器和pKey创建的正确数据元素。

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. 单击该框以添加帖子正文并发送以下内容：

   ```text
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

1. 使用您在上一节中创建的特定数据元素。
1. 在中 **[!UICONTROL Content Type]**&#x200B;键入 **[!UICONTROL application/json]**。
1. 设置 **[!UICONTROL Keep Changes]** 完此设置后单击。

   设置Slack web挂钩作为附加操作，以验证我的操作是否被触发以及是否正在收集正确的数据，这可能会很有帮助。

   >[!IMPORTANT]
   >
   >请记住将最近的更改发布到您的应用程序，以确保将规则和所有数据元素作为配置的一部分进行部署。 发布后，您应重新启动移动应用程序以获取最新配置更新。

### 使用位置数据定位Campaign standard消息

现在，我们在Campaign中填充了位置数据，因此可以将兴趣点用作受众细分工具。

1. 在Adobe Campaign standard实例中，单击“UICONTROL **[创建推送通知”]**。
1. 对于推送通知类型，选择 **[UICONTROL将推送发送给应用程序订阅者]**。

   此推送类型将以应用程序的所有用户为目标。 如果移动用户已附加到营销活动配置文件，则还可以选择 **[UICONTROL将推送发送到营销活动配置文件]** i。

1. 单击 **[!UICONTROL Next]** 并在下一个屏幕上键入常规详细信息。
1. 在“受众”屏幕上，单 **[!UICONTROL Count]** 击查看将发送推送通知的估计用户数。

   在这种情况下，计数为三个，因为测试应用程序上安装了三个设备。

1. 在左侧提要栏上，展开选 **[!UICONTROL Profile]** 项卡并在主区 **[!UICONTROL POI location]** 域上拖动过滤器。
1. 在POI过滤器窗口中，输入要定位的POI的确切名称。

   您可以进行其他选择以确定自用户上次访问此POI以来的时间范围。

   ![](/help/assets/using-loc-services-acs_2.png)

1. 单击 [!**UICONCONTROL确认]**。
1. 再次在顶部运行计数，以查看受众规模的变化。

   如果看不到计数更新，则可能已输入POI名称，其中没有设备触发了条目。 在这里，Slack Web Hook变得很有价值，因为您可以看到来自各种测试设备的POI条目列表。
1. 您可以拖出其他POI位置过滤器，以在消息中包含多个POI。
1. 单击 **[!UICONTROL Next]** 以完成创建要传送的推送通知。

   ![](/help/assets/using-loc-services-acs_3.png)

除了推送通知外，您还可以使用位置数据细分您希望接收应用程序内消息的用户。

1. 在您的Adobe Campaign standard实例中，单击 **[!UICONTROL Create In-App message]**。
1. 对于消息类型，请选择 **[!UICONTROL Target all users of a Mobile application]**。
1. 单击 **[!UICONTROL Next]** 并在下一个屏幕上键入常规详细信息。
1. 在左窗格中，验证您现在可以使用与地点相关的各种触发器。
1. 如果用户已输入POI地理围栏，则可以选择显示应用程序内消息。

   您还可以使用在地点UI中定义的元数据来过滤受众。 在此示例中，我希望触发仅向上次退出POI且还具有健身设施的用户显示的应用程序内消息。 也许我想给他们发一份调查，看看他们是否使用／喜欢健身房。

1. 单 **[!UICONTROL Next]** 击以完成创建要交付的应用程序内消息。

   ![](/help/assets/using-loc-services-acs_4.png)

将地点与Adobe Campaign standard结合使用，为您提供了一个非常强大的工具，可根据历史位置将消息细分和定向给用户。 这种简单的集成为构建更个性化、更符合情境的使用案例打开了大门。

我们不断改进Places和集成解决方案，将位置环境引入移动工作流程中。 即将推出的“触发式旅程”解决方案是利用“地点”的一款产品，它允许客户基于事件触发器（如位置）创建实时工作流。

## 推荐的链接

有关详细信息，请参阅以下内容：

* [Adobe Experience Location Service](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard](https://www.adobe.com/marketing/campaign.html)
* [注册以访问Adobe Places Beta](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)
* [Adobe Campaign与Experience Platform SDK集成](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
