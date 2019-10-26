---
title: Adobe I/O集成概述
seo-title: Adobe I/O集成概述
description: 有关创建Adobe I/O集成的信息。
seo-description: 有关创建Adobe I/O集成的信息。
translation-type: tm+mt
source-git-commit: 3a9653dcc7f5d18b717c4bb59424b8cad7104dd7

---


# Adobe I/O集成 {#adobeio-integration}

此信息会向您展示如何创建Adobe I/O和Places集成。

## 用户访问的先决条件

向贵组织的系统管理员确认以下任务已完成：

* “放置核心服务”会显示在您组织的管理控制台中。
* 您已添加到组织。
* 您已作为用户添加到组织中放置核心服务。

   有关详细信息，请参 *阅常见问题解答中的将用户或开发人员添加到您的位置服务和Experience Platform Launch配置文件*[中](/help/places-faqs.md)。

* 您已作为开发人员添加到您组织中的Places Core Service。

   有关添加开发人员的详细信息，请参 *阅常见问题解答中的将用户或开发人员添加到您的位置服务和Experience Platform Launch配置文件*[中](/help/places-faqs.md)。

   有关开发人员角色的详细信息，请参阅管 [理开发人员](https://helpx.adobe.com/enterprise/using/manage-developers.html)。

### REST API请求

对Places REST API的每个请求都需要以下项：

* 组织ID
* API密钥
* 承载令牌

与Adobe I/O的集成提供了这些项，以及使用JSON web令牌(JWT)请求承载令牌的方法。

* 有关JWT的详细信息，请参 [阅JSON web令牌简介](https://jwt.io/introduction/)。
* 要为Places创建集成，请参阅下 *面的创建Places集成* 部分。
* 要了解API密钥集成、生成JWT和公钥证书，请参阅 [Adobe I/O身份验证概述](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)。

>[!IMPORTANT]
>
>如果您无法登录到Adobe I/O控制台，或者如果“创建集成”页面上不提供Experience Platform Location Service *，请参阅* Web服务API概述中的组织要求 **[](/help/web-service-api/places-web-services.md)。

## 创建Places集成

要创建地点集成，请完成以下任务：

### 生成公钥和私钥对

要创建Places集成，您需要一个公共密钥对和一个私钥对。 可以购买这些对，也可以生成您自己的自签名密钥。

要生成您自己的自签名密钥，请执行以下操作：

1. 在终端窗口中，复制并粘贴以下每行，然后在粘贴每 **[!UICONTROL Enter]** 行后按：

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >我们建议您命名密钥以便于参考，并将其存储在文件夹中。 如果您创建多个集成，则可以轻松识别和管理属于哪个集成的密钥。

2. 键入OpenSSL请求的信息：

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

3. 导览至文件和文 `.key` 件所 `.crt` 在的目录。

   例如，在iOS中，转到 **[!UICONTROL Macintosh HD]** &gt; **[!UICONTROL users]** &gt; **[!UICONTROL (your user name)]** &gt; **[!UICONTROL Keys]**。

以下视频将指导您完成生成键对的过程：

![集成视频](/help/assets/places_integration_video.gif)

### 在Adobe I/O控制台中创建地点集成

要创建Places集成，请执行以下操作：

1. 转到 [https://console.adobe.io](https://console.adobe.io) ，然后使用您的Adobe ID登录。
2. 如果您有权访问多个Experience cloud组织，请从左侧的下拉列表中选择该组织。
3. 单击 **[!UICONTROL New Integration]**。
4. 选择 **[!UICONTROL Access an API]** 并单击 **[!UICONTROL Continue]**。
5. 在下 **[!UICONTROL Experience Cloud]**&#x200B;面，选 **[!UICONTROL Places]** 择要集成到的Adobe服务，然后单击 **[!UICONTROL Continue]**。
6. 选择 **[!UICONTROL New integration]** 并单击 **[!UICONTROL Continue]**。
7. 在创建 *新集成屏幕中* ，输入名称和说明。
8. 将您在上面创 `xxxx_public.crt` 建的文件拖放到放置 **[!UICONTROL Public keys certificates]** 区域。
9. At the bottom of the page, click **[!UICONTROL Create integration]**.
10. 几秒钟后，在“集成已创 *建”屏幕中* ，确认显示以下消息：

   `Your integration has been created.`

11. 单击 **[!UICONTROL Continue to integration details]**。

   此时将显示您与API密钥、组织ID、技术帐户ID集成的概述，以及有关集成的其他详细信息。

### 记录组织ID和API密钥

1. 在选项卡 **[!UICONTROL Services]** 上，确认显 **[!UICONTROL Places]** 示该选项卡。
2. 在选 **[!UICONTROL Overview]** 项卡上，找到并记录API密钥（客户端ID）和组织ID。

   每个Places REST API请求都需要这些ID。

![](/help/assets/places_orgid_api-key.png)

### 生成JWT令牌

在选 **[!UICONTROL JWT]** 项卡上，Adobe I/O控制台允许您通过生成JWT并提供交换URL来测试集成。

要生成JWT令牌，请执行以下操作：

1. 在文本编辑器中，打开您 `private.key` 在上面创建的文件。
2. 在选 **[!UICONTROL JWT]** 项卡上，复制密钥的内容并将其粘贴到字 **[!UICONTROL Paste private key]** 段中。
3. 单击 **[!UICONTROL Generate JWT]**。
4. 在部分 **[!UICONTROL Sample CURL command]** 中，单击并 **[!UICONTROL Copy]** 将内容粘贴到命令提示符或终端窗口中。
5. 通过按键盘运 **[!UICONTROL Enter]** 行命令。
6. 找到 `"token_type": "bearer"` 和 `"access_token"` 值。

   承载访问令牌的值是您将在Places API请求中使用的值。

>[!IMPORTANT]
>
>Adobe访问令牌的有 **效期仅为** 24小时，因此请保存示例CURL命令（第5步）。 如果访问令牌不再有效，您需要再次生成该令牌。