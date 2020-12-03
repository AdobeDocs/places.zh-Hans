---
title: Adobe I/O集成概述
description: 有关创建Adobe I/O集成的信息。
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---


# Integration overview and prerequisites {#integration-prereqs}

此信息向您展示如何创建Adobe I/O和Places Service集成。

## 用户访问的先决条件

向组织的系统管理员确认以下任务已完成：

* Places Core Service显示在组织的管理控制台中。
* 您已添加到组织。
* 您已作为用户添加到您的组织中放置核心服务。

   有关详细信息，请参 *阅获取对Places Service的访问权，将用户或开发* 人员添加到您的Places服务和Experience Platform Launch用户档案 [](/help/places-gain-access.md)中。

* 您已作为开发人员添加到您组织中的Places Core Service。

   有关添加开发人员的详细信 *息，请参阅获取对Places Service的访* 问中的将用户或开发人员添加到您的Places服务 [](/help/places-gain-access.md)和Experience Platform Launch用户档案中。

   有关开发人员角色的详细信息，请参 [阅管理开发人员](https://helpx.adobe.com/cn/enterprise/using/manage-developers.html)。

### REST API请求

对Places Service REST API的每个请求都需要以下项：

* 组织ID
* API密钥
* 承载令牌

与Adobe I/O的集成提供了这些项目，以及使用JSON Web令牌(JWT)请求承载令牌的方法。

* 有关JWT的详细信息，请参 [阅JSON Web令牌简介](https://jwt.io/introduction/)。
* 要创建Places Service的集成，请参阅下 *面的创建Places Service集成* 部分。
* 要了解API密钥集成、生成JWT和公钥证书，请参阅 [Adobe I/O身份验证概述](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)。

>[!IMPORTANT]
>
>如果无法登录到Adobe I/O控制台，或者如果“创建集成”页面上不提供“ *Places Service”选项*，请参 *阅Web服务API* 概述中的组织要求 [](/help/web-service-api/places-web-services.md)。

## 创建Places Service集成

要创建Places Service集成，请完成以下任务:

### 生成公钥对和私钥对

要创建Places Service集成，您需要一个公共密钥对和一个私钥对。 可以购买这些对，也可以生成您自己的自签名密钥。

要生成您自己的自签名密钥，请执行以下操作：

1. 在终端窗口中，复制并粘贴以下每一行，粘贴每 **[!UICONTROL Enter]** 行后按：

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >我们建议您命名密钥以便参考，并将它们存储在一个文件夹中。 如果您创建多个集成，则可以轻松识别和管理属于哪个集成的密钥。

1. 键入OpenSSL请求的信息：

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   有关OpenSSL的详细信息，请参 [阅OpenSSL](https://www.openssl.org/)。

   >[!IMPORTANT]
   >
   >您提供的信息会并入密钥中。

1. 导览至文件和文 `.key` 件所 `.crt` 在的目录。

   例如，在MacOS中，转到 **[!UICONTROL Macintosh HD]** > **[!UICONTROL users]** > **[!UICONTROL (your user name)]** > **[!UICONTROL Keys]**。

以下视频将指导您完成生成密钥对的过程：

![集成视频](/help/assets/places_integration_video.gif)

### 在Adobe I/O控制台中创建Places Service集成

要创建Places Service集成，请执行以下操作：

1. 转到 [https://console.adobe.io](https://console.adobe.io) ，然后与您的Adobe ID登录。
1. 在“快 **速开始** ”部分，单击 **创建集成**。
1. 选择 **[!UICONTROL Access an API]** 并单击 **[!UICONTROL Continue]**。

   **[!UICONTROL Access an API]** 是默认位置。

1. 如果您有权访问多个Experience Cloud组织，请从右上方的下拉列表中选择该组织。
1. Under **[!UICONTROL Experience Cloud]**, select **[!UICONTROL Places Service]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. 选择 **[!UICONTROL New integration]** 并单击 **[!UICONTROL Continue]**。
1. 在“创建新集成”屏幕上，输入名称和说明。
1. 将您在上面 `xxxx_public.crt` 创建的文件拖放到放置 **[!UICONTROL Public keys certificates]** 区域。
1. 选择产品用户档案。

   如果不确定要选择哪个用户档案，请与系统管理员联系。
1. 在页面底部，单击 **[!UICONTROL Create integration]**。
1. 几秒钟后，在“集成创建 *的”屏幕* ，验证是否显示以下消息：

   `Your integration has been created.`

1. 此时将显示集成详细信息页面，其顶部是集成的名称。

   该选 **[!UICONTROL Overview]** 项卡默认显示，并显示API密钥、组织ID、技术帐户ID以及有关集成的其他详细信息。

### 记录组织ID和API密钥

1. 在集成详细信息页面上，单 **[!UICONTROL Services]** 击选项卡并确认 **[!UICONTROL Places Service]** 显示在下 **[!UICONTROL Configured Services]**&#x200B;面。
1. 在选 **[!UICONTROL Overview]** 项卡上，找到并记录API密钥（客户端ID）和组织ID。

   每个Places Service REST API请求都需要这些ID。

![](/help/assets/places_orgid_api-key.png)

### 生成JWT令牌

在集成详细信息页面上，单 **[!UICONTROL JWT]** 击选项卡，以便通过生成JWT并提供exchange URL来测试集成。

要生成JWT令牌：

1. 在文本编辑器中，打开您 `private.key` 在上面创建的文件。
1. On the **[!UICONTROL JWT]** tab, copy the contents of the key and paste it in the **[!UICONTROL Paste private key]** field.
1. 单击 **[!UICONTROL Generate JWT]**。
1. In the **[!UICONTROL Sample CURL command]** section, click **[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. 通过按键盘运 **[!UICONTROL Enter]** 行命令。
1. 找到 `"token_type": "bearer"` 和 `"access_token"` 值。

   承载访问令牌的值是您将在Places Service API请求中使用的值。

>[!IMPORTANT]
>
>Adobe访问令牌 **的有效** 期仅为24小时，因此请保存示例CURL命令（步骤5）。 如果访问令牌不再有效，您需要重新生成令牌。