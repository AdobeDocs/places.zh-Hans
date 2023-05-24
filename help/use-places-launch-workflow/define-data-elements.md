---
title: 定义数据元素
description: 本节提供了有关如何在Experience Platform Launch中为Places创建、使用和发布数据元素的信息。
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---

# 定义数据元素 {#define-data-elements}

以下信息可帮助您了解数据元素以及如何创建和发布它们。

## 关于数据元素

数据元素是应用程序数据字典的构建块，用于跨营销和广告技术收集、组织和交付数据。

数据元素是一个变量，其值可以映射到访客ID、运营商名称、广告ID、推送ID等。 在Experience Platform Launch中，您可以通过其变量名称引用此值。 此数据元素集合将成为可用于构建规则（事件、条件和操作）的已定义数据的字典，并且此字典可在各Experience Platform Launch之间共享，可与资产中的任何扩展一起使用。

使用Places扩展，您可以引用以下目标中的值：

* 当前POI，是指您的客户当前所在的POI。

   如果用户位于多个POI中，则选择属于具有较高排名的库的POI。 如果有多个POI属于最高级别的库，则选择半径最小的POI。
* 上次退出的POI，是指用户退出的最新POI。
* 上次输入的POI，是指用户输入的最新POI。

每个POI都包含以下数据引用：

* **[!UICONTROL 类别]**：POI的类别
* **[!UICONTROL 城市]**：目标点(POI)所在的城市
* **[!UICONTROL 国家/地区]**：目标点(POI)的国家/地区
* **[!UICONTROL 纬度]**：目标点的纬度
* **[!UICONTROL 经度]**：POI的经度
* **[!UICONTROL 元数据]**：POI的自定义元数据
* **[!UICONTROL 名称]**：POI的名称
* **[!UICONTROL 半径]**：POI的半径
* **[!UICONTROL 区域ID]**：POI的ID
* **[!UICONTROL 地区/州]**：目标点(POI)的区域、省或州

### 创建数据元素

1. 在应用程序的“属性”页面中，单击 **[!UICONTROL 数据元素]** 选项卡。

1. 单击&#x200B;**[!UICONTROL 创建新数据元素]**。

1. 在已安装的扩展列表中，查找 **[!UICONTROL Places]**.

1. 在 **[!UICONTROL 数据元素类型]** 从下拉列表中，为此数据元素选择数据引用。

1. 选择POI目标。

1. 如果此数据元素是自定义元数据引用，请选择一个元数据键。

1. 键入数据元素的名称，然后单击 **[!UICONTROL 保存]**.

   ![创建数据元素](/help/assets/create-de-7-v3.png)


## 使用数据元素

创建数据元素后，如果存在数据元素选取器，则可以使用任何规则组件中的数据元素。

![使用数据元素](/help/assets/use-de-v2.png)

如果规则组件中不存在数据元素选取器，则可以使用数据元素，方法是使用将数据元素名称换行 **[!UICONTROL %%]** 令牌。
例如，如果数据元素名称为 **[!UICONTROL 最后一个POI城市]**，您可以添加 **[!UICONTROL 最后一个POI城市]** 输入文本。


## 发布数据元素

如果数据元素用于任何规则组件中，则这些数据元素还必须包含在库中并发布。
