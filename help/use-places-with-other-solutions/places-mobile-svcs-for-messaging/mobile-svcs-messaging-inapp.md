---
title: 应用程序内通知
description: 此部分将向您展示如何将Places服务与应用程序内消息传送结合使用。
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# 应用程序内通知 {#places-push-messaging}

以下信息说明了如何配置要从Places Service事件触发的应用程序内消息。

>[!IMPORTANT]
>
>消息必须位于Analytics点击上。

## 应用程序内消息

Mobile Services允许您使用发送到Analytics的位置数据作为应用程序内消息的触发事件和/或条件。 如果从SDK触发应用程序内消息，而无需等待Analytics处理数据，则一旦触发即可实时显示消息。

### 本地通知消息

以下是可用的应用程序内消息传送类型列表：

* 全屏
* 警报
* 本地通知消息

这些类型是应用程序内消息，因为它们由SDK触发。 本地通知的外观和感觉类似于推送通知，因为它们会在应用程序处于后台时显示。 当应用程序处于后台时，这些通知还会在用户进入或退出您的POI时交付实时通知。

### 先决条件

在开始之前，您已了解如何在Mobile Services中发送和创建应用程序内消息以及触发器工作方式。 有关详细信息，请参阅[创建应用程序内消息。](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=zh-Hans)

## Experience Platform Launch中的规则

您可以创建Experience Platform Launch规则，将您希望能够用作应用程序内消息触发器规则一部分的数据发送到Analytics。 您可以将Places扩展中的数据用作Experience Platform Launch规则中的事件和/或条件，具体取决于您的用例。

* 使用位置数据作为触发事件。

  例如，您可以在用户输入POI时将数据发送到Analytics。

* 将位置数据用作触发事件的条件。

  例如，如果您在Places服务中为不同POI的天气创建了自定义元数据标记，则可以将该元数据用作规则条件的参数。 虽然可以将此条件与前面描述的POI进入事件一起使用，但也可以将该条件用作任何事件的上下文。

使用正确的事件和条件参数设置规则后，通过配置操作以将数据发送到Analytics来完成规则配置。

## 创建操作

要创建操作，请执行以下操作：

1. 选择&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;扩展。
1. 在&#x200B;**[!UICONTROL 操作类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 跟踪。]**
1. 键入操作的名称。
1. 在右侧窗格的&#x200B;**[!UICONTROL 上下文数据]**&#x200B;中，选择键值对以设置将发送到Analytics的上下文数据。

例如，您可以选择`poiname`作为键，`{%%Last Entered POI Name}`作为值。

>[!TIP]
>
>可以将Analytics处理规则设置为选取此上下文数据。 有关详细信息，请参阅[处理规则](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=zh-Hans)。 在&#x200B;*创建操作*&#x200B;中的示例中，该操作将发送`poiname`作为上下文，以描述发送到Analytics的POI进入事件。

![创建操作](/help/assets/configure-action.png)

以下是完整规则的示例：

![已完成规则](/help/assets/create-a-rule.png)

## 在Mobile Services中创建应用程序内消息

作为触发器参数的一部分，您可以通过以下方式之一使用Places服务中的数据创建消息的受众：

* 使用特定于位置的操作，如登入或退出。
* 使用作为上下文数据发送的POI元数据来缩小受众目标范围。

  此选项可与特定于位置的操作（如条目）一起使用，也可以用作其他事件（如启动项或按钮单击）的上下文。

  以下是如何配置应用程序内消息的示例，以欢迎输入名称中包含&#x200B;**[!UICONTROL Adobe]**&#x200B;的POI的用户：

  ![触发器参数](/help/assets/trigger-parameters.png)

* Mobile Services中&#x200B;*触发器和特征*&#x200B;页面的Places服务标题中的参数不适用于Places服务中的数据。

  这些参数仅适用于在Mobile Services中创建的旧版Places服务数据库。
