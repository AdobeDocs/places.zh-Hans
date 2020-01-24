---
title: 'Web服务API概述 '
description: Places service是一套服务，使Adobe客户能够更轻松地在正确的时间和地点将Adobe Experience cloud和Adobe Experience Platform解决方案与位置数据和恰当的体验结合在一起。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Web服务API概述 {#places-web-services-api}

Places service是一套服务，使Adobe客户能够更轻松地在正确的时间和地点将Adobe Cloud Platform和Adobe Experience platform解决方案与位置数据和恰当的体验结合在一起。

Web服务API允许您执行以下操作：

* 管理地理围栏
* 即使应用程序处于后台，也可以衡量用户的位置
* 在重要时实时使用数据

本节提供有关如何使用REST API和POI数据库的信息，POI数据库包含贵组织的POI数据。

## REST API

Places Service REST API使您能以编程方式使用单位的POI。 这些API允许您创建、更新和删除库以及这些库中的POI。 这些API使用JavaScript对象表示法(JSON)标准来格式化发送和接收的数据。 JSON的主要优点是它使开发人员和计算机能够轻松编写、读取和解析API查询。

在使用Web服务API之前，请确保满足以下要求：

* 地点服务是在您的组织中提供的，并且您作为用户拥有相应的访问权限。

   有关详细信息，请参阅集 *成概述和先决条件中* ，用 [户访问的先决条件](/help/web-service-api/adobe-i-o-integration.md)。

* 在您的组织中设置Places服务后，并且您有权访问，请为Places服务创建Adobe集成。

   有关详细信息，请参 *阅“集成”概述和先决条件中的* “创 [建Places服务集成”](/help/web-service-api/adobe-i-o-integration.md)。

其他信息:

* 有关可用API以及如何使用这些API的详细信息，请参阅 [管理库](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) 和 [管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* 有关这些API中的标题和参数的详细信息，请参阅 [标题和参数](/help/web-service-api/api-usage/headers-and-parameters.md)。