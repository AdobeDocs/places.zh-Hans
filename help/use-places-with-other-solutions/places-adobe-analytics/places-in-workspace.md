---
title: Analytics Workspace中位置数据的报告
description: 本节提供有关如何在Analytics Workspace中报告位置数据的信息。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 9%

---


# Analytics Workspace中位置数据的报告 {#places-in-workspace}

此文档显示了如何在Analytics Workspace中报告位置数据的示例。 每个步骤都将包含一个高级摘要，其中通过引用其他文档页面提供详细信息。

## 先决条件

此文档假定：

1. Places扩展在您的应用程序中实现。

   有关实施Places扩展的详细信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

1. Adobe Analytics用户是管理员，有权访问处理规则。

   有关处理规则的更多信息，请参阅[处理规则概述](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

1. 在Launch属性中，已为您需要的Places服务变量创建数据元素。

   有关Launch中数据元素的详细信息，请参 [阅定义数据元素](/help/use-places-launch-workflow/define-data-elements.md)。


## 1.创建启动规则

创建一条规则，使SDK在设备进入POI时向Analytics发送数据。 在将POI输入和退出数据发 [送到Analytics页面上介绍了如何创建此类规](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) 则。

在此示例中，规则的操作具有为Analytics请求定义的以下值：

* **[!UICONTROL Action]** 值 **[!UICONTROL Places Entry]**。

* 上下文数据 **[!UICONTROL poi.name]** 键被设置为数据元素的值 **[!UICONTROL {%%POI Name%%}]**。

![&quot;设置操作&quot;](/help/assets/pt-setAction.png)

## 2.创建分析变量

要映射上下文数据（在步骤1中发送），必须首先为Analytics报表包创建变量。 有关在Analytics中创建变量的详细信息，请参 [阅转换变量(eVar)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html)。

在此示例中，已创建并 **[!UICONTROL Evar2]**&#x200B;命名转换变量 **[!UICONTROL Places POI Name]**。 需要为要以报告形式显示的每个位置变量创建其他变量。

![“创建分析变量”](/help/assets/aa-evar.png)

## 3.创建处理规则

需要此步骤将上下文数据（步骤1）映射到Analytics变量（步骤2）。 For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/admin-tools/processing-rules/processing-rules.html).

在此示例中，已创建处理规则以将上下文数据值映射 **[!UICONTROL poi.name]** 到 **[!UICONTROL Places POI Name (eVar2)]**。 需要为创建的每个位置变量创建其他处理规则。

![&quot;创建处理规则&quot;](/help/assets/aa-processing-rule.png)

## 4.在Workspace中生成报告

此步骤显示Analytics Workspace中的基本报告，以视图在步骤1-3中收集的数据。 有关如何使用Analytics Workspace的更多信息，请参阅 [Analytics Workspace概述](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/analysis-workspace/analysis-workspace-features.html)。

在此示例中，报表具有以下设置：

* 量度 - **[!UICONTROL Occurrences]**

* 维度 - **[!UICONTROL Action Name]**

   * 按Dimension细分- **[!UICONTROL Places POI Name]**

![“在工作区中创建报告”](/help/assets/aa-workspace.png)
