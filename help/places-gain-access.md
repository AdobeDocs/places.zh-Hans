---
title: '获取对Places Service的访问权限 '
description: 本节提供有关如何将用户添加到Places服务和Experience Platform Launch的信息，以便用户能够访问Places服务。
translation-type: tm+mt
source-git-commit: 26538602a73e806a4822705c7a3aa44d76351030
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 7%

---

# 获取对Places Service的访问权限 {#adding-user-launch-places}

您可以从Adobe Experience Cloud家的快速访问菜单访问Places [服务](https://experience.adobe.com)。
如果您的用户ID具有访问权限，您将看到Places Service图标，如下所示：

![快速访问菜单](/help/assets/quickaccess.png)

您还可以从Adobe Experience Platform菜单访问Places Service:

![Experience Platform菜单](/help/assets/solutionaccessmenu.png)

如果您在其中任一菜单中都未看到“放置服务”，请联系您组织中的管理员，将您的用户ID添加到Admin Console中的“放置核心服务”。

## 将用户添加到Places服务和Experience Platform Launch

要允许用户访 [问Experience Platform LaunchUI](https://launch.adobe.com)，他们需要以用户身份添加到Admin Console中的Places Core Service。 要允许用户访问Experience Platform Launch、配置移动属性以及使用Adobe Experience PlatformSDK中的地点，需要将他们添加到Admin Console中的Experience Platform Launch并授予以下Experience Platform Launch权限：

* 所有产权：
   * 开发
   * 批准
   * 发布
   * 管理扩展
   * 管理环境
* 管理公司权限下的属性权限

如果这是您第一次添加用户，请完成以下步骤，将用户添加到Experience Platform Launch和位置服务。 如果您以前已经添加了用户，则可能会显示多个用户档案，因此请确保您选择了正确的用户档案。

>[!IMPORTANT]
>
>只有组织管理员才能访问Admin Console并添加用户。

### 1.验证是否已设置Places服务和Experience Platform Launch

1. 登录您的Experience Cloud组织。
1. 在右上角，单击Experience Cloud外壳切换器。

   ![外壳切换器](/help/assets/places_shell_switcher1.png)

1. 在 **[!UICONTROL Platform]** 下，单击 **[!UICONTROL Administration]**。

   如果列表中未 **显示** “管理”，则您不是管理员。 要完成此过程，必须与组织管理员联系。

1. 在“Experience Cloud管理”页面的卡片 **[!UICONTROL Admin Console]** 上，单击 **[!UICONTROL Take me there]**。

1. 在该Admin Console中，如果您有权访问多个组织，请验证在页面的右上方选择了正确的组织。

   这是您将向其添加用户的组织。 如果尚未选择正确的组织，请单击该组织，然后从下拉列表中选择该组织。

   >[!IMPORTANT]
   >
   >如果您无权访问某个组织，则表示您无权访问该组织。

1. 验证是否显示 **[!UICONTROL Adobe Experience Platform Launch]** 和 **[!UICONTROL Places Core Services]** 的卡。

   ![](/help/assets/places_provisioned1.png)

   如果显示了这些内容，则已为您的组织设置了地点服务和Experience Platform Launch。 如果未显示，则需要为您的组织设置这些设置。


### 2.设置用户档案并添加权限

1. 设置Experience Platform Launch用户档案，允许被添加到用户档案的用户将Experience Platform Launch及其移动属性与Experience PlatformSDK一起使用。

   a.在菜单栏中，单击 **[!UICONTROL Product]**。

   b.在左窗格的产品列表中，单击 **[!UICONTROL Adobe Experience Platform Launch]**。

   * Experience Platform Launch用户档案显示在右侧。
   * Experience Platform Launch有一个默认的用户档案, *称为启动项-（组织名称）* 。

      如果您以前将用户添加到Experience Platform Launch，您可能会看到列出多个用户档案。

1. 选择正确的用户档案:

   a.单击默认用户档案的名称。

   b. Click the **[!UICONTROL Permissions]** tab.

   c.单击 **[!UICONTROL Edit]** 旁 **[!UICONTROL Property Rights]**&#x200B;边。

   d.在左窗格中，单击 **[!UICONTROL + Add all]**。

   此步骤将所有可用权限移动到包含的权限列表。

   e.单击 **[!UICONTROL Company Rights]**。

   f.在左窗格中，单击 **[!UICONTROL + Manage Properties]**。

   g.单击 **[!UICONTROL Save]**。

>[!IMPORTANT]
>
>对于Places Service，存在默认用户档案，但您不必添加任何权限。

您已成功将权限添加到您创建的用户档案。

### 3.将用户或开发人员添加到您的Places服务和Experience Platform Launch用户档案

您可以将用户和／或开发人员添加到您的Places服务和Experience Platform Launch用户档案。

### 添加用户

将用户添加到您的Places服务和Experience Platform Launch用户档案:

1. 将用户添加到Experience Platform Launch用户档案。

   a.在菜单栏中，单击 **[!UICONTROL Overview]**。

   b.在卡 **[!UICONTROL Adobe Experience Platform Launch]** 上验证以下内容：

   * 卡底部显示两个点。
   * 左边的圆点是黑色。

      如果右侧的点为黑色，则只能添加开发人员。 要添加用户，请单击左侧的点。
   c.单击 **[!UICONTROL + Add Users]**。

   d.输入用户的Adobe ID。

   e.完成以下步骤之一：

   * 如果要添加新用户，请单 **[!UICONTROL New user]**&#x200B;击，然后输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。

   f.在下 **[!UICONTROL Please select a profile for this product]** 拉列表中，选择您之前编辑的用户档案。

   g.单击 **[!UICONTROL Save]**。

1. 将用户添加到 **[!UICONTROL Places Core Services]**。

   >[!TIP]
   >
   >当前，所有Places Service用户具有相同的权限，因此您无需编辑权限。

   a.在卡 **[!UICONTROL Places Core Services]** 上验证以下内容：

   * 卡底部显示两个点。
   * 左边的圆点是黑色。

   b.单击 **[!UICONTROL + Assign Users]**。

   c.输入用户的Adobe ID。

   d.完成以下步骤之一：

   * 如果要添加新用户，请单 **[!UICONTROL New user]**&#x200B;击，然后输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。

   e.在下 **[!UICONTROL Please select a profile for this product]** 拉列表中，选择“地点”用户档案。

   f.单击 **[!UICONTROL Save]**。

### 添加开发人员

对于还需要访问Web服务API的用户，您需要将其添加为开发人员。

要添加开发人员，请执行以下操作：

1. 在卡 **[!UICONTROL Places Core Services]** 上验证以下内容：

   * 卡底部显示两个点。
   * 单击右侧的点，以 **[!UICONTROL Assign Developers]** 便显示在卡的底部。

1. 单击 **[!UICONTROL + Assign Developers]**。

1. 输入用户的 Adobe ID。

1. 完成以下步骤之一：

   * 如果要添加新用户，请单 **[!UICONTROL New user]** 击并输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。

1. 在下 **[!UICONTROL Please select a profile for this product]** 拉列表中，选择“Places Service”用户档案。

1. 单击&#x200B;**保存**。

用户收到一封电子邮件，通知他们有权访问 Experience Platform Launch。They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. 如果您完成了&#x200B;**添加开发人员**&#x200B;过程中的步骤 4，用户也可以登录 [Adobe I/O 控制台](https://console.adobe.io)以创建 Places 集成并使用 Places REST API。
