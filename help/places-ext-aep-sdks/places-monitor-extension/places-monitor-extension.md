---
title: 地点监视器扩展
description: 位置监视器扩展处理与操作系统的交互，以注册和监视最接近用户的POI。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# 地点监视器扩展 {#places-monitor-extension}

位置监视器扩展处理与操作系统的交互，以注册和监视最接近用户的POI。 此扩展检索需要从Places扩展中注册的POI，并将进入和退出通知传递到Places扩展。 这些通知在Experience Platform Launch规则中将作为事件提供。

“监视器”扩展是可选的，因为某些客户可能已经在使用操作系统监视区域。 如果出现这种情况，请确保添加Places扩展API以从Places Service数据库接收最接近的POI，并传递进入和退出事件，以便采取适当的操作。
