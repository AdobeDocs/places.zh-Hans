---
title: 获取对Places服务的访问权限
description: 此部分提供有关如何向Places服务和Experience Platform Launch添加用户，以便用户能够访问Places服务的信息。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 1%

---

# 获取对Places服务的访问权限 {#adding-user-launch-places}

Places服务现在可在数据收集UI中使用。 您可以从上的快速访问菜单访问数据收集 [Adobe Experience Cloud主页](https://experience.adobe.com).

![快速访问菜单](/help/assets/quickaccess.png)

您还可以从Adobe Experience Platform菜单访问数据收集：

![Experience Platform菜单](/help/assets/solutionaccessmenu.png)

如果您的用户ID具有访问权限，您将在数据收集中的数据管理下方的左侧面板中看到Places服务图标，如下所示：

![“数据收集”左侧面板](/help/assets/places_in_data_collection.png)

如果您未在此位置看到Places服务，请联系您组织中的管理员，以将您的用户ID添加到Admin Console中的Adobe Experience Platform。

## 添加用户以访问Places服务和Experience Adobe Experience Platform数据收集

Places现已包含在Adobe Experience Platform中。 允许用户访问 [Places Service](https://experience.adobe.com/#/data-collection/places)，则需要将它们作为用户添加到Admin Console中的Adobe Experience Platform。 要允许用户通过配置移动Experience Platform所需的权限以及通过Adobe Experience Platform SDK使用Places来访问资产数据收集，还需将他们添加到Admin Console中的Adobe Experience Platform数据收集，并为其授予Adobe Experience Platform数据收集的以下权限：

* “资产权限”下的所有权限：
   * 批准
   * 开发
   * 编辑属性
   * 管理环境
   * 管理扩展
   * 发布
* “公司权限”下的“管理资产”权限

如果这是您首次添加用户，请完成以下步骤以将用户添加到Adobe Experience Platform数据收集和Adobe Experience Platform。 如果您以前添加过用户，则可能会显示多个配置文件，因此请确保您选择了正确的配置文件。

>[!IMPORTANT]
>
>只有组织管理员可以访问该Admin Console并添加用户。

### 1.验证是否已配置Adobe Experience Platform和Adobe Experience Platform数据收集

1. 登录到您的Experience Cloud组织， [Adobe Experience Cloud主页](https://experience.adobe.com).
1. 单击右上角的Experience Cloud外壳切换器以显示下拉菜单。

   ![壳层切换器](/help/assets/places_shell_switcher1.png)

1. 在列表底部，单击 **[!UICONTROL Admin Console]**. (指向以下内容的链接： **[!UICONTROL Admin Console]** 也可在快速访问部分找到)。

   如果您没有看到 **[!UICONTROL Admin Console]** 在列表中，您不是管理员。 必须联系组织管理员才能完成此过程。

1. 在Admin Console中，如果您有权访问多个组织，请确认在页面的右上角选择了正确的组织。

   这是您将向其添加用户的组织。 如果未选择正确的组织，请单击该组织，然后从下拉列表中选择正确的组织。

   >[!IMPORTANT]
   >
   >如果所需的组织不在下拉列表中，则意味着您无权访问该组织。

1. 在Admin Console中，单击Products选项卡，并验证卡是否用于 **[!UICONTROL Adobe Experience Platform数据收集]** 和 **[!UICONTROL Adobe Experience Platform]** 将显示。

   ![](/help/assets/places_provisioned1.png)

   这2个产品会自动配置到所有组织，因此它们应该存在。


### 2.将用户添加到这些产品

#### 添加用户以提供对Places服务UI的访问权限

1. 在“产品”选项卡中，单击 **[!UICONTROL Adobe Experience Platform]** 信息卡。
2. 可以将用户添加到中的任意配置文件 **[!UICONTROL Adobe Experience Platform]** 要访问Places，无需设置任何特定权限。
3. 选择一个配置文件（如果有多个配置文件），然后单击该配置文件以将其打开。
4. 单击蓝色 **添加用户** 按钮，使用用户的AdobeID和名称填写用户，然后单击保存以完成添加。

#### 将用户添加到数据收集

1. 在“产品”选项卡中，单击 **[!UICONTROL Adobe Experience Platform数据收集]** 信息卡。
2. 默认情况下，名为的配置文件 **默认数据收集所有访问** 将已创建。 将用户添加到此配置文件将确保他们拥有适当的权限来使用Places服务和数据收集。 如果选择其他配置文件，请确保包含上述权限。
3. 选择一个配置文件（如果有多个配置文件），然后单击该配置文件以将其打开。
4. 单击蓝色 **添加用户** 按钮，使用用户的AdobeID和名称填写用户，然后单击保存以完成添加。

#### 将用户添加为Places Service的开发人员。

对于还需要访问Places Service REST API的用户，您需要将他们添加为开发人员。
1. 在“产品”选项卡中，单击 **[!UICONTROL Adobe Experience Platform]** 信息卡。
2. 如果用户已添加到 **[!UICONTROL Adobe Experience Platform]** 按照上面的说明，选择以前使用的同一配置文件并单击它。
3. 在配置文件中，单击 **开发人员** 选项卡
4. 单击蓝色 **添加开发人员** 按钮，使用用户的AdobeID和名称填写用户，然后单击保存以完成添加。

完成上述步骤后，用户将收到一封电子邮件，通知他们有权访问 **[!UICONTROL Adobe Experience Platform]** 和 **[!UICONTROL Adobe Experience Platform数据收集]**. 然后，他们可以登录到 [Adobe Experience Cloud](https://experience.adobe.com) 用于此组织并访问Places服务和数据收集。 如果您还完成了这些步骤 **[!UICONTROL 添加开发人员]**，用户也可以登录到 [Adobe Developer控制台](https://developer.adobe.com/console/home) 创建一个项目，以提供对Places服务REST API的访问权限。
