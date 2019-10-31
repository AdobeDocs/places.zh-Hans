---
title: 将地点数据发送到Adobe Analytics
seo-title: 将地点数据发送到Adobe Analytics
description: 本节提供有关如何将地点数据发送到Analytics的信息。
seo-description: '本节提供有关如何将地点数据发送到Analytics的信息。 '
translation-type: tm+mt
source-git-commit: 7ca51580a4cfa9c00431ad3972bd10e2a12dfbd1

---


# 将地点数据发送到Adobe Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>本节假定您已在应用程序中实施了地点。 有关实施Places的详细信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places发送进入和退出事件后，您可以在Experience Platform Launch中创建规则，将Places数据发送到Adobe Analytics。 要创建此类型的规则，请在启动项中选择您的属性，然后完成以下步骤：

## 1.创建规则

1. 在选项卡 **[!UICONTROL Rules]** 上，单击 **[!UICONTROL Create New Rule]**。

   请牢记以下信息：

   * 如果此属性没有现有规则，则 **[!UICONTROL Create New Rule]** 按钮将位于屏幕中间。
   * 如果您的属性有规则， **[!UICONTROL Create New Rule]** 则按钮将位于屏幕的右上方。

## 2.选择活动

1. 为规则键入有意义的名称。

   这样，规则在您的规则列表中就能很容易识别。 在此示例中，该规则被命名 **[!UICONTROL Send Data to Analytics]**。

2. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

3. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places]**。

4. 从下 **[!UICONTROL Event Type]** 拉列表中，选择 **[!UICONTROL Enter POI]**。

5. 单击 **[!UICONTROL Keep Changes]**。

   !["选择活动"](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.添加条件

>[!IMPORTANT]
>
>完成此步骤，将条件添加到规则。 否则，请跳到 *下面的定义操作* 。

在此示例中，创建了一个条件，该条件使规则仅在当前POI的名称等于时触发 **[!UICONTROL My POI]**。

1. 在部分 **[!UICONTROL Conditions]** 下，单击 **[!UICONTROL Add]**。

2. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places]**。

3. 从下 **[!UICONTROL Condition Type]** 拉列表中，选择 **[!UICONTROL Name]**。

4. 在右侧窗格的文本字段中，输入 **[!UICONTROL My POI]**。

5. 单击 **[!UICONTROL Keep Changes]**。

   !["设置条件"](/help/assets/ad-setCondition_use-analytics-data.png)


## 4.定义操作

1. 在部分 **[!UICONTROL Actions]** 下，单击 **[!UICONTROL Add]**。

2. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Adobe Analytics]**。

3. 从下 **[!UICONTROL Action Type]** 拉列表中，选择 **[!UICONTROL Track]**。

4. 在右侧窗格中，添加要发送到Analytics的操作或状态。

   您还可以选择向此请求添加任何其他上下文数据。 请记住，您可以使用数据元素从SDK动态获取此数据。

5. 单击 **[!UICONTROL Keep Changes]**。

   在以下示例中，将向 `TrackAction` Analytics发送一个调用，其中其他上下文数据与触发此条目事 `poi.name` 件的POI的名称相等：

   ![“设置操作”](/help/assets/ad-setAction_use-analytics-data.png)

## 5.保存规则并重新构建您的属性

完成配置后，请验证您的规则是否如下图所示：

![“规则已创建”](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 单击 **[!UICONTROL Save]**。

2. 重新构建您的启动项属性并将其部署到正确的环境。

