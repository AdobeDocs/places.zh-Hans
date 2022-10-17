---
title: 获取对Places Service的访问权限
description: 本节提供了有关如何将用户添加到Places Service和Experience Platform Launch，以便用户能够访问Places Service的信息。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# 获取对Places Service的访问权限 {#adding-user-launch-places}

Places Service现在在数据收集UI中可用。 您可以从 [Adobe Experience Cloud主页](https://experience.adobe.com).

![快速访问菜单](/help/assets/quickaccess.png)

您还可以从Adobe Experience Platform菜单访问数据收集：

![Experience Platform菜单](/help/assets/solutionaccessmenu.png)

如果您的用户ID具有访问权限，您将在数据收集中的数据管理下方的左侧面板中看到Places Service图标，如下所示：

![数据收集左面板](/help/assets/places_in_data_collection.png)

如果在此位置中未看到Places Service，请联系贵组织的管理员，以在Admin Console中将用户ID添加到Adobe Experience Platform。

## 添加用户以访问Places Service和Experience Adobe Experience Platform数据收集

位置现已包含在Adobe Experience Platform中。 允许用户访问 [Places Service](https://experience.adobe.com/#/data-collection/places)，则需要以用户身份添加到Admin Console的Adobe Experience Platform中。 要允许用户具有配置移动资产和在Adobe Experience Platform SDK中使用Places所需的权限来访问Experience Platform数据收集，还需将用户添加到Admin Console的Adobe Experience Platform数据收集中，并为用户授予Adobe Experience Platform数据收集的以下权限：

* 资产权限下的所有权限：
   * 批准
   * 开发
   * 编辑属性
   * 管理环境
   * 管理扩展
   * 发布
* 根据公司权限管理资产权限

如果您是首次添加用户，请完成以下步骤以将用户添加到Adobe Experience Platform数据收集和Adobe Experience Platform。 如果您之前已添加用户，则可能会显示多个用户档案，因此请确保选择正确的用户档案。

>[!IMPORTANT]
>
>只有组织管理员才能访问Admin Console和添加用户。

### 1.验证是否已配置Adobe Experience Platform和Adobe Experience Platform数据收集

1. 登录到您的Experience Cloud组织， [Adobe Experience Cloud主页](https://experience.adobe.com).
1. 单击右上方的Experience Cloud外壳切换器以显示下拉菜单。

   ![壳切换器](/help/assets/places_shell_switcher1.png)

1. 在列表底部，单击 **[!UICONTROL Admin Console]**. (指向 **[!UICONTROL Admin Console]** 也可在快速访问部分中找到)。

   如果您没有看到 **[!UICONTROL Admin Console]** 在列表中，您不是管理员。 要完成此过程，必须联系您的组织管理员。

1. 在Admin Console中，如果您有权访问多个组织，请确认在页面的右上角选择了正确的组织。

   这是要将用户添加到的组织。 如果未选择正确的组织，请单击组织，然后从下拉列表中选择正确的组织。

   >[!IMPORTANT]
   >
   >如果所需组织不在下拉列表中，则表示您没有该组织的管理员访问权限。

1. 在Admin Console中，单击产品选项卡，然后验证 **[!UICONTROL Adobe Experience Platform数据收集]** 和 **[!UICONTROL Adobe Experience Platform]** 中。

   ![](/help/assets/places_provisioned1.png)

   这2种产品会自动配置给所有组织，因此它们应当存在。


### 2.将用户添加到这些产品

#### 添加用户以提供对Places Service UI的访问

1. 在产品选项卡中，单击 **[!UICONTROL Adobe Experience Platform]** 卡。
2. 可以将用户添加到 **[!UICONTROL Adobe Experience Platform]** 要获取对Places的访问权限，无需设置任何特定权限。
3. 选择一个用户档案（如果有多个用户档案），然后单击该用户档案以将其打开。
4. 单击蓝色 **添加用户** 按钮，在用户中填写其AdobeID和名称，然后单击保存以完成添加。

#### 将用户添加到数据收集

1. 在产品选项卡中，单击 **[!UICONTROL Adobe Experience Platform数据收集]** 卡。
2. 默认情况下，名为 **默认数据收集全部访问** 将被创建。 向此配置文件添加用户将确保他们具有使用Places Service和数据收集的适当权限。 如果选择了其他用户档案，请确保包含上述权限。
3. 选择一个用户档案（如果有多个用户档案），然后单击该用户档案以将其打开。
4. 单击蓝色 **添加用户** 按钮，在用户中填写其AdobeID和名称，然后单击保存以完成添加。

#### 将用户添加为Places Service的开发人员。

对于还需要访问Places Service REST API的用户，您需要将他们添加为开发人员。
1. 在产品选项卡中，单击 **[!UICONTROL Adobe Experience Platform]** 卡。
2. 如果用户已添加到 **[!UICONTROL Adobe Experience Platform]** 按照上述说明进行信息卡，选择之前使用过的相同配置文件并单击它。
3. 在用户档案中，单击 **开发人员** 选项卡
4. 单击蓝色 **添加开发人员** 按钮，在用户中填写其AdobeID和名称，然后单击保存以完成添加。

完成上述步骤后，用户将收到一封电子邮件，通知他们有权访问 **[!UICONTROL Adobe Experience Platform]** 和 **[!UICONTROL Adobe Experience Platform数据收集]**. 然后，他们可以登录到 [Adobe Experience Cloud](https://experience.adobe.com) ，并访问Places Service和数据收集。 如果您还完成了这些步骤 **[!UICONTROL 添加开发人员]**，用户还可以登录到 [Adobe Developer控制台](https://developer.adobe.com/console/home) 创建项目，以便提供对Places Service REST API的访问权限。
