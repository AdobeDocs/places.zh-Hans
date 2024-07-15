---
title: 将Places服务与Mobile Services结合使用进行消息传递
description: 此部分将向您展示如何将Places服务与Mobile Services结合使用来进行消息传送。
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

在使用Mobile Services扩展进行消息传送之前，请查看以下先决条件：

* 已在Places Service中创建目标点。 有关详细信息，请参阅[创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。

  >[!IMPORTANT]
  >
  >Places服务为您的组织包含一个新的、经过改进的POI数据库，该数据库位于旧版Mobile Services UI之外。 位于Mobile Service *管理位置*&#x200B;页面导航中的POI将仅适用于SDK版本4。

* 以下是旧版SDK的旧版Mobile Services UI中的&#x200B;*管理位置* POI管理页面：

  ![旧版UI](/help/assets/legacy-location-v4-ui.png)

* 这是Places服务UI：

  ![Places服务POI管理UI](/help/assets/places-ui.png)

* ACP SDK已正确配置了Places扩展。

  这意味着数据可用作移动设备应用程序的Experience Platform Launch规则引擎中的事件和/或条件。 有关详细信息，请参阅[Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

* 熟悉如何在移动应用程序中创建Experience Platform Launch规则并将其发布到ACP SDK。

  有关详细信息，请参阅[规则引擎](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)。

* Experience Platform Launch数据元素是从将在Rules引擎中使用的Places扩展数据创建的。

  有关详细信息，请参阅[数据元素](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)。

## 报告

在使用报表之前，请完成以下先决条件：

* 成功将Places服务数据发送到Adobe Analytics报表包。

  有关详细信息，请参阅[将Places服务用于Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)。

* 熟悉Mobile Services报表。

  有关详细信息，请参阅[报告](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=zh-Hans)。

## 报表可视化

您可以使用发送到Adobe Analytics的Places Service数据来运行Mobile Service报表。 在以下示例中，当用户在其中一个POI中拥有条目时会发送事件。 在此报表中，POI登入事件的过滤器已添加到现成的用户报表中：

![报表可视化图表](/help/assets/report-visualize.png)

在Adobe Analytics界面中，增加了可视化Places服务数据的灵活性。
