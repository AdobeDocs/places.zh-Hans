---
title: 定义数据元素
description: 本节提供了有关如何在Experience Platform Launch for Places中创建、使用和发布数据元素的信息。
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
TQID: https://experienceleague.adobe.com/NQ83uUZJtNglAcxD6HNl4Gw1Y8-0-uqfu-hH8H0EITg
product_v2:
  - id: a829a185-511f-4bf8-8dcf-9e684f8011cf
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 486
ht-degree: 1%

---

# 定义数据元素 {#define-data-elements}

以下信息可帮助您了解数据元素以及如何创建和发布它们。

## 关于数据元素

数据元素是应用程序数据字典的构建块，用于跨营销和广告技术收集、组织和交付数据。

数据元素是一个变量，其值可以映射到访客ID、运营商名称、Advertising ID、推送ID等。 在Experience Platform Launch中，您可以通过其变量名称引用此值。 此数据元素集合将成为可用于构建规则（事件、条件和操作）的已定义数据的字典，该字典将跨Experience Platform Launch共享，您可以在其中与资产中的任何扩展一起使用。

使用Places扩展，您可以引用以下目标中的值：

* 当前POI，是指您的客户当前所在的POI。

  如果用户位于多个POI中，则选择属于具有较高排名的库的POI。 如果有多个POI属于最高级别的库，则选择半径最小的POI。
* 上次退出的POI，是指用户退出的最新POI。
* 上次输入的POI，是指用户输入的最新POI。

每个POI都包含以下数据引用：

* **[!UICONTROL 类别]**：目标点类别
* **[!UICONTROL 城市]**： POI的城市
* **[!UICONTROL 国家/地区]**： POI的国家/地区
* **[!UICONTROL 纬度]**：目标点的纬度
* **[!UICONTROL 经度]**： POI的经度
* **[!UICONTROL 元数据]**： POI的自定义元数据
* **[!UICONTROL 名称]**： POI的名称
* **[!UICONTROL 半径]**： POI的半径
* **[!UICONTROL 区域ID]**： POI的ID
* **[!UICONTROL 地区/州]**： POI的地区、省或州

### 创建数据元素

1. 在应用程序的“属性”页面中，单击&#x200B;**[!UICONTROL 数据元素]**&#x200B;选项卡。

1. 单击&#x200B;**[!UICONTROL 创建新数据元素]**。

1. 在安装扩展的列表中，找到&#x200B;**[!UICONTROL Places]**。

1. 在&#x200B;**[!UICONTROL 数据元素类型]**&#x200B;下拉列表中，为此数据元素选择数据引用。

1. 选择POI目标。

1. 如果此数据元素是自定义元数据引用，请选择一个元数据键。

1. 键入数据元素的名称，然后单击&#x200B;**[!UICONTROL 保存]**。

   ![创建数据元素](/help/assets/create-de-7-v3.png)


## 使用数据元素

创建数据元素后，如果存在数据元素选取器，则可以使用任何规则组件中的数据元素。

![使用数据元素](/help/assets/use-de-v2.png)

如果规则组件中不存在数据元素选取器，则可以通过使用&#x200B;**[!UICONTROL %]**&#x200B;令牌封装数据元素名称来使用该数据元素。
例如，如果数据元素名称为&#x200B;**[!UICONTROL 最后一个POI城市]**，则可以将&#x200B;**[!UICONTROL 最后一个POI城市]**&#x200B;添加到文本输入中。


## 发布数据元素

如果有任何规则组件中使用数据元素，则这些数据元素还必须包含在库中并发布。
