---
title: Places Monitor扩展
description: “地点监视器”扩展处理与操作系统的交互，以注册和监视最接近用户的POI。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Places Monitor扩展 {#places-monitor-extension}

“地点监视器”扩展处理与操作系统的交互，以注册和监视最接近用户的POI。 此扩展检索需要从“地点”扩展中注册的POI，并将进入和退出通知传递到“地点”扩展。 这些通知将作为事件在Experience Platform启动规则中可用。

“监视器”扩展是可选的，因为某些客户可能已经在使用操作系统监视区域。 如果出现这种情况，请确保添加Places扩展API以从Places数据库接收最近的POI，并传递进入和退出事件，以便采取相应的操作。
