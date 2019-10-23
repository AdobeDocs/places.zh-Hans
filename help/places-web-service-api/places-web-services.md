---
title: '放置Web服务概述 '
seo-title: '放置Web服务概述 '
description: Places是一套服务，使Adobe客户能更轻松地在正确的时间和地点将Adobe Experience cloud和Adobe Experience Platform解决方案与位置数据以及恰当的体验结合在一起。
seo-description: Places是一套服务，使Adobe客户能更轻松地在正确的时间和地点将Adobe Experience cloud和Adobe Experience Platform解决方案与位置数据以及恰当的体验结合在一起。
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# 放置Web服务概述 {#places-web-services-api}

Places是一套服务，使Adobe客户能更轻松地在正确的时间和地点将Adobe Cloud Platform和Adobe Experience platform解决方案与位置数据以及恰当的体验结合在一起。

“地点”允许您执行以下操作：

* 管理地理围栏
* 即使应用程序处于后台，也可以衡量用户的位置
* 在重要时实时使用数据

本节提供有关如何使用REST API和Places数据库的信息，Places数据库包含贵组织的POI数据。

## Places REST API

Places REST API允许您以编程方式使用单位的POI。 这些API允许您创建、更新和删除库以及这些库中的POI。 这些API使用JavaScript对象表示法(JSON)标准来格式化发送和接收的数据。 JSON的主要优点是它使开发人员和计算机能够轻松编写、读取和解析API查询。

在使用Places API之前，请确保满足以下要求：

* 您的组织中设置了地点，并且您以用户身份拥有相应的访问权限。

   For more information, see the *Organization requirements* section below.

* 在您的组织中设置Places后，您便有权访问，为Places创建Adobe集成。

   有关详细信息，请参 *阅在* Adobe I/O集成概述中创建Places集成 [](/help/places-web-service-api/adobe-i-o-integration.md)。

附加信息：

* 有关可用API以及如何使用这些API的详细信息，请参阅 [管理库](/help/places-web-service-api/api-usage/manage-libraries/manage-libraries.md) 和 [管理POI](/help/places-web-service-api/api-usage/manage-pois/manage-pois.md)。
* 有关这些API中的标题和参数的详细信息，请参阅 [标题和参数](/help/places-web-service-api/api-usage/headers-and-parameters.md)。

## 组织要求 {#org-requirements}

要访问Places REST API，请向系统管理员确认以下任务已完成：

* 地点已设置好，并显示在组织中。
* 您已添加到组织。
* 您已添加到组织中的地点。

   有关详细信息，请参 *阅将用户添加到Places和Experience Platform Launch* 中 [的常见问题解答](/help/places-faqs.md)。

* 您已作为地点开发人员添加到您的组织。

   有关开发人员角色的详细信息，请参阅管 [理开发人员](https://helpx.adobe.com/enterprise/using/manage-developers.html)。