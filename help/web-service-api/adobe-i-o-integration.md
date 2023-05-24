---
title: Adobe I/O集成概述
description: 有关创建Adobe I/O集成的信息。
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---

# 集成概述和先决条件 {#integration-prereqs}

此信息向您说明如何创建Adobe I/O和Places Service集成。

## 用户访问的先决条件

与贵组织的系统管理员确认以下任务已完成：

* Places核心服务将显示在您组织的Admin Console中。
* 您已被添加到组织。
* 您已被添加为组织中的Places核心服务的用户。

   有关更多信息，请参阅 *将用户或开发人员添加到Places服务和Experience Platform Launch配置文件* 在 [获取对Places服务的访问权限](/help/places-gain-access.md).

* 您已被添加为组织中Places核心服务的开发人员。

   有关添加开发人员的详细信息，请参阅 *将用户或开发人员添加到Places服务和Experience Platform Launch配置文件* 在 [获取对Places服务的访问权限](/help/places-gain-access.md).

   有关开发人员角色的更多信息，请参阅 [管理开发人员](https://helpx.adobe.com/cn/enterprise/using/manage-developers.html).

### REST API请求

对Places服务REST API的每个请求都需要以下项：

* 组织ID
* API密钥
* 持有者令牌

与Adobe I/O的集成提供了这些项目，以及使用JSON Web令牌(JWT)请求持有者令牌的方法。

* 有关JWT的更多信息，请参阅 [JSON Web令牌简介](https://jwt.io/introduction/).
* 要为Places Service创建集成，请参阅 *创建Places服务集成* 部分。
* 要了解API密钥集成、生成JWT和公共密钥证书，请参阅 [Adobe I/O身份验证概述](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>如果您无法登录到Adobe I/O控制台，或者如果Places服务不是 *创建集成页面*，请参见 *组织要求* 在 [Web服务API概述](/help/web-service-api/places-web-services.md).

## 创建Places服务集成

要创建Places Service集成，请完成以下任务：

### 生成公钥和私钥对

要创建Places服务集成，您需要一个公钥和私钥对。 这些密钥对可以购买，也可以生成您自己的自签名密钥。

要生成您自己的自签名密钥，请执行以下操作：

1. 在终端窗口中，复制并粘贴以下各行，然后按键 **[!UICONTROL 输入]** 粘贴每行后：

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >我们建议您为密钥命名以便轻松引用，并将它们存储在文件夹中。 如果您创建多个集成，则可以轻松识别和管理哪些键属于哪个集成。

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

   有关OpenSSL的详细信息，请参见 [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >您提供的信息将合并到键中。

1. 导航到 `.key` 和 `.crt` 找到文件。

   例如，在MacOS中，转到 **[!UICONTROL Macintosh HD]** > **[!UICONTROL 用户]** > **[!UICONTROL （您的用户名）]** > **[!UICONTROL 键]**.

以下视频将指导您完成生成密钥对的过程：

![集成视频](/help/assets/places_integration_video.gif)

### 在Adobe I/O控制台中创建Places Service集成

要创建Places Service集成，请执行以下操作：

1. 转到 [https://console.adobe.io](https://console.adobe.io) 然后使用您的Adobe ID登录。
1. 在 **快速入门** 部分，单击 **创建集成**.
1. 选择 **[!UICONTROL 访问API]** 并单击 **[!UICONTROL 继续]**.

   **[!UICONTROL 访问API]** 是默认位置。

1. 如果您有权访问多个Experience Cloud组织，请从右上方的下拉列表中选择该组织。
1. 下 **[!UICONTROL Experience Cloud]**，选择 **[!UICONTROL Places Service]** 作为要集成到的Adobe服务，然后单击 **[!UICONTROL 继续]**.
1. 选择 **[!UICONTROL 新集成]** 并单击 **[!UICONTROL 继续]**.
1. 在创建新集成屏幕上，输入名称和描述。
1. 拖放 `xxxx_public.crt` 文件（您在上面创建的）到 **[!UICONTROL 公钥证书]** 放置区域。
1. 选择产品配置文件。

   如果不确定要选择哪个配置文件，请联系您的系统管理员。
1. 在页面底部，单击 **[!UICONTROL 创建集成]**.
1. 几秒钟后，在 *已创建集成* 屏幕，验证是否显示以下消息：

   `Your integration has been created.`

1. 此时将显示集成详细信息页面，集成名称位于顶部。

   此 **[!UICONTROL 概述]** 选项卡，其中默认显示API密钥、您的组织ID、技术帐户ID，以及有关您的集成的其他详细信息。

### 记录组织ID和API密钥

1. 在集成详细信息页面上，单击 **[!UICONTROL 服务]** 制表符并确认 **[!UICONTROL Places Service]** 显示于 **[!UICONTROL 已配置的服务]**.
1. 在 **[!UICONTROL 概述]** 选项卡，找到并记录API密钥（客户端ID）和组织ID。

   每个Places服务REST API请求都需要这些ID。

![](/help/assets/places_orgid_api-key.png)

### 生成JWT令牌

在集成详细信息页面上，单击 **[!UICONTROL JWT]** 选项卡，以便您可以通过生成JWT并提供Exchange URL来测试集成。

要生成JWT令牌：

1. 在文本编辑器中，打开 `private.key` 您在上面创建的文件。
1. 在 **[!UICONTROL JWT]** 选项卡上，复制密钥的内容并将其粘贴到&#x200B;**[!UICONTROL 粘贴私钥]**&#x200B;字段中。
1. 单击 **[!UICONTROL 生成JWT]**.
1. 在&#x200B;**[!UICONTROL 示例 CURL 命令]**&#x200B;部分中，单击&#x200B;**[!UICONTROL 复制]**&#x200B;并将内容粘贴到命令提示符或终端窗口中。
1. 通过按运行命令 **[!UICONTROL 输入]** 在键盘上。
1. 找到 `"token_type": "bearer"` 和 `"access_token"` 值。

   持有者访问令牌的值是您将在Places服务API请求中使用的值。

>[!IMPORTANT]
>
>Adobe访问令牌有效 **仅限** 保存24小时，然后保存示例CURL命令（步骤5）。 如果访问令牌不再有效，则需要重新生成令牌。
