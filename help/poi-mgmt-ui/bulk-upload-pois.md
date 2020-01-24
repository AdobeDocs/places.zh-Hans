---
title: 批量上传POI
description: 本节提供有关如何批量上传POI的信息。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# 批量上传POI {#bulk-upload-pois}

已创建一组Python脚本，以通过Web服务API简化从。csv文件到POI数据库的POI的批量导入。 这些脚本可从此开放源代码 [git存储库下载](https://github.com/adobe/places-scripts)。

在运行这些脚本之前，要访问Web服务API，请参阅集成概 *述和先决条件中用户访问*[的先决条件](/help/web-service-api/adobe-i-o-integration.md)。

以下是有关这些脚本的一些信息：

>[!TIP]
>
>此信息也包含在 [git存储库的自述文件中](https://github.com/adobe/places-scripts)。

## CSV文件

示例。csv文件是此包 `places_sample.csv`的一部分，它包含所需的标题和一行示例数据。 这些标题均为小写，与在Places数据库中使用的保留元数据键相对应。 添加到。csv文件的列将作为键／值对添加到POI数据库的每个POI的单独元数据部分中的列，并且头值用作键。

以下是您需要使用的列和值的列表：

* `lib_id`

   从POI数据库获取的有效库ID。

* `type`

   Point目前是唯一有效的值。

* `longitude`

   介于-180和180之间的值。

* `latitude`

   介于-85和85之间的值。

* `radius`

   介于10到20,000之间的值。

### 列值

以下列的值在Places Service UI中使用：

* color，它用作PIN的颜色，该颜色表示POI在Places Service UI映射中的位置。
   * 有效值为“”、#3E76D0、#AA99E8、#DC2ABA、#FC685B、#FC962E、#F6C436、#BECE5D、#61B56Bb和#3DC8DE和“”。
   * 如果该值留空，则Places Service UI使用蓝色作为默认颜色。

      这些值对应于蓝色(#3E76D0)、紫色(#AA99E8)、富士基亚(#DC2ABA)、橙色(#FC685B)、浅橙色(#FC962E)、黄色(#F6C436)、浅绿色(#BECE5D)、绿色(#61B56B)和浅蓝色(#3DC8DE)。

* 图标，它用作PIN上的图标，该图标表示POI在Places Service UI映射上的位置。

   * 有效值为“”、商店、酒店、汽车、火车、船、体育场、娱乐公园、锚、烧杯、钟、标书、书籍、箱包、公文包、浏览、笔刷、建筑、计算器、照相机、钟、教育、手电筒、跟踪、游戏、女性、礼物、锤子、心、家、钥匙、启动、灯、邮筒、销、促销、丝带、购物车、星目标，茶壶，拇指向下，拇指向上，陷阱，奖杯，扳手。

      图标值按它们在下图中显示的顺序列出：

      ![图标](/help/assets/UI_icons.png)

   * 如果该值留空，则UI将使用星形作为默认图标。

* 未提及的列可留空。

## 运行脚本

1. 将文件从 [git存储库下载](https://github.com/adobe/places-scripts) 到您的本地目录。
1. 在文本编辑器中，打开文 `config.py` 件并完成以下任务：

   a.将以下变量值编辑为字符串：

   * `csv_file_path`

      这是您的文件的路 `.csv` 径。

   * `access_code`

      这是您从调用Adobe IMS中获取的访问代码。 有关如何获取此访问代码的信息，请参阅集成概 *述和先决条件中* ，用 [户访问的先决条件](/help/web-service-api/adobe-i-o-integration.md)。

   * `org_id`

      要导入POI的Experience cloud组织ID。 有关如何获取组织ID的信息，请参阅集成概 *述和入门项目中用户访问*[的先决条件](/help/web-service-api/adobe-i-o-integration.md)。

   * `api_key`

      这是您从Adobe I/O Places集成获得的Places REST API密钥。 有关如何获取API密钥的信息，请参阅集成概 *述和入门项目中用户访* 问 [的先决条件](/help/web-service-api/adobe-i-o-integration.md)。
   b.保存更改。

1. 在终端窗口中，导航到该目 `…/places-scripts/import/` 录。
1. 输入 `python ./places_import.py` 并按 **[!UICONTROL enter]**(**[!UICONTROL return]**)键。


## 预导入CSV检查

脚本首先对。csv文件完成以下检查：

* 是否指 `.csv` 定了文件。
* 文件路径是否有效。
* 是否包含保留的元数据标题。

   保留的元数据标题为lib_id、name、description、type、longitude、latitude、radius、country、state、city、street、category、icon和color。

   >[!TIP]
   >
   >标题均采用小写形式，可以按任意顺序列出。

* 验证在CSV文件部分中指定的列的值。

如果找到错误，则脚本将打印出错误并中止。 如果未找到错误，脚本将尝试以1000批次导入POI。 如果成功导入了批，则脚本报告状态代码为200。 如果未成功导入批，则会报告错误。

## 单元测试

单元测试位于文 `tests.py` 件中，应在每个拉取请求之前运行，并且应全部通过。 应使用新代码添加其他测试。 要运行测试，请导航到目 `…/places-scripts/import/` 录，然后在 `python ./places_import.py` 终端中输入。
