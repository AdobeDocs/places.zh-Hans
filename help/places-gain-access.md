---
title: 获取对Places服务的访问权限
description: 此部分提供有关如何向Places服务和Experience Platform Launch添加用户，以便用户能够访问Places服务的信息。
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# 获取对Places服务的访问权限 {#adding-user-launch-places}

Places服务现在可在数据收集UI中使用。 您可以通过[Adobe Experience Cloud主页](https://experience.adobe.com)上的快速访问菜单访问数据收集。

![快速访问菜单](/help/assets/quickaccess.png)

您还可以从Adobe Experience Platform菜单访问数据收集：

![Experience Platform菜单](/help/assets/solutionaccessmenu.png)

如果您的用户ID具有访问权限，您将在数据收集中的数据管理下方的左侧面板中看到Places服务图标，如下所示：

![数据收集左侧面板](/help/assets/places_in_data_collection.png)

如果您未在此位置看到Places服务，请联系您组织中的管理员，以在Admin Console中将您的用户ID添加到Adobe Experience Platform。

## 添加用户以访问Places服务和Experience Adobe Experience Platform数据收集

Places现已包含在Adobe Experience Platform中。 要允许用户访问[Places服务](https://experience.adobe.com/#/data-collection/places)，需要将这些用户作为用户添加到Admin Console中的Adobe Experience Platform。 要允许用户通过配置移动资产所需的权限来访问Experience Platform数据收集，并将地标与Adobe Experience Platform SDK结合使用，还需将他们添加到Admin Console中的Adobe Experience Platform数据收集，并为其授予Adobe Experience Platform数据收集的以下权限：

* “资产权限”下的所有权限：
   * 审批
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

1. 登录到您的Experience Cloud组织[Adobe Experience Cloud主页](https://experience.adobe.com)。
1. 单击右上角的Experience Cloud外壳切换器以显示下拉菜单。

   ![外壳切换器](/help/assets/places_shell_switcher1.png)

1. 单击列表底部的&#x200B;**[!UICONTROL Admin Console]**。 (也可以在“快速访问”部分中找到指向&#x200B;**[!UICONTROL Admin Console]**&#x200B;的链接)。

   如果您未在列表中看到&#x200B;**[!UICONTROL Admin Console]**，则表明您不是管理员。 必须联系组织管理员才能完成此过程。

1. 在Admin Console中，如果您有权访问多个组织，请验证是否在该页的右上角选择了正确的组织。

   这是要将用户添加到其中的组织。 如果未选择正确的组织，请单击该组织，然后从下拉列表中选择正确的组织。

   >[!IMPORTANT]
   >
   >如果所需的组织不在下拉列表中，则意味着您不具有该组织的管理员访问权限。

1. 在Admin Console中，单击“产品”选项卡，然后验证是否显示&#x200B;**[!UICONTROL Adobe Experience Platform数据收集]**&#x200B;和&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;的卡片。

   ![](/help/assets/places_provisioned1.png)

   这2个产品会自动配置给所有组织，因此它们应该都会存在。


### 2.将用户添加到这些产品

#### 添加用户以提供对Places服务UI的访问权限

1. 在“产品”选项卡中，单击&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;卡。
2. 可以将用户添加到&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;内的任何配置文件中，以获得对地标的访问权限，无需设置特定权限。
3. 选择一个配置文件（如果有多个配置文件），然后单击该配置文件以将其打开。
4. 单击蓝色的&#x200B;**添加用户**&#x200B;按钮，在该用户中填写其AdobeID和名称，然后单击“保存”以完成添加。

#### 将用户添加到数据收集

1. 在“产品”选项卡中，单击&#x200B;**[!UICONTROL Adobe Experience Platform数据收集]**&#x200B;卡。
2. 默认情况下，将创建名为&#x200B;**默认数据收集所有访问**&#x200B;的配置文件。 将用户添加到此配置文件将确保他们具有使用Places服务和数据收集的适当权限。 如果选择其他配置文件，请确保包含上述权限。
3. 选择一个配置文件（如果有多个配置文件），然后单击该配置文件以将其打开。
4. 单击蓝色的&#x200B;**添加用户**&#x200B;按钮，在该用户中填写其AdobeID和名称，然后单击“保存”以完成添加。

#### 将用户添加为Places服务的开发人员。

对于还需要访问Places服务REST API的用户，您需要将他们添加为开发人员。
1. 在“产品”选项卡中，单击&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;卡。
2. 如果已通过上述说明将该用户添加到&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;卡，请选择以前使用的相同配置文件，然后单击该配置文件。
3. 在配置文件中，单击&#x200B;**开发人员**&#x200B;选项卡
4. 单击蓝色的&#x200B;**添加开发人员**&#x200B;按钮，将用户的AdobeID和名称填写到该用户，然后单击“保存”以完成添加。

完成上述步骤后，用户将收到一封电子邮件，通知他们有权访问&#x200B;**[!UICONTROL Adobe Experience Platform]**&#x200B;和&#x200B;**[!UICONTROL Adobe Experience Platform数据收集]**。 然后，他们可以登录到该组织的[Adobe Experience Cloud](https://experience.adobe.com)并访问Places服务和数据收集。 如果您还完成了步骤&#x200B;**[!UICONTROL 添加开发人员]**，用户也可以登录[Adobe Developer Console](https://developer.adobe.com/console/home)以创建将提供对Places服务REST API的访问权限的项目。
