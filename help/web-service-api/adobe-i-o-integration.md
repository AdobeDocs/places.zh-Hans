---
title: Adobe Developer项目概述
description: 有关创建Adobe Developer API项目的信息。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Places API访问概述和先决条件 {#developer-prereqs}

此信息向您展示了如何在Adobe Developer控制台中创建项目并生成要在Places API请求中使用的访问令牌。

## 用户访问的先决条件

向组织的系统管理员验证以下任务是否已完成：

* 您已被添加到组织。
* 您已被添加到Adobe Experience Platform中的配置文件。

  有关更多信息，请参阅 *将用户或开发人员添加到Places服务和Experience Platform Launch配置文件* 在 [获取对Places服务的访问权限](/help/places-gain-access.md).

### REST API请求

每个对Places服务REST API的请求都需要以下项：

* 组织ID
* API密钥（也称为客户端ID）
* 客户端密码
* 持有者令牌

具有的项目 [Adobe Developer控制台](https://developer.adobe.com/console) 提供了这些项目。

* 要为Places服务API创建项目，请参阅 *创建Places服务项目* 部分。

>[!IMPORTANT]
>
>如果您无法登录到 [Adobe Developer控制台](https://developer.adobe.com/console)，或者如果Places服务在 *创建集成页面*，请参见 *组织要求* 在 [Web服务API概述](/help/web-service-api/places-web-services.md).

## 创建Places服务API项目

要为Places服务API创建项目，请完成以下操作：

1. 登录 [Adobe Developer网站](https://developer.adobe.com) 使用您的Adobe ID。
2. 单击 **[!UICONTROL 控制台]** （在页面的右上角）。
3. 如果您被分配到多个Adobe组织，请从页面右上角的下拉列表中选择正确的组织。
4. 单击 **[!UICONTROL 创建新项目]** 按钮。
5. 单击 **[!UICONTROL 添加API]** 新项目快速入门部分中的按钮。
6. 要选择Places API，请向下滚动页面到Places卡，然后单击卡右上角的复选框。
7. 单击&#x200B;**[!UICONTROL 下一步]**&#x200B;按钮.
8. 选择OAuth服务器到服务器选项（如果有选项）。
9. 命名凭据，然后单击 **[!UICONTROL 下一个]**.
10. 选择用户档案（如果有多个用户档案，则任何用户档案都应该有效）。
11. 单击 **[!UICONTROL 保存和配置API]**.
12. 在左侧面板中，单击 **[!UICONTROL OAuth服务器到服务器]** 在凭据下链接
13. 本页提供以下内容：
   * 一种生成要在Places服务REST API请求中使用的访问令牌的方法。
   * 查看curl命令的示例，了解如何从自己的代码生成访问令牌。
   * 查看客户端ID（也称为API密钥）
   * 查看客户端密码
   * 查看组织ID
   * 在对Places服务REST API的请求中需要所有这些功能。
14. 您可以通过单击窗口左上角路径中的项目名称，将项目重命名为更具描述性的项目
15. 然后，单击 **[!UICONTROL 编辑项目]** 按钮进行标记。

>[!IMPORTANT]
>
>Adobe访问令牌有效 **仅限** 24小时，因此请保存示例CURL命令（步骤5）。 如果访问令牌不再有效，则必须重新生成该令牌。
