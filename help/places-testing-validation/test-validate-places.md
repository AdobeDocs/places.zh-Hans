---
title: 测试和验证Places服务
description: 本节提供有关如何测试和验证Places服务的信息。
translation-type: tm+mt
source-git-commit: 954bd9a12ede841d189138dfbe3d65ad4c1bd3c3
workflow-type: tm+mt
source-wordcount: '1735'
ht-degree: 2%

---


# Recommendations将测试Places服务 {#test-validate-loc-svc}

许多客户和组织将在全球范围内定义POI，因此，有一种方法来模拟和测试Places Service如何与您的应用程序交互非常重要。 此信息有助于您了解如何测试和验证根据定义的POI和用户当前位置正确触发的Places Service条目和退出。

由于环境变量可能是位置信号和准确度的一个因素，我们建议您首先使用本地开发人员工具和模拟位置条目建立基准结果。 目标是验证所有位置事件是否正确工作。 正确验证位置事件后，可测试解决方案集成(例如分析、目标和活动)。 为了帮助您的测试活动，您应使用回传设置SlackWebhook，并在您的单个开发环境中加载GPX文件。

>[!IMPORTANT]
>
>此计划假设POI已在Places Service UI中 [创建](https://places.adobe.com) ，并且安装并正确配置了最新版本的Places扩展和Places Monitor扩展。 有关详细信息，请参 [阅“地点扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md) ” [和“地点监视器扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)”。

| 步骤 | 描述 | 预期结果 |
|--- |--- |--- |
| 1 | 确认已为Android输入正确的清单密钥以授予对跟踪位置的访问权限。 有关详细信息，请参 [阅向清单添加权限](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest)。 | 已确认 |
| 1a | 确认在iOS中配置了位置更新。 另外，请确保在iOS中设置了相应的plist键，以请求用户跟踪位置的权限。 有关详细信息，请 [参阅在后台启用位置更新。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | 已确认 |
| 2 | 确认为iOS设置了哪种监视模式。 连续模式允许更高的准确性和持久性，同时也使电池寿命消耗更多。 有关详细信息，请参 [阅监视模式（仅限iOS）。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | 重大变化或持续 |
| 3 | 如果使用多个POI库，请确认已在“位置”扩展中选择了相应的库以进行Experience Platform Launch。 | 已确认 |
| 4 | 确认最新版Mobile Core和Places/Places Monitor扩展已通过Gradle或CocoaPods与应用程序绑定。 | 已确认——有关最新更新的详细信息，请参 [阅发行说明。](/help/release-notes.md) |
| 5 | 确认已为测试配置了正确的环境。 启动环境ID应与启动项开发环境匹配。 | 已确认 |
| 6 | 为要测试的每个POI创建GPX文件。 GPX文件可用于本地开发环境以模拟位置条目。 有关创建和使用GPX文件的信息，请参阅： <br>[iOS模拟器的GPX文件[已关闭]https://mapstogpx.com/mobiledev.](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[php移动应](https://mapstogpx.com/mobiledev.php)<br>[用程序中的位置测试](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | 将在应用程序项目中创建并加载GPX文件。 |
| 7 | 无需执行任何其他操作，您应能够从Android Studio或XCode启动应用程序并查看相应的警报以请求对跟踪位置的访问权限。 单击“始 *终允许* ”权限。<br><br>我们建议您使用连接到计算机的真实设备，而不是使用设备模拟器。 | 位置请求提示应在通过IDE加载的应用程序上显示 |
| 8 | 接受“位置”权限后。 Places SDK将检索设备的当前位置，而Places Monitor扩展将开始从当前位置监视最近的20个POI | 请参阅表下的日志示例。 |
| 9 | 在XCode或Android studio中的不同位置之间切换应为特定POI生成入口事件。 进入POI时应使用以下日志。 | 请参阅表下的日志示例。 |
| 10 | 当您看到位置监视器找到附近的POI后，您应通过发送位置ping来进行测试。 在Launch中，创建一个新规则，该规则使用Places扩展根据地理围栏条目触发。 然后，使用Mobile Core发送回传，创建新动作。 创建SlackWebhook应用程序可帮助您查看位置条目和退出。 有关创建SlackWebhook应用程序的信息，请参 [阅使用传入Webhook发送消息。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 在Launch中，确保为Places扩展添加了数据元素，包括： <br>当前POI名<br>称当前POI<br>longLast Entered<br>name当前POI<br>last Entered<br>latLatEntered<br>latDesitd<br><br><br>nameLastLast退出LatLongTimestamp |  |
| 10b | 使用事件=位置→进入POI创建新规则 |  |
| 10c | 创建操作=移动核心→回传 |  |
| 10d | 将Webhook URL用于您的Slack应用程序，例如https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | 员额机构类似于： `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>确保您使用在此处创建的特定数据元素。 |  |
| 10f | 确保发布启动项中的所有新数据元素和规则更改。 （您应在启动界面的右上角选择一个工作开发库。） |  |
| 11 | 通过在开发人员IDE中的GPX位置之间切换，再次启动并测试您的应用程序。 | 现在，当您在开发环境中选择不同位置时，您应会看到显示每个POI条目的Slack通知。 |
|  | **快速摘**<br>&#x200B;要此测试的所有内容都可以在本地进行，无需转到特定的POI位置。 验证测试有助于确保您的应用程序配置正确，并且已获得该位置的正确权限。 <br><br>此验证还可以确保定义的POI能够正确使用“地点监视器”扩展。  在此步骤之后，我们将开始测试活动消息，以查看是否根据POI进入和退出显示正确消息。 |  |
|  | **使用Places Service测试Adobe Campaign Standard的应用内消息传递。** |  |
| 12 | 在主活动仪表板上，配置新的应用程序内消息（类型=广播） |  |
| 12a | 在触发器中，选 **择位置事件类型-输入作为触发器**。 |  |
| 12b | 选 **[!UICONTROL Places Custom metadata]** 择作为附加筛选器——使用POI类型=上次输入的POI。<br>我们 **[!UICONTROL Last Entered]** 用作POI类型，因为在大多数情况下 **[!UICONTROL Last Entered]** ，将与相同 **[!UICONTROL Current POI]**。 <br><br>**[!UICONTROL Current POI]**应仅在存在重叠的POI地理围栏的情况下使用。 在这种情况下，这些POI需要为RANKED，然&#x200B;**[!UICONTROL Current POI]**后在用户当前可能处于的2个或3个地理围栏中显示排名最前的POI。 |  |
| 12c | 选择自定义元数据密钥，以帮助您缩小将收到消息的POI。 |  |
| 12d | 对于频率和持续时间，只保留一两天，这样，如果您不喜欢条件，可以在较短的时间内使触发器过期。 |  |
| 12e | 对于“始终／一次”或“直到点进”，选 *择“始* 终”，以便您可以跨多个位置进行测试。 | 当您模拟符合相应元数据条件的位置更改时，将始终显示应用程序内消息。 |
| 12f | 对于显示，请选择“本地通知”以外的选项。 这使得在前台使用应用程序进行测试时更容易查看。) |  |
| 12g | 准备／确认和部署应用程序内消息。 |  |
| 13 | 在开发环境中，确保下载新的活动规则，退出并再次启动应用程序。 | 不要忘记必须再次完全启动应用程序才能将新活动规则文件下载到设备。 |
| 14 | 在开发应用程序中，使用先前创建的GPX文件切换位置。 | 您应当看到根据之前设置的条件显示应用程序内消息。 |
| 15 | 对于下一次测试，我们实质上将复制与以前相同的步骤，但这次我们将测试LOCAL NOTIFICATION。 | 预期结果是每次满足匹配条件时都显示本地通知。 |
| 16 | 配置新的应用程序内消息（类型=广播）。 |  |
| 16a | 在触发器中，选 **[!UICONTROL Places event type]** 择- **[!UICONTROL Entry as the trigger]**。 |  |
| 16b | 选择“放置自定义元数据”作为附加筛选器- **[!UICONTROL POI type]** 使用 **[!UICONTROL Last Entered POI]**=。 |  |
| 16c | 选择自定义元数据密钥，以帮助您缩小将收到消息的POI。 |  |
| 16d | 对于频率和持续时间，只保留一两天，这样，如果您不喜欢条件，可以在较短的时间内使触发器过期。 |  |
| 16e | 对于“始终／一次”或“直到点进” **[!UICONTROL ALWAYS]**。 |  |
| 16f | 对于显示类型，选择 **[!UICONTROL Local Notification]**。 |  |
| 16g | 准备／确认和部署应用程序内消息。 |  |
| 17 | 在开发人员环境中，连接设备并按 **[!UICONTROL Play]** 内部版本。 在确定该位置正在工作后，对应用程序进行后台处理并在Xcode或Android Studio中继续切换位置。 您仍应看到指示位置更改的控制台读出，并且还应看到根据触发器中设置的条件显示本地通知。 （可能会有1-2秒的延迟。） | 预期结果是每次满足匹配条件时都显示本地通知。 |
|  | **摘要点**<br>在此阶段，我们应在本地环境中看到POI条目。 我们还应该看到基于POI工作的活动的消息。 如果出现故障，请检查Slack通知是否未发出。 如果没有Slack消息，请检查应用程序控制台，因为可能未记录新位置条目。 如果结果成功，我们可以非常确定应用程序是否正确运行，以及Places服务和活动消息服务是否也正常运行。 |  |
|  | **现场测试在位**<br>置上进行测试时，应该不会有太大变化。 保持松弛的回发活动有助于了解设备是否进入和退出位置。 |  |
| 18 | 在禁用wifi和蜂窝电话的情况下开始对设备进行测试，然后在POI区域启用一次。 | 如果出现故障，请记下是否在Slack中获得地理围栏条目和通知。 Slack通知上的时间戳是什么？ |
| 19 | 在仅启用手机网络并关闭wifi的情况下进行测试。 |  |
| 20 | 打开手机和wifi后进行测试。 |  |
|  | **SUMMARY POINT** 现 <br>场测试应与开发测试密切匹配。 请记住，在确定用户位置时，可能会考虑一些环境因素，例如在POI地理围栏中停留的时间、小区信号的可用性以及附近wifi接入点的强度。 |  |

## 日志示例

**第8步：** 位置更新期间需要iOS和Android日志

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**第9步：** 在事件期间需要iOS和Android日志

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
