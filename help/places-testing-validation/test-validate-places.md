---
title: 测试和验证地点
description: 本节提供有关如何测试和验证地点的信息。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# 测试位置服务的建议 {#test-validate-loc-svc}

许多客户和组织将在全球范围内定义POI，因此，有一种方法可以模拟和测试位置服务如何与您的应用程序交互非常重要。

此信息有助于您了解如何测试和验证根据定义的POI和用户当前位置正确触发的位置服务条目和退出。

由于环境变量可能是位置信号和准确性的一个因素，我们建议您首先通过本地使用开发人员工具和模拟位置条目来建立基准结果。 此处的目标是验证所有位置事件是否正确工作。

在正确验证位置事件后，可以测试解决方案集成（例如，Analytics、Target和Campaign）。 为了帮助您的测试活动，您应设置Slack Webhooks（带回发）并在您的单个开发环境中加载GPX文件。

>[!IMPORTANT]
>
>此计划假定已在 [Location Service Management UI中创建POI](https://places.adobe.com) ，并且安装并正确配置了最新版本的Places扩展和Places Monitor扩展。

| 步骤 | 描述 | 预期结果 |
|--- |--- |--- |
| 1 | 确认已为Android输入了正确的清单密钥以授予对跟踪位置的访问权限。 有关详细信息，请参 [阅向清单添加权限](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest)。 | 已确认 |
| 1a | 确认在iOS中配置了位置更新。 另外，请确保在iOS中设置了相应的plist键，以请求用户跟踪位置的权限。 有关详细信息，请参 [阅在后台启用位置更新。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | 已确认 |
| 2 | 确认为iOS设置了哪种监视模式。 该连续模式允许更高的准确度和持久性，但也允许更大的消耗电池寿命。 有关详细信息，请参 [阅监视模式（仅限iOS）。](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | 重大变动或持续 |
| 3 | 如果使用多个POI库，请确认已在Places extension for Experience Platform Launch中选择了相应的库。 | 已确认 |
| 4 | 确认最新版Mobile Core和Places/Places Monitor扩展已通过Gradle或CocoaPod与应用程序绑定。 | 已确认——有关最近更新的详细信息，请参阅 [发行说明。](/help/release-notes.md) |
| 5 | 确认已为测试配置了正确的环境。 启动环境ID应与您的启动开发环境相匹配。 | 已确认 |
| 6 | 为要测试的每个POI创建GPX文件。 GPX文件可在本地开发环境中用于模拟位置条目。 有关创建和使用GPX文件的信息，请参阅以下内容：用于 <br>[iOS模拟器的GPX文件[已关闭]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION在移动应用程序中测试](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | 将在应用程序项目中创建并加载GPX文件。 |
| 7 | 无需执行任何其他操作，您应能够从Android studio或XCode启动应用程序并查看相应的警报以请求对跟踪位置的访问。 单击“始 *终允许* ”权限。<br><br>我们建议您使用连接到计算机的实际设备而不是使用设备模拟器。 | 位置请求提示应在通过IDE加载的应用程序上显示 |
| 8 | 接受“位置”权限后。 Places SDK将检索设备的当前位置，而Places Monitor扩展将从当前位置开始监视20个最接近的POI | 请参阅表下的日志示例。 |
| 9 | 在XCode或Android Studio中的不同位置之间切换应为特定POI生成条目事件。 进入POI时应使用以下日志。 | 请参阅表下的日志示例。 |
| 10 | 在您看到“地点监视器”找到附近的POI后，您应该通过发送位置ping来测试。 在Launch中，创建一个新规则，该规则使用Places扩展根据地域围栏条目触发。 然后，使用Mobile Core发送回发，以创建新操作。 创建Slack Webhook应用程序可帮助您查看位置条目和退出。 有关创建Slack Webhook应用程序的信息，请参阅使 [用传入的Webhook发送消息。](https://api.slack.com/messaging/webhooks) |  |
| 10a | 在Launch中，确保为Places扩展添加了数据元素，包括：当前 <br>POI名<br>称当前POI<br>longLast Entered<br>nameLastEntered<br>LatEntered<br><br><br><br><br>LongLastExistedName退出LastLastLastLastLastLastLastLastEmastamp |  |
| 10b | 使用“事件=地点”→“进入POI”创建新规则 |  |
| 10c | 创建一个操作=“移动核心”→“回传” |  |
| 10d | 使用Slack应用程序的Webhook URL，例如https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD.... |  |
| 10e | 员额机构类似于： `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>确保您使用在此处创建的特定数据元素。 |  |
| 10f | 确保发布启动项中的所有新数据元素和规则更改。 （应在启动界面的右上角选择一个工作开发库。） |  |
| 11 | 通过在开发人员IDE中的GPX位置之间切换，再次启动并测试您的应用程序。 | 现在，当您在开发环境中选择不同位置时，您应当看到Slack通知，显示每个POI的条目。 |
|  | **快速摘**<br>&#x200B;要此测试的所有点都可以在本地进行，无需转到特定的POI位置。 验证测试有助于确保您的应用程序配置正确且已获得该位置的正确权限。 <br><br>通过此验证，您还可以确信定义的POI可以正确使用“地点监视器”扩展。  在此步骤之后，我们将开始在Campaign中测试消息传递，以查看是否根据POI进入和退出显示正确的消息。 |  |
|  | **使用位置服务测试Adobe Campaign Standard应用程序内消息传递。** |  |
| 12 | 在主营销活动控制板上，配置新的应用程序内消息（类型=广播） |  |
| 12a | 在触发器中，选 **择“放置事件类型——条目”作为触发器**。 |  |
| 12b | 选择 **[UICONTROL将自定义元数据放置为其他过滤器]**-使用POI类型=上次输入的POI。<br>我们**[!UICONTROL Last Entered]** 使用POI类型，因为在大多数情况下， **[!UICONTROL Last Entered]**将与相同**[!UICONTROL Current POI]**。 <br><br>**[!UICONTROL Current POI]** 只应在POI地理围栏重叠的情况下使用。 在这种情况下，这些POI需要为RANKED，然后 **[!UICONTROL Current POI]**将在用户当前可能位于的2或3个地理围栏中显示排名最前的POI。 |  |
| 12c | 选择自定义元数据键，帮助您缩小将收到消息的POI。 |  |
| 12d | 对于频率和持续时间，请仅保持一或两天，这样，如果您不喜欢该条件，可以在更短的时间内使触发器过期。 |  |
| 12e | 对于“总是／一次”或“直到点进”，选择“总 *是* ”，以便您可以跨多个位置进行测试。 | 当您模拟符合相应元数据条件的位置更改时，将始终显示应用程序内消息。 |
| 12f | 对于显示，请选择“本地通知”以外的选项。 这样，在前台使用应用程序进行测试时就更容易看到。) |  |
| 12g | 准备／确认和部署应用程序内消息。 |  |
| 13 | 在开发环境中，要确保下载新的营销活动规则，请退出并再次启动应用程序。 | 不要忘记必须再次完全启动应用程序才能将新的Campaign规则文件下载到设备。 |
| 14 | 在开发应用程序中，使用先前创建的GPX文件切换位置。 | 您应当看到基于之前设置的条件显示应用程序内消息。 |
| 15 | 对于下一次测试，我们实质上将复制与之前相同的步骤，但这次我们将测试LOCAL NOTIFICATION。 | 期望的结果是每次满足匹配条件时都显示本地通知。 |
| 16 | 配置新的应用程序内消息（类型=广播）。 |  |
| 16a | 在触发器中，选 **[!UICONTROL Places event type]**择-**[!UICONTROL Entry as the trigger]**。 |  |
| 16b | 选择“放置自定义元数据”作为其他过滤器- **[!UICONTROL POI type]**使用=**[!UICONTROL Last Entered POI]**。 |  |
| 16c | 选择自定义元数据键，帮助您缩小将收到消息的POI。 |  |
| 16d | 对于频率和持续时间，只保留一或两天，这样，如果您不喜欢该条件，就可以在更短的时间内使触发器过期。 |  |
| 16e | 对于“始终／一次”或“直到点进” **[!UICONTROL ALWAYS]**。 |  |
| 16f | 对于显示类型，选择 **[!UICONTROL Local Notification]**。 |  |
| 16g | 准备／确认和部署应用程序内消息。 |  |
| 17 | 在开发人员环境中，连接设备并按 **[!UICONTROL Play]**内部版本。 在确定该位置正在工作后，对应用程序进行后台处理并继续在Xcode或Android studio中切换位置。 您仍应看到指示位置更改的控制台读出内容，并且还应看到根据触发器中设置的条件显示的本地通知。 （可能会有1-2秒的延迟。） | 期望的结果是每次满足匹配条件时都显示本地通知。 |
|  | **摘要** 在此 <br>阶段，我们应该看到本地环境中的POI条目。 我们还应该看到Campaign基于POI工作的消息。 如果出现故障，请检查Slack通知是否未发出。 如果没有Slack消息，请检查应用程序控制台，因为可能没有记录新的位置条目。 如果结果成功，我们可以相当确定应用程序是否正确运行，以及位置服务和营销活动消息服务是否也正常运行。 |  |
|  | **现场测试在位**<br>置上进行测试时，应该不会有太大变化。 保持slack回发活动有助于了解设备是否有位置的进入和退出。 |  |
| 18 | 在禁用wifi和蜂窝状电话的情况下开始进行测试，然后在POI区域启用一次。 | 如果出现故障，请记住是否在Slack中获得地理围栏条目和通知。 Slack通知的时间戳是多少？ |
| 19 | 在仅启用蜂窝和关闭wifi的情况下进行测试。 |  |
| 20 | 在打开蜂窝和wifi的情况下进行测试。 |  |
|  | **SUMMARY POINT** <br>On-site测试应与开发测试紧密匹配。 请记住，在确定用户位置时可能会出现一些环境因素，例如在POI地理围栏中停留的时间、蜂窝信号的可用性以及附近wifi接入点的强度。 |  |

## 日志示例

**** 第8步：位置更新期间需要iOS和Android日志

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

**** 第9步：事件期间需要iOS和Android日志

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
