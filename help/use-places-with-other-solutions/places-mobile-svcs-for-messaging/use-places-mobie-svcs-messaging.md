---
title: 将地点与Mobile services结合使用以进行消息传递
seo-title: 将地点与Mobile services结合使用以进行消息传递
description: 本节将向您介绍如何将Places与Mobile services结合使用以进行消息传递。
seo-description: 本节将向您介绍如何将Places与Mobile services结合使用以进行消息传递。
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Adobe Mobile Services {#places-mobile-services}

在使用Mobile services扩展进行消息传递之前，请查看以下先决条件：

* 目标点已在位置服务中创建。 如果需要，请参阅文档。 （链接到创建POI）注意：位置服务包括一个新的、经过改进的组织目标点数据库，该数据库存在于传统AMS界面之外。 在AMS的“管理地点”导航中找到的任何POI只适用于SDK版本4。
   * 以下是旧版SDK的AMS中的旧版Places POI管理界面：

      ![旧版UI](/help/assets/legacy-location-v4-ui.png)

   * 下面是位置服务POI管理界面：

      ![位置服务POI管理UI](/help/assets/places-ui.png)

* ACP SDK正确配置了地点和／或地点监视器扩展。 这意味着数据在您的移动应用程序的启动规则引擎中可用作事件和／或条件。 如果需要，请参阅文档。 (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* 熟悉如何在您的移动应用程序中创建启动规则并将其发布到ACP SDK。 如果需要，请参阅文档。 (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* 启动数据元素是从将在“规则”中使用的Places SDK扩展数据创建的。 请参阅文档(https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)

## 报表

在使用报告之前，请完成以下先决条件：

* 已成功将位置服务数据发送到Adobe Analytics Report Suite。 如果需要，请访问Adobe Analytics文档（链接到Steve的文档）。
* 熟悉AMS报告。 如有需要，请访问文档(https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)

## 报告可视化

您可以使用发送到Adobe Analytics的位置服务数据运行AMS报告。 例如，当用户在某个POI中有条目时，我已发送活动。 在此报告中，我在现成的用户报告上添加了POI条目事件的过滤器：

![报告可视化](/help/assets/report-visualize.png)

在Adobe Analytics界面中可以更灵活地可视化位置服务数据。

