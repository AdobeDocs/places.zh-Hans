---
title: Web服务API概述
description: Places Service是一组服务，可让Adobe客户更轻松地在正确的时间和正确的地点向正确的人员水合Adobe Experience Cloud和Adobe Experience Platform解决方案中的位置数据和正确体验。
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
TQID: https://experienceleague.adobe.com/jP7iQH7X85UZROjsa3XzuN0bJZjjKffODFGGji7XZfQ
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 0%

---

# Web服务API概述 {#places-web-services-api}

Places Service是一组服务，可让Adobe客户更轻松地在正确的时间和正确的地点将Adobe Cloud Platform和Adobe Experience Platform解决方案与位置数据和正确体验水合到正确的人手中。

Web服务API允许您执行以下操作：

* 管理地理围栏
* 测量用户的位置，即使应用程序处于后台
* 在重要时实时使用数据

本节提供了有关如何使用REST API和POI数据库（包含组织的POI数据）的信息。

## REST API

Places服务REST API允许您以编程方式处理组织的POI。 这些API允许您创建、更新和删除库以及这些库中的POI。 这些API使用JavaScript对象表示法(JSON)标准来格式化发送和接收的数据。 JSON的主要优势是它使API查询易于开发人员和计算机写入、读取和分析。

在使用Web服务API之前，请确保已满足以下要求：

* Places服务在您的组织中配置，并且您作为用户具有适当的访问权限。

  有关详细信息，请参阅[集成概述和先决条件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*用户访问的先决条件*。

* 在您的组织中配置Places服务并且您具有访问权限后，为Places服务创建Adobe集成。

  有关详细信息，请参阅[集成概述和先决条件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*创建Places服务集成*。

其他信息：

* 有关可用API以及如何使用它们的详细信息，请参阅[管理库](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md)和[管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。
* 有关这些API中的标头和参数的更多信息，请参阅[标头和参数](/help/web-service-api/api-usage/headers-and-parameters.md)。
