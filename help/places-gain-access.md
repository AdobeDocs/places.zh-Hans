---
title: '访问Places Service '
description: 本节提供有关如何将用户添加到Places Service和Experience Platform Launch，以便用户能够访问Places Service的信息。
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 9%

---

# 获取对Places Service {#adding-user-launch-places}的访问权

您可以从[Adobe Experience Cloud主页](https://experience.adobe.com)上的“快速访问”菜单访问Places Service。
如果您的用户ID具有访问权限，您将看到Places Service图标，如下所示：

![快速访问菜单](/help/assets/quickaccess.png)

您还可以从Adobe Experience Platform菜单访问Places Service:

![Experience Platform菜单](/help/assets/solutionaccessmenu.png)

如果您在其中任一菜单中都未看到“放置服务”，请与贵组织的管理员联系，以将您的用户ID添加到Admin Console中的“放置核心服务”。

## 将用户添加到Places Service和Experience Platform Launch

要允许用户访问[Experience Platform LaunchUI](https://launch.adobe.com)，需要将用户添加到Admin Console中的Places Core Service。 要允许用户访问Experience Platform Launch、配置移动属性和使用Adobe Experience Platform SDK中的Places，需要将他们添加到Admin Console中的Experience Platform Launch并授予以下Experience Platform Launch权限：

* 所有产权：
   * 开发
   * 批准
   * 发布
   * 管理扩展
   * 管理环境
* 管理公司权限下的属性权限

如果这是您第一次添加用户，请完成以下步骤，将用户添加到Experience Platform Launch和Places Service。 如果您之前已经添加了用户，则可能会显示多个用户档案，因此请确保您选择了正确的用户档案。

>[!IMPORTANT]
>
>只有组织管理员才能访问Admin Console并添加用户。

### 1.验证是否已设置Places Service和Experience Platform Launch

1. 登录到您的Experience Cloud组织。
1. 在右上角，单击Experience Cloud外壳切换器。

   ![外壳切换器](/help/assets/places_shell_switcher1.png)

1. 在&#x200B;**[!UICONTROL 平台]**&#x200B;下，单击&#x200B;**[!UICONTROL 管理]**。

   如果列表中未显示&#x200B;**[!UICONTROL 管理]**，则您不是管理员。 您必须与组织管理员联系以完成此过程。

1. 在“Experience Cloud管理”页面的&#x200B;**[!UICONTROL Admin Console]**&#x200B;卡上，单击&#x200B;**[!UICONTROL 将我带到]**。

1. 在此Admin Console中，如果您有权访问多个组织，请验证在页面右上方选择了正确的组织。

   这是要将用户添加到的组织。 如果尚未选择正确的组织，请单击该组织，然后从下拉列表中选择该组织。

   >[!IMPORTANT]
   >
   >如果您无权访问某个组织，则表示您无权访问该组织。

1. 验证是否显示 **[!UICONTROL Adobe Experience Platform Launch]** 和 **[!UICONTROL Places 核心服务]**&#x200B;的信息卡。

   ![](/help/assets/places_provisioned1.png)

   如果显示了这些设置，则已为您的组织设置了“地点服务”和“Experience Platform Launch”。 如果未显示，则需要为您的组织设置它们。


### 2.设置用户档案并添加权限

1. 设置Experience Platform Launch用户档案，允许添加到用户档案的用户将Experience Platform Launch及其移动属性与Experience Platform SDK一起使用。

   a.在菜单栏中，单击&#x200B;**[!UICONTROL 产品]**。

   b.在左窗格的产品列表中，单击&#x200B;**[!UICONTROL Adobe Experience Platform Launch]**。

   * Experience Platform Launch用户档案显示在右侧。
   * Experience Platform Launch有一个默认用户档案，名为&#x200B;*Launch -(org name)*。

      如果您以前将用户添加到Experience Platform Launch，则可能会看到列出多个用户档案。

1. 选择正确的用户档案:

   a.单击默认用户档案的名称。

   b.单击&#x200B;**[!UICONTROL 权限]**&#x200B;选项卡。

   c. 单击&#x200B;**[!UICONTROL 属性权限]**&#x200B;旁边的&#x200B;**[!UICONTROL 编辑]**。

   d.在左窗格中，单击&#x200B;**[!UICONTROL +添加所有]**。

   此步骤会将所有可用权限移动到包含的权限列表。

   e.单击&#x200B;**[!UICONTROL 公司权限]**。

   f.在左窗格中，单击&#x200B;**[!UICONTROL +管理属性]**。

   g. 单击&#x200B;**[!UICONTROL 保存]**。

>[!IMPORTANT]
>
>对于Places Service，存在默认用户档案，但您不必添加任何权限。

您已成功将权限添加到您创建的用户档案。

### 3.将用户或开发人员添加到您的Places服务和Experience Platform Launch用户档案

您可以将用户和/或开发人员添加到您的Places服务和Experience Platform Launch用户档案。

### 添加用户

要将用户添加到您的Places服务和Experience Platform Launch用户档案:

1. 将用户添加到Experience Platform Launch用户档案。

   a.在菜单栏中，单击&#x200B;**[!UICONTROL 概述]**。

   b.在&#x200B;**[!UICONTROL Adobe Experience Platform Launch]**&#x200B;卡上，验证以下内容：

   * 卡底部显示两个点。
   * 左边的圆点是黑色。

      如果右侧的点为黑色，则只能添加开发人员。 要添加用户，请单击左侧的点。
   c.单击&#x200B;**[!UICONTROL +添加用户]**。

   d.输入用户的Adobe ID。

   e.完成以下步骤之一：

   * 如果要添加新用户，请单击&#x200B;**[!UICONTROL 新建用户]**，然后输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。

   f.在&#x200B;**[!UICONTROL 请为此产品]**&#x200B;下拉用户档案选择列表，选择您之前编辑的用户档案。

   g. 单击&#x200B;**[!UICONTROL 保存]**。

1. 将用户添加到&#x200B;**[!UICONTROL 放置核心服务]**。

   >[!TIP]
   >
   >目前，所有Places Service用户具有相同的权限，因此您无需编辑权限。

   a.在&#x200B;**[!UICONTROL 放置核心服务]**&#x200B;卡上，验证以下内容：

   * 卡底部显示两个点。
   * 左边的圆点是黑色。

   b.单击&#x200B;**[!UICONTROL + Assign Users]**。

   c.输入用户的Adobe ID。

   d.完成以下步骤之一：

   * 如果要添加新用户，请单击&#x200B;**[!UICONTROL 新建用户]**，然后输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。

   e.在&#x200B;**[!UICONTROL 请为此产品]**&#x200B;下拉列表选择用户档案，选择地点用户档案。

   f. 单击&#x200B;**[!UICONTROL 保存]**。

### 添加开发人员

对于还需要访问Web服务API的用户，您需要将他们添加为开发人员。

要添加开发人员，请执行以下操作：

1. 在 **[!UICONTROL Places 核心服务]**&#x200B;信息卡上，验证以下内容：

   * 卡底部显示两个点。
   * 单击右侧的圆点，这样卡的底部就会出现&#x200B;**[!UICONTROL “分配开发人员]**”。

1. 单击&#x200B;**[!UICONTROL + Assign Developers]**。

1. 输入用户的 Adobe ID。

1. 完成以下步骤之一：

   * 如果要添加新用户，请单击&#x200B;**[!UICONTROL 新建用户]**&#x200B;并输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。

1. 在&#x200B;**[!UICONTROL 请为此产品]**&#x200B;下拉用户档案选择列表，选择“Places Service”用户档案。

1. 单击&#x200B;**[!UICONTROL 保存]**。

用户收到一封电子邮件，通知他们有权访问 Experience Platform Launch。他们可以登录到此组织的[Experience Platform Launch](https://launch.adobe.com)或[放置服务](https://places.adobe.com) UI。 如果您完成了&#x200B;**[!UICONTROL 添加开发人员]**&#x200B;过程中的步骤 4，用户也可以登录 [Adobe I/O 控制台](https://console.adobe.io)以创建 Places 集成并使用 Places REST API。
