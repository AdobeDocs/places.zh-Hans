---
title: Places Monitor扩展
description: Places Monitor扩展可处理与操作系统的交互，以注册和监视距用户最近的POI。
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Places Monitor扩展 {#places-monitor-extension}

Places Monitor扩展可处理与操作系统的交互，以注册和监视距用户最近的POI。 此扩展将检索需要从Places扩展中注册的POI，并将登入和退出通知传递到Places扩展。 这些通知将在Experience Platform Launch规则中作为事件提供。

Monitor扩展是可选的，因为某些客户可能已经使用操作系统监视区域。 如果是这种情况，请确保添加Places扩展API以从Places Service数据库中接收最接近的POI，并传递登入和退出事件，以便能够执行适当的操作。

## 弃用Places Monitor

2021年8月31日，将弃用适用于Adobe Experience Platform Mobile SDK的Places Monitor扩展。 8月31日之后，Places Monitor扩展将不会再收到更多更新或支持。

当前使用Places Monitor扩展的客户可以继续使用此扩展，但需要了解的是，将无法通过Adobe获取其他更新或支持。

Places Monitor扩展的弃用对Places Service扩展没有影响或负面影响，Places Service扩展将继续受到增强和更新的支持。

希望从Places Monitor扩展过渡到其自身的监控解决方案的客户应查阅以下文档：[将Places Service与您自己的监控解决方案结合使用](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en)。 本文档介绍如何通过在iOS上实施[核心位置服务](https://developer.apple.com/documentation/corelocation)或从Google Play中实施[位置服务](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary)来与Places Service进行交互。
