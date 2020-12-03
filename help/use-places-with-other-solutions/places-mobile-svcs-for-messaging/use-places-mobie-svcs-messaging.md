---
title: 将Places Service与Mobile Services结合使用以进行消息传递
description: 本节向您介绍如何将Places Service与Mobile Services结合使用以进行消息传递。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 1%

---


# Adobe Mobile Services {#places-mobile-services}

在使用Mobile Services扩展进行消息传递之前，请查看以下先决条件：

* 已在Places Service中创建兴趣点。 For more information, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >Places Service包括一个新的和经过改进的POI数据库，该数据库适用于您的组织，它存在于传统Mobile Services UI之外。 位于Mobile Service“管理位置”页 *面导航* 上的POI仅适用于SDK的版本4。

* 以下是旧 *版SDK* Mobile Services UI中的“管理地点POI”管理页：

   ![旧版UI](/help/assets/legacy-location-v4-ui.png)

* 下面是Places服务UI:

   ![Places Service POI管理UI](/help/assets/places-ui.png)

* ACP SDK正确配置了Places Service和／或Places Monitor扩展。

   这意味着数据在您的移动应用程序的事件规则引擎中可作为Experience Platform Launch和／或条件可用。 有关详细信息，请参 [阅“地点扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md) ” [或“地点监视器扩展](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)”。

* 熟悉在您的移动应用程序中创建Experience Platform Launch规则并将其发布到ACP SDK。

   For more information, see [Rules engine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch数据元素是从Places扩展数据创建的，这些扩展数据将在规则引擎中使用。

   For more information, see [Data elements](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## 报表

在使用报告之前，请完成以下先决条件：

* 成功将Places Service数据发送到Adobe Analytics报告套件。

   有关详细信息，请参 [阅将Places服务与Adobe Analytics结合使用](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)。

* 熟悉Mobile Services报告。

   For more information, see [Reports](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## 报告可视化

您可以使用发送到Adobe Analytics的Places Service数据运行Mobile Service报告。 在以下示例中，当用户在其中一个POI中有条目时，会发送事件。 在此报告中，POI条目事件的过滤器已添加到现成的用户报告中：

![报表可视化](/help/assets/report-visualize.png)

在Adobe Analytics界面中可以更灵活地可视化Places Service数据。

