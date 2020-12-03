---
title: 定义数据元素
description: 本节提供有关如何在PlacesExperience Platform Launch中创建、使用和发布数据元素的信息。
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---


# Define a data element {#define-data-elements}

以下信息可帮助您了解数据元素以及如何创建和发布它们。

## 关于数据元素

数据元素是应用程序的数据字典的构件，用于跨营销和广告技术收集、组织和交付数据。

数据元素是一个变量，在该变量中，值可以映射到访客ID、运营商名称、广告ID、推送ID等。 在Experience Platform Launch中，您可以通过变量名称引用此值。 此事件元素集合成为可用于构建规则（、条件和操作）的已定义数据的字典，该字典在Experience Platform Launch之间共享，在该区域可以与属性中的任何扩展一起使用。

通过“地点”扩展，您可以引用以下目标中的值：

* 当前POI，指客户当前所在的POI。

   如果用户位于多个POI中，则选择属于级别较高的库的POI。 如果多个POI属于最高级库，则选取半径最小的库。
* 上次退出POI，指用户退出的最新POI。
* 上次输入的POI，指用户输入的最新POI。

每个POI都包含以下数据引用：

* **[!UICONTROL Category]**:POI类别
* **[!UICONTROL City]**:POI市
* **[!UICONTROL Country]**:POI国家／地区
* **[!UICONTROL Latitude]**:POI的纬度
* **[!UICONTROL Longitude]**:POI的经度
* **[!UICONTROL Metadata]**:POI的自定义元数据
* **[!UICONTROL Name]**:POI的名称
* **[!UICONTROL Radius]**:POI的radius
* **[!UICONTROL Region ID]**:POI的ID
* **[!UICONTROL Region/State]**:POI的地区、省或州

### 创建数据元素

1. 在应用程序的“属性”页中，单击选 **[!UICONTROL Data Elements]** 项卡。

1. 单击 **[!UICONTROL Create New Data Element]**。

1. 在已安装扩展的列表中，找到 **[!UICONTROL Places]**。

1. 在下 **[!UICONTROL Data Element Type]** 拉列表中，为此数据元素选择数据引用。

1. 选择POI目标。

1. 如果此数据元素是自定义元数据引用，请选择元数据键。

1. 键入数据元素的名称，然后单击 **[!UICONTROL Save]**。

   ![创建数据元素](/help/assets/create-de-7-v3.png)


## 使用数据元素

创建数据元素后，如果存在数据元素选取器，则可以使用任何规则组件中的数据元素。

![使用数据元素](/help/assets/use-de-v2.png)

如果规则组件中不存在数据元素选取器，则可以通过将数据元素名称打包为令牌来使用数据 **[!UICONTROL %%]** 元素。
例如，如果数据元素名称 **[!UICONTROL Last POI City]**&#x200B;为，则可以 **[!UICONTROL LAST POI City]** 添加到文本输入。


## 发布数据元素

如果在任何规则组件中使用数据元素，则这些数据元素还必须包含在库中并发布。
