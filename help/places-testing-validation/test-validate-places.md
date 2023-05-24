---
title: 测试和验证Places服务
description: 本节提供了有关如何测试和验证Places服务的信息。
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 2%

---

# Recommendations测试Places服务 {#test-validate-loc-svc}

全球有许多客户和组织将定义POI，因此有必要模拟和测试Places服务与您的应用程序之间的交互方式。 此信息可帮助您了解如何测试和验证根据定义的POI和用户的当前位置正确触发的Places服务条目和退出。

由于环境变量可能是位置信号和精度的一个因素，因此我们建议您首先通过使用开发人员工具和模拟的位置条目在本地工作来建立基线结果。 目标是验证所有位置事件是否都正常工作。 正确验证位置事件后，可以测试解决方案集成（例如Analytics、Target和Campaign）。 为了帮助测试活动，您应该使用回发设置SlackWebhook，并在单独的开发环境中加载GPX文件。

>[!IMPORTANT]
>
>此计划假设已在以下位置创建POI： [Places Service UI](https://places.adobe.com) 并正确安装和配置了Places扩展的最新版本。 在进行主动区域监控时，还假定实施了区域监控解决方案。 有关更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)， [CoreLocation文档](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) 对于iOS，或者 [Android位置文档](https://developer.android.com/training/location/geofencing).

| 步骤 | 描述 | 预期结果 |
|--- |--- |--- |
| 1 | 确认已为Android输入正确的清单键以授予对跟踪位置的访问权限。 | 已确认 |
| 1a | 确认在iOS中配置了位置更新。 此外，还要确保您在iOS中设置了适当的plist键，以请求用户跟踪位置的权限。 | 已确认 |
| 2 | 确认为iOS设置了哪个监视模式。 连续模式允许更高的精度和持久性，但也会更严重地消耗电池寿命。 | 重大变化或持续性 |
| 3 | 如果使用多个POI库，请确认已在Places扩展中选择了相应的库以进行Experience Platform Launch。 | 已确认 |
| 4 | 确认最新版本的Mobile Core和Places扩展已通过Gradle或CocoaPods与应用程序捆绑在一起。 | 已确认 — 有关最近更新的详细信息，请参阅 [发行说明。](/help/release-notes.md) |
| 5 | 确认为测试配置了正确的环境。 Launch环境ID应与您的Launch开发环境匹配。 | 已确认 |
| 6 | 为要测试的每个POI创建GPX文件。 GPX文件可用于本地开发环境中模拟位置条目。 有关创建和使用GPX文件的信息，请参阅以下内容： <br>[iOS模拟器的GPX文件[已关闭]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[移动应用程序中的位置测试](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX文件会在应用程序项目中创建和加载。 |
| 7 | 您无需执行任何其他操作，即可从Android Studio或Xcode启动应用程序，并查看相应的警报以请求访问跟踪位置。 单击 *始终允许* 许可。<br><br>我们建议您使用连接到计算机的真实设备，而不是使用设备模拟器。 | 在通过IDE加载的应用程序上应显示位置请求提示 |
| 8 | 在接受“位置”权限后。 Places SDK将检索设备的当前位置，并且区域监视代码应开始从当前位置监视20个最近的POI | 请参阅表下的日志示例。 |
| 9 | 在Xcode或Android Studio中的不同位置之间切换应生成特定POI的条目事件。 进入POI时应遵循以下日志。 | 请参阅表下的日志示例。 |
| 10 | 在区域监视器找到附近的POI后，应通过发送位置ping进行测试。 在Launch中，创建一个新规则，该规则使用Places扩展根据地理围栏条目进行触发。 然后，使用移动核心创建新操作以发送回发。 创建SlackWebhook应用程序可帮助您查看位置条目和退出点。 有关创建SlackWebhook应用程序的信息，请参阅 [使用传入Webhook发送消息。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 在Launch中，确保为Places扩展添加了数据元素，其中包括： <br>当前POI名称<br>当前POI纬度<br>当前POI时长<br>上次输入的名称<br>上次输入时间<br>上次输入时间较长<br>上次退出的名称<br>上次退出日期<br>上次退出时间过长<br>时间戳 |  |
| 10b | 使用Event = Places → Enter POI创建新规则 |  |
| 10c | 创建一个操作= Mobile Core → Postback |  |
| 10d | 为您的Slack应用程序使用Webhook URL，例如https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD...。 |  |
| 10e | 帖子正文将类似于： `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>确保您使用在此处创建的特定数据元素。 |  |
| 10f | 确保在Launch中发布所有新的数据元素和规则更改。 （您应在Launch界面的右上角选择一个工作开发库。） |  |
| 11 | 通过在开发人员IDE中的GPX位置之间切换来再次启动并测试应用程序。 | 现在，当您在开发环境中选择不同的位置时，应该会看到Slack通知，其中显示每个POI的条目。 |
|  | **快速摘要点**<br>&#x200B;所有这些测试都可以在本地执行，而无需转到特定的POI位置。 验证测试有助于确保您的应用程序配置正确，并且已获得位置的正确权限。 <br><br>此验证还可让您确信定义的POI可与您的区域监控实施一起正常工作。  执行此步骤后，我们将开始在Campaign中测试消息，以了解根据POI进入和退出次数是否显示正确的消息。 |  |
|  | **使用Places服务测试Adobe Campaign Standard应用程序内消息传送。** |  |
| 12 | 在Campaign主仪表板上，配置新的应用程序内消息（类型=广播） |  |
| 12a | 在触发器中，选择 **Places事件类型 — 作为触发器的条目**. |  |
| 12b | 选择 **[!UICONTROL Places自定义元数据]** 作为附加过滤器 — 使用POI类型=上次输入的POI。<br>我们使用 **[!UICONTROL 上次输入]** 作为POI类型，因为大多数情况下， **[!UICONTROL 上次输入]** 将与 **[!UICONTROL 当前POI]**. <br><br>**[!UICONTROL 当前POI ]**应仅在存在重叠POI地理围栏的情况下使用。 在这种情况下，这些POI需要排名，然后**[!UICONTROL &#x200B;当前POI ]**将显示用户当前可能所在的2个或3个地理围栏中的排名最前的POI。 |  |
| 12c | 选择自定义元数据键，以帮助您缩小接收消息的POI范围。 |  |
| 12d | 对于频度和持续时间，请仅保留一天或两天，这样当您不喜欢该标准时，可以在更短的时间内使触发器过期。 |  |
| 12e | 对于Always/Once或Until点进，选择 *始终* 以便您可以跨多个位置进行测试。 | 当您模拟符合相应元数据标准的位置更改时，将始终显示应用程序内消息。 |
| 12f | 对于显示，请选择本地通知以外的选项。 这样一来，在前台测试应用程序时更容易查看。) |  |
| 12g | 准备/确认并部署应用程序内消息。 |  |
| 13 | 在开发环境中，为确保下载新的营销活动规则，请退出并再次启动应用程序。 | 请不要忘记，必须再次完全启动应用程序，才能将新的Campaign规则文件下载到设备。 |
| 14 | 在开发应用程序中，使用之前创建的GPX文件切换位置。 | 您应会看到根据之前设置的条件显示的应用程序内消息。 |
| 15 | 在下一次测试中，我们将复制与之前相同的步骤，但这次将测试本地通知。 | 预期的结果是每次满足匹配条件时都显示本地通知。 |
| 16 | 配置新的应用程序内消息（类型=广播）。 |  |
| 16a | 在触发器中，选择 **[!UICONTROL 地标事件类型]** - **[!UICONTROL 作为触发器的条目]**. |  |
| 16b | 选择Places自定义元数据作为附加筛选器 — 使用 **[!UICONTROL POI类型]** = **[!UICONTROL 上次进入的POI]**. |  |
| 16c | 选择自定义元数据键，以帮助您缩小接收消息的POI范围。 |  |
| 16d | 对于频率和持续时间，请仅保留一或两天，这样当您不喜欢该标准时，可以在更短的时间内使触发器过期。 |  |
| 16e | 对于Always/Once或Until点进， **[!UICONTROL 始终]**. |  |
| 16f | 对于显示类型，选择 **[!UICONTROL 本地通知]**. |  |
| 16g | 准备/确认并部署应用程序内消息。 |  |
| 17 | 在开发人员环境中，连接设备并按 **[!UICONTROL 播放]** 在内部版本上。 确定位置正常工作后，将应用程序置于后台并继续在Xcode或Android Studio中切换位置。 您仍然应该会看到指示位置更改的控制台读出，并且您还应该会看到根据触发器中设置的标准显示的本地通知。 （可能会有1-2秒的延迟。） | 预期的结果是每次满足匹配条件时都显示本地通知。 |
|  | **摘要点** <br>在此阶段，我们应会看到本地环境中的POI条目。 我们还应基于POI工作流程查看Campaign中的消息。 如果失败，请检查Slack通知是否未发出。 如果没有Slack消息，请检查应用程序控制台，因为可能尚未记录新的位置条目。 如果结果成功，那么我们可以非常肯定地看到应用程序正在正确执行，并且Places Service和Campaign消息服务也在正确运行。 |  |
|  | **现场测试** <br>在位置上进行测试时，应该不会发生太大变化。 保持Slack回发处于活动状态应该有助于了解设备是否获得位置的进入和退出。 |  |
| 18 | 对设备进行测试，首先禁用wifi和移动设备，然后在POI区域中启用一次。 | 如果失败，请记下是否在Slack中获取地理围栏条目和通知。 Slack通知上的时间戳是什么？ |
| 19 | 在仅启用蜂窝网络并关闭wifi的情况下执行测试。 |  |
| 20 | 在打开手机网络和WiFi的情况下进行测试。 |  |
|  | **摘要点** <br>现场测试应该与开发测试紧密配合。 请记住，在确定用户位置时，可能会有一些环境因素起作用，例如POI地理围栏中的逗留时间、小区信号的可用性和附近WiFi接入点的强度。 |  |

## 日志示例

**步骤8 ：** 位置更新期间预期iOS和Android日志

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**步骤9 ：** 事件期间的预期iOS和Android日志

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
