---
title: 将Places Service与Mobile Services结合使用以进行消息传送
description: 此部分将向您展示如何将Places Service与Mobile Services结合使用来进行消息传送。
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

在使用Mobile Services扩展进行消息传送之前，请查看以下先决条件：

* 已在Places Service中创建目标点。 有关更多信息，请参阅 [创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Places Service包含一个新的和经过改进的POI数据库，该数据库适用于旧版Mobile Services UI之外的组织。 位于Mobile Service上的POI *管理位置* 页面导航仅适用于SDK版本4。

* 以下是 *管理位置* 旧版Mobile Services UI中的POI管理页面（对于旧版SDK）：

   ![旧版UI](/help/assets/legacy-location-v4-ui.png)

* 以下是Places Service UI:

   ![Places Service POI管理UI](/help/assets/places-ui.png)

* ACP SDK已正确配置了Places扩展。

   这意味着数据可在移动设备应用程序的Experience Platform Launch规则引擎中作为事件和/或条件使用。 有关更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* 熟悉如何在您的移动应用程序中创建Experience Platform Launch规则并将其发布到ACP SDK。

   有关更多信息，请参阅 [规则引擎](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch数据元素是从Places扩展数据创建的，这些数据将在规则引擎中使用。

   有关更多信息，请参阅 [数据元素](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## 报告

在使用报表之前，请完成以下先决条件：

* 已成功将Places Service数据发送到Adobe Analytics报表包。

   有关更多信息，请参阅 [将Places Service与Adobe Analytics结合使用](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* 熟悉Mobile Services报表。

   有关更多信息，请参阅 [报表](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## 报表可视化

您可以使用发送到Adobe Analytics的Places Service数据运行Mobile Service报表。 在以下示例中，当用户在其中一个POI中具有条目时，将发送事件。 在此报表中，在现成用户报表上添加了POI条目事件的过滤器：

![报表可视化](/help/assets/report-visualize.png)

在Adobe Analytics界面中，可以更灵活地显示Places Service数据。
