---
title: 将用户添加到地点和体验平台启动项
seo-title: 将用户添加到地点和体验平台启动项
description: '您需要将用户添加到Places Core Service，以便他们能够访问Places UI。 '
seo-description: '您需要将用户添加到Places Core Service，以便他们能够访问Places UI。 '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# 将用户添加到地点和体验平台启动项 {#adding-user-launch-places}

要允许用户访问 [启动服务UI](https://places.adobe.com)，他们需要以用户身份添加到管理控制台中的Places Core Service。 要允许用户访问Experience Platform Launch、配置移动属性以及使用Adobe Experience Platform SDK的地点，需要将他们添加到Admin Console中的Experience Platform Launch中，并为其授予以下Experience Platform Launch权限：

* 所有产权：
   * 开发
   * 批准
   * 发布
   * 管理扩展
   * 管理环境
* 根据公司权限管理属性权限

如果这是您第一次添加用户，请完成以下步骤以将用户添加到Experience Platform Launch and Places。 如果您之前已经添加了用户，则可能会显示多个配置文件，因此请确保您选择了正确的配置文件。

>[!IMPORTANT]
>
>只有组织管理员才能访问Admin Console并添加用户。

## 1.验证是否配置了Places和Experience Platform Launch

要验证是否配置了Places和Experience Platform Launch，请执行以下操作：

1. 登录您的Experience cloud组织。
1. 在右上方，单击Experience Cloud Shell切换程序。

   ![外壳切换器](/help/assets/places_shell_switcher1.png)

1. 在 **[!UICONTROL Platform]** 下，单击 **[!UICONTROL Administration]**。

   如果列表中未 **显示** “管理”，则您不是管理员。 要完成此过程，必须与组织管理员联系。

1. 在Experience cloud管理页面的卡片上，单 **[!UICONTROL Admin Console]** 击该页面 **[!UICONTROL Take me there]**。

1. 在管理控制台中，如果您有权访问多个组织，请确认在页面的右上方选择了正确的组织。

   这是您向其添加用户的组织。 如果尚未选择正确的组织，请单击该组织，然后从下拉列表中选择该组织。

   >[!IMPORTANT]
   >
   >如果您无权访问某个组织，则表示您无权访问该组织。

1. 验证显示的 **[!UICONTROL Adobe Experience Platform Launch]** 和 **[!UICONTROL Places Core Services]** 卡。

   ![](/help/assets/places_provisioned1.png)

   如果显示了这些设置，则表示您的组织已配置了地点和体验平台启动项。 如果未显示，则需要为您的组织配置这些组件。

   >[!IMPORTANT]
   >
   >在测试期间，完成测试版调 [查后](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)，将向供应团队发出请求。

## 2.设置配置文件并添加权限

要设置配置文件并添加权限，请执行以下操作：

1. 设置Experience Platform Launch配置文件，该配置文件允许已添加到该配置文件的用户将Experience Platform Launch及其移动属性与Experience Platform SDK一起使用。

   a.在菜单栏中，单击 **[!UICONTROL Product]**。

   b.在左窗格的产品列表中，单击 **[!UICONTROL Adobe Experience Platform Launch]**。

   * Experience Platform启动配置文件显示在右侧。
   * Experience Platform Launch有一个默认的配置文 *件，名为Launch -（组织名称）* 。

      如果您之前已将用户添加到Experience Platform Launch，则可能会看到列出多个配置文件。

2. 选择正确的配置文件：

   a.单击默认配置文件的名称。

   b.单击选 **[!UICONTROL Permissions]** 项卡。

   c.单击 **[!UICONTROL Edit]** 旁边的 **[!UICONTROL Property Rights]**。

   d.在左窗格中，单击 **[!UICONTROL + Add all]**。

   此步骤会将所有可用权限移动到包含的权限列表。

   e.单击 **[!UICONTROL Company Rights]**。

   f.在左窗格中，单击 **[!UICONTROL + Manage Properties]**。

   g.单击 **[!UICONTROL Save]**。

>[!IMPORTANT]
>
>对于“地点”，存在默认的配置文件，但您不必添加任何权限。

您已成功地将权限添加到您创建的配置文件。

## 3.将用户或开发人员添加到您的Places和Experience Platform Launch配置文件

您可以将用户和／或开发人员添加到您的Places和Experience Platform Launch配置文件。

## 添加用户

要将用户添加到您的地点和体验平台启动配置文件，请执行以下操作：

1. 将用户添加到Experience Platform启动配置文件。

   a.在菜单栏中，单击 **[!UICONTROL Overview]**。

   b.在卡 **[!UICONTROL Adobe Experience Platform Launch]** 上验证以下内容：

   * 卡的底部显示两个点。
   * 左边的圆点是黑色的。

      如果右侧的圆点为黑色，则只能添加开发人员。 要添加用户，请单击左侧的点。
   c.单击 **[!UICONTROL + Add Users]**。

   d.输入用户的Adobe ID。

   e.完成以下步骤之一：

   * 如果要添加新用户，请单 **[!UICONTROL New user]**&#x200B;击，然后输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。
   f.在下拉 **[!UICONTROL Please select a profile for this product]** 列表中，选择您之前编辑的配置文件。

   g.单击 **[!UICONTROL Save]**。

2. 将用户添加到 **[!UICONTROL Places Core Services]**。

   >[!TIP]
   >
   >目前，所有Places用户都具有相同的权限，因此您无需编辑权限。

   a.在卡 **[!UICONTROL Places Core Services]** 上验证以下内容：

   * 卡的底部显示两个点。
   * 左边的圆点是黑色的。
   b.单击 **[!UICONTROL + Assign Users]**。

   c.输入用户的Adobe ID。

   d.完成以下步骤之一：

   * 如果要添加新用户，请单 **[!UICONTROL New user]**&#x200B;击，然后输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。
   e.在下拉 **[!UICONTROL Please select a profile for this product]** 列表中，选择地点配置文件。

   f.单击 **[!UICONTROL Save]**。

## 添加开发人员

对于还需要访问Places REST API的用户，您需要将他们添加为开发人员。

要添加开发人员，请执行以下操作：

1. 在卡 **[!UICONTROL Places Core Services]** 上验证以下内容：

   * 卡的底部显示两个点。
   * 单击右侧的圆点，以 **[!UICONTROL Assign Developers]** 便显示在卡的底部。

1. 单击 **[!UICONTROL + Assign Developers]**。

1. 输入用户的Adobe ID。

1. 完成以下步骤之一：

   * 如果要添加新用户，请单 **[!UICONTROL New user]** 击并输入用户的名和姓。
   * 如果要添加现有用户，请单击显示的用户名。

1. 在下拉 **[!UICONTROL Please select a profile for this product]** 列表中，选择位置服务配置文件。

1. 单击&#x200B;**保存**。

用户会收到一封电子邮件，通知他们有权访问Experience Platform Launch。 他们可以登录到此组 [织的Experience Platform Launch](https://launch.adobe.com)[或Places](https://places.adobe.com) UI。 如果您完成了“添加开发人员 **”过程中的步骤4，则用户还可以登录到**[](https://console.adobe.io) Adobe I/O控制台，以创建Places集成并使用Places REST API。

