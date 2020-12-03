---
title: 'Web服务API概述 '
description: Places Service是一套服务，使Adobe客户能更轻松地在正确的时间和地点将位置数据和适当的体验融入Adobe Experience Cloud和Adobe Experience Platform解决方案。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---


# Web服务API概述 {#places-web-services-api}

Places Service是一套服务，使Adobe客户能更轻松地在正确的时间和地点将位置数据和适当的体验融入Adobe Cloud Platform和Adobe Experience Platform解决方案。

Web服务API允许您执行以下操作：

* 管理地理围栏
* 即使应用程序处于后台，也可以衡量用户的位置
* 在重要时实时使用数据

本节提供有关如何使用REST API和POI数据库（包含组织的POI数据）的信息。

## REST API

Places Service REST API允许您以编程方式处理组织的POI。 这些API允许您创建、更新和删除库以及这些库中的POI。 这些API使用JavaScript对象表示法(JSON)标准来格式化发送和接收的数据。 JSON的主要优势在于它使开发人员和计算机能轻松编写、读取和分析API查询。

在使用Web服务API之前，请确保满足以下要求：

* 您的组织中设置了“地点服务”，您以用户身份拥有适当的访问权限。

   有关详细信息，请参 *阅集成概述和先决条件* ，以 [便用户访问](/help/web-service-api/adobe-i-o-integration.md)。

* 在您的组织中设置Places服务后，并且您具有访问权限，请为Places服务创建Adobe集成。

   有关详细信息，请参 *阅在集成概述和先决条件中*[创建Places Service集成](/help/web-service-api/adobe-i-o-integration.md)。

其他信息：

* 有关可用API及其使用方法的详细信息，请参阅 [管理库](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)[和管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* 有关这些API中的标题和参数的详细信息，请参 [阅标题和参数](/help/web-service-api/api-usage/headers-and-parameters.md)。