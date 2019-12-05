---
title: Analytics Workspace中位置数据的报告
description: 本节提供有关如何在Analytics Workspace中报告位置数据的信息。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Analytics Workspace中位置数据的报告 {#places-in-workspace}

本文档展示了如何在Analytics Workspace中报告位置数据的示例。 每个步骤都将包含一个高级摘要，其详细信息通过引用其他文档页面来提供。

## 先决条件

本文档假定：

1. Adobe Places扩展是在您的应用程序中实现的。 有关实施Adobe Places的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

1. Adobe Analytics用户是管理员，有权访问处理规则。 有关处理规则的更多信息，请参阅[处理规则概述](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

1. 在“启动”属性中，已为所需的位置服务变量创建数据元素。 有关Launch中数据元素的详细信息，请参 [阅定义数据元素](/help/use-places-launch-workflow/define-data-elements.md)。


## 1.创建启动规则

创建一个规则，该规则将导致SDK在设备进入POI时向Analytics发送数据。 将POI条目和退出数据发送到 [Analytics页面中介绍了如何创建此类规则](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) 。

在此示例中，规则的操作为Analytics请求定义了以下值：

* **[!UICONTROL Action]** 提供值 **[!UICONTROL Places Entry]**。

* 上下文数据键 **[!UICONTROL poi.name]** 被设置为数据元素的值 **[!UICONTROL {%%POI Name%%}]**。

![“设置操作”](/help/assets/pt-setAction.png)

## 2.创建分析变量

要映射上下文数据（在步骤1中发送），必须首先为Analytics报表包创建变量。 有关在Analytics中创建变量的详细信息，请参 [阅Conversion variables \(eVars\)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html)。

在此示例中，已创建并命 **[!UICONTROL Evar2]**&#x200B;名转换变量 **[!UICONTROL Places POI Name]**。 需要为要在报告中显示的每个位置变量创建其他变量。

![“创建分析变量”](/help/assets/aa-evar.png)

## 3.创建处理规则

需要此步骤才能将上下文数据（步骤1）映射到Analytics变量（步骤2）。 For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

在此示例中，已创建处理规则以将上下文数据值映射到 **[!UICONTROL poi.name]** 中 **[!UICONTROL Places POI Name \(eVar2\)]**。 需要为创建的每个位置变量创建其他处理规则。

![“创建处理规则”](/help/assets/aa-processing-rule.png)

## 4.在Workspace中生成报告

此步骤在Analytics Workspace中显示一个基本报告，用于查看在步骤1-3中收集的数据。 有关如何使用Analytics Workspace的更多信息，请参阅 [Analytics Workspace概述](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html)。

在此示例中，报表具有以下设置：

* Metric - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Action Name]**

   * 按维度细分- **[!UICONTROL Places POI Name]**

![“在工作区中创建报告”](/help/assets/aa-workspace.png)
