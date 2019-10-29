---
title: 应用程序内消息传递
seo-title: 应用程序内消息传递
description: 本节将向您介绍如何将地点与应用程序内消息传递结合使用。
seo-description: 本节将向您介绍如何将地点与应用程序内消息传递结合使用。
translation-type: tm+mt
source-git-commit: 7985943cef606525401983c4c80862c277f41bf0

---


# 应用程序内通知(#places-push-messaging)

如何配置应用程序内消息以从Places事件触发；消息必须位于Analytics点击中。

## 应用程序内消息

AMS允许您使用发送到Analytics的位置数据作为应用程序内消息的触发事件和／或条件。 从SDK触发触发器后，应用程序内消息可立即实时显示给用户，无需等待Analytics处理数据。

本地通知：应用程序内消息传递有3种不同类型：

* 全屏消息
* 警报
* 本地通知。

这些类型符合应用程序内消息的条件，因为它们是由SDK触发的，但必须注意，当应用程序不在前台时，本地通知的外观和感觉就像推送通知一样。 本地通知是在应用程序处于后台时向用户发送进入或退出POI的实时通知的极好选项。 请参阅Places Monitor扩展文档以了解位置监视(https://placesdocs.com/places-services-by-adobe-documentation/configure-places-in-the-sdk/places-monitor-extension)。

### 先决条件

* 了解如何在AMS中发送和创建应用程序内消息以及触发器的工作方式。

   有关更多信息，请参阅[创建应用程序内消息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)。


## 在Experience Platform Launch中创建规则

创建启动规则，该规则将正确的数据发送到Analytics，以便能够作为应用程序内消息触发规则的一部分使用。 您可以根据用例，将Launch规则中“地点”扩展中的数据用作事件和／或条件。

* 使用位置数据作为触发事件。 例如，如果要在用户进入POI时向Analytics发送数据。

* 将位置数据用作触发事件的条件。 例如，如果您在位置服务中为不同POI的天气创建了自定义元数据标记，则可以将该元数据用作您的规则条件的参数，如下所示。 尽管可以将此条件用于前面所述的POI条目事件，但也可以将它用作任何事件的上下文。

使用正确的事件和条件参数设置规则后，通过配置将数据发送到Analytics的操作，完成规则配置。 为此，请执行以下操作：

* 选择Adobe Analytics作为扩展
* 选择“跟踪”作为操作类型
* 确定操作的名称
* 设置与活动一起发送的上下文数据。 使用上下文数据界面将启动数据元素映射到要发送到Analytics的键名。

请注意，可以设置Analytics处理规则来获取此上下文数据。 如有需要，请参阅分析处理规则(https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)例如，此操作将以上下文的形式在点名中发送，以描述要发送到Analytics的POIentry事件。

![创建操作](/help/assets/configure-action.png)

下面是一个示例，说明完成的规则的外观。

![完整规则](/help/assets/create-a-rule.png)

## 在AMS中创建应用程序内消息：

您将使用来自位置服务的数据作为触发器参数的一部分来创建消息的受众。

* 使用特定于位置的操作，如进入或退出
* 使用作为上下文数据发送的POI元数据缩小受众的目标范围。 这可以与特定位置的操作（如条目）一起使用，也可以用作启动项或按钮单击等其他事件的上下文。

   下面是一个示例，说明如何为欢迎用户设置应用程序内消息，这些用户在名称中输入的POI中包含“Adobe”:

   ![触发参数](/help/assets/trigger-parameters.png)

* 在AMS触发器和特征中的“地点”标题中找到的参数不能用于位置服务中的数据。 这些参数用于在AMS中创建的传统Places数据库。