---
title: 应用程序内通知
description: 此部分将向您展示如何将Places Service与应用程序内消息传送结合使用。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 3%

---

# 应用程序内通知 {#places-push-messaging}

以下信息向您展示了如何配置应用程序内消息以从Places Service事件触发。

>[!IMPORTANT]
>
>消息必须位于Analytics点击中。

## 应用程序内消息

Mobile Services允许您使用发送到Analytics的位置数据作为应用程序内消息的触发事件和/或条件。 如果从SDK触发应用程序内消息，并且不需要等待Analytics处理数据，则触发器一旦发生，消息就会实时显示。

### 本地通知消息

以下是可用的应用程序内消息传送类型列表：

* 全屏
* 警报
* 本地通知消息

这些类型是应用程序内消息，因为它们是由SDK触发的。 本地通知的外观与推送通知类似，因为当应用程序处于后台时，会显示本地通知。 当应用程序处于后台时，当用户进入或退出您的POI时，这些通知还会提供实时通知。

### 先决条件

在开始之前，您将了解如何在Mobile Services中发送和创建应用程序内消息，以及触发器的工作方式。 有关更多信息，请参阅 [创建应用程序内消息。](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

##  Experience Platform Launch 中的规则

您可以创建Experience Platform Launch规则，以将要用作应用程序内消息触发器规则一部分的数据发送到Analytics。 您可以根据用例将Experience Platform Launch规则中Places扩展的数据用作事件和/或条件。

* 使用位置数据作为触发事件。

   例如，您可以在用户进入POI时向Analytics发送数据。

* 将位置数据用作触发事件的条件。

   例如，如果您在Places Service中为不同POI的天气创建了自定义元数据标记，则可以将该元数据用作规则条件的参数。 虽然您可以将此条件与前面介绍的POI条目事件一起使用，但也可以将该条件用作任何事件的上下文。

在使用正确的事件和条件参数设置规则后，通过配置将数据发送到Analytics的操作，完成规则配置。

## 创建操作

要创建操作，请执行以下操作：

1. 选择 **[!UICONTROL Adobe Analytics]** 扩展。
1. 在 **[!UICONTROL 操作类型]** 下拉列表中，选择 **[!UICONTROL 跟踪。]**
1. 键入操作的名称。
1. 在右侧窗格中，在 **[!UICONTROL 上下文数据]**，选择键值对以设置将发送到Analytics的上下文数据。

例如，您可以选择 `poiname` 作为键和 `{%%Last Entered POI Name}` 作为值。

>[!TIP]
>
>可以设置Analytics处理规则以获取此上下文数据。 有关更多信息，请参阅[处理规则](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)。在 *创建操作*，则操作将发送 `poiname` 作为描述要发送到Analytics的POI条目事件的上下文。

![创建操作](/help/assets/configure-action.png)

以下是完整规则的示例：

![已完成规则](/help/assets/create-a-rule.png)

## 在Mobile Services中创建应用程序内消息

在触发器参数中，您可以通过以下方式之一为使用Places Service中的数据创建消息的受众：

* 使用特定于位置的操作，例如登入或退出。
* 使用作为上下文数据发送的POI元数据来缩小受众的目标。

   此选项可与特定于位置的操作（如条目）一起使用，也可用作其他事件（如启动项或按钮单击）的上下文。

   以下是如何配置应用程序内消息以欢迎进入具有 **[!UICONTROL Adobe]** 在名称中：

   ![触发器参数](/help/assets/trigger-parameters.png)

* 中Places Service标题的参数 *触发器和特征* 页面无法处理Places Service中的数据。

   这些参数仅适用于在Mobile Services中创建的旧版Places Service数据库。
