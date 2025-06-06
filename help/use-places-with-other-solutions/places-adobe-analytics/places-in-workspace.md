---
title: 在Analytics Workspace中报告位置数据
description: 本节介绍如何在Analytics Workspace中报告位置数据。
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 2%

---

# 在Analytics Workspace中报告位置数据 {#places-in-workspace}

本文档展示了如何在Analytics Workspace中报告位置数据的示例。 每个步骤都将包含一个高级摘要，通过引用其他文档页面提供了详细信息。

## 先决条件

本文档假设以下内容：

1. Places扩展在您的应用程序中实施。

   有关实施Places扩展的详细信息，请参阅[Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

1. Adobe Analytics用户是管理员，有权访问处理规则。

   有关处理规则的更多信息，请参阅[处理规则概述](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=zh-Hans)。

1. 在Launch属性中，已为您所需的Places服务变量创建数据元素。

   有关Launch中的数据元素的更多信息，请参阅[定义数据元素](/help/use-places-launch-workflow/define-data-elements.md)。


## 1.创建Launch规则

创建一个规则，以使SDK在设备进入POI时将数据发送到Analytics。 在[将POI登入和退出数据发送到Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)页面上描述了创建此类规则。

在此示例中，规则的操作具有为Analytics请求定义的以下值：

* 为&#x200B;**[!UICONTROL 操作]**&#x200B;提供的值为&#x200B;**[!UICONTROL Places条目]**。

* 上下文数据键&#x200B;**[!UICONTROL poi.name]**&#x200B;设置为数据元素&#x200B;**[!UICONTROL {%%POI Name%%}]**&#x200B;的值。

![“设置操作”](/help/assets/pt-setAction.png)

## 2.创建Analytics变量

要映射上下文数据（在步骤1中发送），必须首先为Analytics报表包创建变量。 有关在Analytics中创建变量的更多信息，请参阅[转化变量(eVar)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=zh-Hans)。

在此示例中，已创建转化变量&#x200B;**[!UICONTROL Evar2]**，并将其命名为&#x200B;**[!UICONTROL Places POI名称]**。 需要为要在报表中公开的每个位置变量创建其他变量。

![“创建分析变量”](/help/assets/aa-evar.png)

## 3.创建处理规则

将上下文数据（步骤1）映射到Analytics变量（步骤2）时需要此步骤。 有关创建处理规则的更多信息，请参阅[处理规则概述](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=zh-Hans)。

在此示例中，已创建处理规则以将上下文数据值&#x200B;**[!UICONTROL poi.name]**&#x200B;映射到&#x200B;**[!UICONTROL Places POI名称(eVar2)]**。 需要为创建的每个位置变量创建其他处理规则。

![“创建处理规则”](/help/assets/aa-processing-rule.png)

## 4.在Workspace中生成报表

此步骤显示Analytics Workspace中的基本报表，用于查看在第1-3步中收集的数据。 有关如何使用Analytics Workspace的更多信息，请参阅[Analytics Workspace概述](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=zh-Hans)。

在此示例中，报表具有以下设置：

* 量度 — **[!UICONTROL 发生次数]**

* Dimension- **[!UICONTROL 操作名称]**

   * 按Dimension细分 — **[!UICONTROL 地标POI名称]**

![“在工作区中创建报告”](/help/assets/aa-workspace.png)
