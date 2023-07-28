---
title: 在Analytics Workspace中报告位置数据
description: 本节介绍如何在Analytics Workspace中报告位置数据。
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 5%

---

# 报告Analytics Workspace中的位置数据 {#places-in-workspace}

本文档展示了如何在Analytics Workspace中报告位置数据的示例。 每个步骤都将包含一个高级摘要，通过引用其他文档页面提供了详细信息。

## 先决条件

本文档假设以下内容：

1. Places扩展在您的应用程序中实施。

   有关实施Places扩展的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. Adobe Analytics用户是管理员，有权访问处理规则。

   有关处理规则的更多信息，请参阅[处理规则概述](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html)。

1. 在Launch属性中，已为您所需的Places服务变量创建数据元素。

   有关Launch中的数据元素的更多信息，请参阅 [定义数据元素](/help/use-places-launch-workflow/define-data-elements.md).


## 1.创建Launch规则

创建一个规则，以使SDK在设备进入POI时将数据发送到Analytics。 有关创建此类规则的说明，请参见 [将POI登入和退出数据发送到Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) 页面。

在此示例中，规则的操作具有为Analytics请求定义的以下值：

* **[!UICONTROL 操作]** 提供了以下值 **[!UICONTROL 地标条目]**.

* 上下文数据键 **[!UICONTROL poi.name]** 设置为数据元素的值 **[!UICONTROL {%%POI名称%%}]**.

![&quot;设置操作&quot;](/help/assets/pt-setAction.png)

## 2.创建Analytics变量

要映射上下文数据（在步骤1中发送），必须首先为Analytics报表包创建变量。 有关在Analytics中创建变量的更多信息，请参阅 [转化变量(eVar)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=zh-Hans).

在本例中，转化变量， **[!UICONTROL Evar2]**，已创建并命名 **[!UICONTROL 地标POI名称]**. 需要为要在报表中公开的每个位置变量创建其他变量。

![&quot;创建analytics变量&quot;](/help/assets/aa-evar.png)

## 3.创建处理规则

将上下文数据（步骤1）映射到Analytics变量（步骤2）时需要此步骤。 有关创建处理规则的更多信息，请参阅 [处理规则概述](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

在此示例中，已创建处理规则来映射上下文数据值 **[!UICONTROL poi.name]** 到 **[!UICONTROL 地标POI名称(eVar2)]**. 需要为创建的每个位置变量创建其他处理规则。

![&quot;创建处理规则&quot;](/help/assets/aa-processing-rule.png)

## 4.在工作区中生成报表

此步骤显示Analytics Workspace中的基本报表，用于查看在第1-3步中收集的数据。 有关如何使用Analytics Workspace的更多信息，请参阅 [Analytics工作区概述](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html).

在此示例中，报表具有以下设置：

* 量度 —  **[!UICONTROL 发生次数]**

* Dimension- **[!UICONTROL 操作名称]**

   * 按Dimension细分 —  **[!UICONTROL 地标POI名称]**

![&quot;在工作区中创建报告&quot;](/help/assets/aa-workspace.png)
