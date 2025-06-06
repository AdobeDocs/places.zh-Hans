---
audience: end-user
user-guide-title: Places Service 指南
user-guide-description: Places Service 是一种地理位置服务，它使具有位置感知的移动设备应用程序能够了解位置上下文。
feature: Places
source-git-commit: 9f2c6fee6e0d6d075b662cc0b6cbee49cf05ee55
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 18%

---


# Places Service {#using}

+ [Places Service概述](home.md)
+ [发行说明](release-notes.md)
+ [快速入门](getting-started.md)
+ [获取对Places服务的访问权限](places-gain-access.md)
+ Places服务UI {#poi-mgmt-ui}
   + [Places服务UI概述](poi-mgmt-ui/poi-mgmt-ui-overview.md)
   + [创建POI](poi-mgmt-ui/create-a-poi-ui.md)
   + [管理以前创建的POI](poi-mgmt-ui/managing-pois-in-the-places-ui.md)
   + [将元数据与POI一起使用的策略](poi-mgmt-ui/metadata-with-pois.md)
   + [批量上传POI](poi-mgmt-ui/bulk-upload-pois.md)
   + [管理多个库](poi-mgmt-ui/manage-libraries-in-the-places-ui.md)
+ Web服务API {#web-service-api}
   + [Web服务API概述](web-service-api/places-web-services.md)
   + [集成先决条件](web-service-api/adobe-i-o-integration.md)
   + API使用情况{#api-usage}
      + [API使用情况概述](web-service-api/api-usage/api-usage-overview.md)
      + [标题和参数](web-service-api/api-usage/headers-and-parameters.md)
      + 管理库{#manage-libraries}
         + [管理库概述](web-service-api/api-usage/manage-libraries/manage-libraries.md)
         + [创建库](web-service-api/api-usage/manage-libraries/create-a-library.md)
         + [读取库](web-service-api/api-usage/manage-libraries/read-a-library.md)
         + [更新库](web-service-api/api-usage/manage-libraries/update-a-library.md)
         + [删除库](web-service-api/api-usage/manage-libraries/delete-a-library.md)
         + [读取组织中的所有库](web-service-api/api-usage/manage-libraries/read-all-libraries-in-your-organization.md)
         + [在库中设置排名](web-service-api/api-usage/manage-libraries/set-a-ran-on-your-libraries.md)
         + [获取库的排名](web-service-api/api-usage/manage-libraries/get-a-librarys-rank.md)
      + 管理目标点 {#manage-pois}
         + [管理POI概述](web-service-api/api-usage/manage-pois/manage-pois.md)
         + [创建POI](web-service-api/api-usage/manage-pois/create-a-poi.md)
         + [读取POI](web-service-api/api-usage/manage-pois/read-a-poi.md)
         + [更新POI](web-service-api/api-usage/manage-pois/update-a-poi.md)
         + [删除目标点(POI)](web-service-api/api-usage/manage-pois/delete-a-poi.md)
         + [读取库中的所有POI](web-service-api/api-usage/manage-pois/read-all-pois-in-a-library.md)
         + [读取您组织中的所有POI](web-service-api/api-usage/manage-pois/read-all-pois-in-your-organization.md)
         + 批次API {#batch-apis}
            + [批处理API概述](web-service-api/api-usage/manage-pois/batch-apis/batch-apis.md)
            + [创建多个POI](web-service-api/api-usage/manage-pois/batch-apis/create-multiple-pois.md)
            + [更新多个POI](web-service-api/api-usage/manage-pois/batch-apis/update-multiple-pois.md)
            + [删除多个POI](web-service-api/api-usage/manage-pois/batch-apis/delete-multiple-pois.md)
      + [查询API](web-service-api/api-usage/query-apis.md)
+ Mobile SDK的扩展{#places-ext-aep-sdks}
   + [Places扩展](places-ext-aep-sdks/places-extension/places-extension.md)
+ [将Places Service与您自己的监控解决方案结合使用](using-your-own-monitor.md)
+ [不使用活动区域监视的Places服务](use-places-without-active-monitoring.md)
+ 将Places服务用作Experience Platform Launch工作流的一部分{#use-places-launch-workflow}
   + [将Places服务用作Experience Platform Launch工作流的一部分](use-places-launch-workflow/places-launch-workflow.md)
   + [定义数据元素](use-places-launch-workflow/define-data-elements.md)
   + [创建登入和退出规则](use-places-launch-workflow/create-rule-places-property.md)
+ 将Places服务与其他Adobe解决方案一起使用{#use-places-with-other-solutions}
   + Adobe Analytics {#places-adobe-analytics}
      + [将Places服务与Adobe Analytics结合使用](use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)
      + [将POI登入和退出数据发送到Analytics](use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)
      + [将位置上下文添加到Analytics请求](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)
      + [在Analytics Workspace中报告位置数据](use-places-with-other-solutions/places-adobe-analytics/places-in-workspace.md)
   + Adobe Mobile Services {#places-mobile-svcs-messaging}
      + [Adobe Mobile Services](use-places-with-other-solutions/places-mobile-svcs-for-messaging/use-places-mobie-svcs-messaging.md)
      + [推送通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-push.md)
      + [应用程序内通知](use-places-with-other-solutions/places-mobile-svcs-for-messaging/mobile-svcs-messaging-inapp.md)
   + Adobe Campaign Standard {#places-acs}
      + [将Places服务与Adobe Campaign Standard结合使用](use-places-with-other-solutions/places-acs/places-acs-overview.md)
      + [推送通知](use-places-with-other-solutions/places-acs/places-acs-push-notifications.md)
      + [应用程序内消息](use-places-with-other-solutions/places-acs/places-acs-in-app-messages.md)
   + Adobe Target {#places-target}
      + [将Places服务与Adobe Target结合使用](use-places-with-other-solutions/places-target/places-target.md)
+ 测试和验证 {#places-testing-validation}
   + [测试和验证Places服务](places-testing-validation/test-validate-places.md)
+ [常见问题解答](places-faqs.md)
