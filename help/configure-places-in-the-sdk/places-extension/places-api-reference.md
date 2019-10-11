---
title: Places API参考
seo-title: Places API参考
description: 有关Places中API引用的信息。
seo-description: 有关Places中API引用的信息。
translation-type: tm+mt
source-git-commit: 1fb87285d2ccd581ee59ab1b1efbec4af04a0fab

---


# Places API参考 {#places-api-reference}

以下是有关Places中API引用的信息：

## 处理区域事件

当设备跨越应用程序预定义的地点区域边界时，区域和事件类型将传递给SDK进行处理。

### ProcessGeofence(Android)

处理所 `Geofence` 提供的区域事件 `transitionType`。

传递 `transitionType` 自 `GeofencingEvent.getGeofenceTransition()`。 当前 `Geofence.GEOFENCE_TRANSITION_ENTER` 和 `Geofence.GEOFENCE_TRANSITION_EXIT` 受支持。

**语法**

下面是这种方法对应的语法：

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**示例**

在注册用于接收Android `IntentService` 地理围栏事件的方法中调用此方法。

以下是此方法的代码示例：

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call Adobe Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent(iOS)

此方法应在委托中调 `CLLocationManager` 用，该委托告知用户是否已进入或退出特定区域。

**语法**

下面是这种方法对应的语法：

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**示例**

以下是这种方法的代码示例：


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofercingEvent(Android)

同时 `Geofences` 处理所 `GeofencingEvent` 有内容。

**语法**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**示例**

在注册用于接收Android地 `IntentService` 理科学事件的您中调用此方法

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call Adobe Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## 检索附近的目标点

返回回调中附近POI的有序列表。

### GetEncorredPointsOfInterest(Android)

下面是这种方法对应的语法：

**语法**

```java
public static void getNearbyPointsOfInterest(final Location location,
    final int limit, final AdobeCallback<List<PlacesPOI>> callback);
```

**示例**

以下是这种方法的代码示例：

```java
Places.getNearbyPlaces(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});
```

### GetEncorredPointsOfInterest(iOS)

**语法**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;
```

**示例**

```objectivec
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];
```

## 检索当前设备关注点

请求设备当前已知位于其中的POI列表，并在回调中返回它们。

### GetCurrentPointsOfInterest(Android)

下面是这种方法对应的语法：

**语法**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**示例**

以下是这种方法的代码示例：

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest(iOS)

**语法**

下面是这种方法对应的语法：

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**示例**

以下是这种方法的代码示例：

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## 获取设备的位置

请求设备的位置（如之前所知），由“地点”扩展。

>[!TIP]
>
>地点扩展只了解通过呼叫向其提供的位置 `GetNearbyPointsOfInterest`。


### GetLastKnownLocation(Android)

**语法**

下面是这种方法对应的语法：

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**示例**

以下是这种方法的代码示例：

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation(iOS)

**语法**

下面是这种方法对应的语法：

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**示例**

以下是这种方法的代码示例：

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## 清除客户端数据


### 清除(Android)

清除处于共享状态、本地存储和内存中的“地点”的客户端数据。

**语法**

下面是这种方法对应的语法：

```java
public static void clear();
```

**示例**

以下是这种方法的代码示例：

```java
Places.clear();
```

### clear(iOS)

清除处于共享状态、本地存储和内存中的“地点”的客户端数据。

**语法**

下面是这种方法对应的语法：

```objectivec
+ (void) clear;
```

**示例**

以下是这种方法的代码示例：

```objectivec
[ACPPlaces clear];
```