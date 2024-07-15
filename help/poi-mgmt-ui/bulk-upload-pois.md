---
title: 批量上传POI
description: 本节提供有关如何批量上传POI的信息。
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# 批量上传POI {#bulk-upload-pois}

Places服务中的&#x200B;**导入POI**&#x200B;按钮可用于使用CSV文件批量上传新的POI。 提供了一个电子表格模板示例，用于显示需要哪些数据列以及如何添加可选的自定义元数据。

![批量导入屏幕](/help/assets/Bulk-import.png)

请观看以下视频，了解批量导入和批量编辑的过程：

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Places服务批量导入和编辑POI](https://www.youtube.com/watch?v=75qVtirsXhg)

## Python API脚本

已创建了一组Python脚本，以简化使用Web服务API将.csv文件中的POI批量导入POI数据库的工作。 可以从此开放源代码[Git存储库](https://github.com/adobe/places-scripts)下载这些脚本。

在运行这些脚本之前，要访问Web服务API，请参阅[集成概述和先决条件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*用户访问的先决条件*。

以下是有关脚本的一些信息：

>[!TIP]
>
>此信息还包含在[Git存储库](https://github.com/adobe/places-scripts)的自述文件中。

## CSV 文件

示例.csv文件`places_sample.csv`是此包的一部分，并包含所需的标头和示例数据行。 这些标头全部为小写，对应于Places数据库中使用的保留元数据键。 您添加到.csv文件中的列将作为键/值对添加到POI数据库的每个POI的单独元数据部分中，并且标头值将用作键。

以下是您需要使用的列和值的列表：

* `lib_id`

  从POI数据库获取的有效库ID。

* `type`

  点是当前唯一的有效值。

* `longitude`

  介于–180和180之间的值。

* `latitude`

  介于–85和85之间的值。

* `radius`

  介于10和20,000之间的值。

### 列值

以下列的值在Places服务UI中使用：

* 颜色，用作Places服务UI映射中POI位置的pin的颜色。
   * 有效值为“”、#3E76D0、#AA99E8、#DC2ABA、#FC685B、#FC962E、#F6C436、#BECE5D、#61B56B和#3DC8DE以及“”。
   * 如果该值留空，则Places服务UI使用蓝色作为默认颜色。

     这些值分别对应于蓝色(#3E76D0)、紫色(#AA99E8)、紫色(#DC2ABA)、橙色(#FC685B)、浅橙色(#FC962E)、黄色(#F6C436)、浅绿色(#BECE5D)、绿色(#61B56B)和浅蓝色(#3DC8DE)。

* 图标，用作Places服务UI映射中POI位置的pin上的图标。

   * 有效值为“”、商店、旅馆、汽车、飞机、火车、船、体育场、游乐园、锚点、烧杯、铃、出价、书、盒、公文包、浏览、刷子、建筑物、计算器、相机、时钟、教育、手电筒、关注、游戏、女性、男性、礼物、锤子、心、家、钥匙、发射、灯泡、邮箱、钱、图钉、促销、彩带、购物车、星星、目标、茶壶、thumbDown、thumbUp、陷阱、奖杯、扳手。

     图标值按如下图所示的顺序列出：

     UI中的![图标](/help/assets/UI_icons.png)

   * 如果将该值留空，则UI使用星形作为默认图标。

* 未提及的列可留空。

## 运行脚本

1. 将文件从[Git存储库](https://github.com/adobe/places-scripts)下载到您的本地目录。
1. 在文本编辑器中，打开`config.py`文件并完成以下任务：

   a.将以下变量值编辑为字符串：

   * `csv_file_path`

     这是您的`.csv`文件的路径。

   * `access_code`

     这是您的访问代码，通过调用Adobe IMS获取。 有关如何获取此访问代码的信息，请参阅[集成概述和先决条件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*用户访问的先决条件*。

   * `org_id`

     要将POI导入到的Experience CloudorgID。 有关如何获取组织ID的信息，请参阅[集成概述和先决条件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*用户访问的先决条件*。

   * `api_key`

     这是从Adobe I/OPlaces集成获得的Places REST API密钥。 有关如何获取API密钥的信息，请参阅[集成概述和先决条件](/help/web-service-api/adobe-i-o-integration.md)中的&#x200B;*用户访问的先决条件*。

   b.保存更改。

1. 在终端窗口中，导航到`…/places-scripts/import/`目录。
1. 输入`python ./places_import.py`并按&#x200B;**[!UICONTROL enter]** (**[!UICONTROL return]**)键。


## 预导入CSV检查

脚本最初对.csv文件完成以下检查：

* 是否指定了`.csv`文件。
* 文件路径是否有效。
* 是否包含保留的元数据标头。

  保留的元数据标头为lib_id、名称、描述、类型、经度、纬度、半径、国家/地区、州、城市、街道、类别、图标和颜色。

  >[!TIP]
  >
  >标头全部为小写，可以按任意顺序列出。

* 验证CSV文件部分中指定的列的值。

如果发现错误，脚本将打印出错误并中止。 如果未发现错误，脚本将尝试以1000为批次导入POI。 如果已成功导入批次，脚本将报告状态代码200。 如果未成功导入批次，则会报告错误。

## 单元测试

单元测试位于`tests.py`文件中，应在每个拉取请求之前运行，并且应全部通过。 应使用新代码添加其他测试。 要运行测试，请导航到`…/places-scripts/import/`目录，然后在终端中输入`python ./places_import.py`。
