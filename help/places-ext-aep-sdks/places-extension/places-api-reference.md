---
title: Places API参考
seo-title: Places API参考
description: 有关Places中API引用的信息。
seo-description: 有关Places中API引用的信息。
translation-type: tm+mt
source-git-commit: 379278f7677d7d3cdc697d78c54693d0a3c62e02

---


# Places API参考 {#places-api-reference}

以下是有关Places中API引用的信息：

## 处理区域事件

当设备跨越应用程序预定义的地点区域边界时，区域和事件类型将传递给SDK进行处理。

### ProcessGeofence(Android)

处理所 `Geofence` 提供的区域事件 `transitionType`。

传递 `transitionType` 自 `GeofencingEvent.getGeofenceTransition()`。 当前 `Geofence.GEOFENCE_TRANSITION_ENTER` 和 `Geofence.GEOFENCE_TRANSITION_EXIT` 受支持。

**语法**

以下是此方法的语法：

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
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent(iOS)

此方法应在委托中调 `CLLocationManager` 用，该委托告知用户是否已进入或退出特定区域。

**语法**

以下是此方法的语法：

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**示例**

以下是此方法的代码示例：


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
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## 检索附近的目标点

返回回调中附近POI的有序列表。 如果生成的网络调用出现问题，此方法的重载版本将返回错误代码。

### GetEncorredPointsOfInterest(Android)

以下是此方法的语法：

**语法**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**示例**

以下是此方法的代码示例：

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetEncorredPointsOfInterest(iOS)

**语法**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**示例**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## 检索当前设备关注点

请求设备当前已知位于其中的POI列表，并在回调中返回它们。

### GetCurrentPointsOfInterest(Android)

以下是此方法的语法：

**语法**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**示例**

以下是此方法的代码示例：

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

以下是此方法的语法：

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**示例**

以下是此方法的代码示例：

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

以下是此方法的语法：

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**示例**

以下是此方法的代码示例：

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

以下是此方法的语法：

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**示例**

以下是此方法的代码示例：

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

以下是此方法的语法：

```java
public static void clear();
```

**示例**

以下是此方法的代码示例：

```java
Places.clear();
```

### clear(iOS)

清除处于共享状态、本地存储和内存中的“地点”的客户端数据。

**语法**

以下是此方法的语法：

```objectivec
+ (void) clear;
```

**示例**

以下是此方法的代码示例：

```objectivec
[ACPPlaces clear];
```

## 设置位置授权状态

### setAuthorizationStatus(Android)

即将推出

### setAuthorizationStatus(iOS)

*从ACPPlaces v1.3.0开始提供*

在“地点”扩展中设置授权状态。

提供的状态存储在“地点”共享状态中，仅供参考。
调用此方法不会影响此设备的实际位置授权状态。

当设备授权状态发生更改时，将 `locationManager:didChangeAuthorizationStatus:` 调用您的 `CLLocationManagerDelegate` 方法。 从此方法中，您应将新值传 `CLAuthorizationStatus` 递给ACPPlaces `setAuthorizationStatus:` API。

**语法**

以下是此方法的语法：

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**示例**

以下是此方法的代码示例：

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
