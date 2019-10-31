---
title: 应用程序内通知
seo-title: 应用程序内通知
description: 本节将向您介绍如何将地点与应用程序内消息传递结合使用。
seo-description: 本节将向您介绍如何将地点与应用程序内消息传递结合使用。
translation-type: tm+mt
source-git-commit: a76e91775efd92ce56f2dc5cbdcc65786855b5c3

---


# 应用程序内通知(#places-push-messaging)

以下信息向您显示如何配置应用程序内消息以从“地点”事件触发。

>[!IMPORTANT]
>
>消息必须位于Analytics点击中。

## 应用程序内消息

Mobile services允许您使用发送到Analytics的位置数据作为应用程序内消息的触发事件和／或条件。 如果从SDK触发应用程序内消息并且无需等待Analytics处理数据，则触发器一旦发生，消息就可以实时显示。

### 本地通知消息

以下是可用的应用程序内消息传递类型列表：

* 全屏消息
* 警报
* 本地通知消息

这些类型是应用程序内消息，因为它们由SDK触发。 本地通知的外观和感觉就像推送通知一样，因为当应用程序处于后台时，它们会显示。 当用户在应用程序处于后台时进入或退出POI时，这些通知也会发送实时通知。 有关详细信息，请参 [阅“地点监视器扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)”。

### 先决条件

在开始之前，您会了解如何在Mobile services中发送和创建应用程序内消息以及触发器的工作方式。 For more information, see [Create an in-app message.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch 中的规则

您可以创建启动规则，这些规则将要用作应用程序内消息触发规则一部分的数据发送到Analytics。 您可以根据用例，将Launch规则中“地点”扩展中的数据用作事件和／或条件。

* 使用位置数据作为触发事件。

   例如，当用户进入POI时，您可以将数据发送到Analytics。

* 将位置数据用作触发事件的条件。

   例如，如果您在位置服务中为不同POI的天气创建了自定义元数据标记，则可以将该元数据用作规则条件的参数。 虽然可以将此条件与前面所述的POI条目事件一起使用，但也可以将该条件用作任何事件的上下文。

在使用正确的事件和条件参数设置规则后，通过配置将数据发送到Analytics的操作来完成规则配置。

## 创建操作

要创建操作，请执行以下操作：

1. 选择 **扩展。[!UICONTROL Adobe Analytics]**
1. 在下 **[!UICONTROL Action type]** 拉列表中，选择 **[!UICONTROL Track.]**
1. 键入操作的名称。
1. 在右侧窗格中， **[!UICONTROL Context Data]**&#x200B;选择键值对以设置将发送到Analytics的上下文数据。

例如，您可以选择 `poiname` 作为键和 `{%%Last Entered POI Name}` 作为值。

>[!TIP]
>
>可以设置分析处理规则来获取此上下文数据。 For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). 在创建操作 *的示例中*`poiname` ，操作将作为上下文发送，以描述要发送到Analytics的POI条目事件。

![创建操作](/help/assets/configure-action.png)

以下是完整规则的示例：

![完整规则](/help/assets/create-a-rule.png)

## 在Mobile services中创建应用程序内消息

作为触发器参数的一部分，您可以通过以下方式之一使用位置服务中的数据为消息创建受众：

* 使用特定于位置的操作，如进入或退出。
* 使用作为上下文数据发送的POI元数据缩小受众的目标范围。

   此选项可与特定位置的操作（如条目）一起使用，也可用作启动项或按钮单击等其他事件的上下文。

   下面是一个如何为欢迎用户配置应用程序内消息的示例，这些用户输入名 **[!UICONTROL Adobe]** 称中包含POI:

   ![触发参数](/help/assets/trigger-parameters.png)

* Mobile services中“触发器”和“ *特征* ”页面的“地点”标题中的参数不处理来自位置服务的数据。

   这些参数仅适用于在Mobile services中创建的传统Places数据库。