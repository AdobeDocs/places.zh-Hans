---
title: Places API参考
description: 有关Places中API引用的信息。
feature: Mobile SDK
exl-id: ce1a113c-dee0-49df-8d2f-789ccc1c8322
source-git-commit: f521d5e3b0b69977877d88382ce41fcb7d1c54b9
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 32%

---

# Places API参考 {#places-api-reference}

以下是有关Places扩展中的API引用的信息：

## 处理区域事件

当设备跨越应用程序预定义的Places服务区域边界之一时，该区域和事件类型将传递到SDK进行处理。

### 进程地理围栏(Android)

进程a `Geofence` 提供的的区域事件 `transitionType`.

传递 `transitionType` 从 `GeofencingEvent.getGeofenceTransition()`. 当前 `Geofence.GEOFENCE_TRANSITION_ENTER` 和 `Geofence.GEOFENCE_TRANSITION_EXIT` 受支持。

**语法**

以下是此方法的语法：

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**示例**

在您的中调用此方法 `IntentService` 注册以接收Android地理围栏事件。

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

### ProcessRegionEvent (iOS)

此方法应在 `CLLocationManager` 委派，用于告知用户是否已进入或退出特定区域。

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

### ProcessGeofencingEvent (Android)

全部处理 `Geofences` 在 `GeofencingEvent` 同时。

**语法**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**示例**

在您的中调用此方法 `IntentService` 注册以接收Android地理围栏事件的用户

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

返回回调中附近POI的有序列表。 如果生成的网络调用出错，则此方法的多载版本将返回错误代码。

### GetNeartherPointsOfInterest (Android)

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

### GetInnearlyPointsOfInterest (iOS)

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

## 检索当前设备目标点

请求当前已知设备所在的POI列表，并在回调中返回这些POI。

### GetCurrentPointsOfInterest (Android)

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

### GetCurrentPointsOfInterest (iOS)

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

请求Places扩展以前所知的设备位置。

>[!TIP]
>
>Places扩展仅知道通过调用向其提供的位置 `GetNearbyPointsOfInterest`.


### GetLastKnownLocation (Android)

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

### GetLastKnownLocation (iOS)

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

清除Places扩展处于共享状态、本地存储和内存中的客户端数据。

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

### 清除(iOS)

清除Places扩展处于共享状态、本地存储和内存中的客户端数据。

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

### setAuthorizationStatus (Android)

*从Places v1.4.0开始提供*

在Places扩展中设置授权状态。

提供的状态存储在Places共享状态中，仅供参考。
调用此方法不会影响此设备的实际位置授权状态。

**语法**

以下是此方法的语法：

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**示例**

以下是此方法的代码示例：

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*从ACPPlaces v1.3.0开始提供*

在Places扩展中设置授权状态。

提供的状态存储在Places共享状态中，仅供参考。
调用此方法不会影响此设备的实际位置授权状态。

当设备授权状态发生变化时， `locationManager:didChangeAuthorizationStatus:` 方法 `CLLocationManagerDelegate` 将调用。 在此方法中，您应该传递新的 `CLAuthorizationStatus` ACPlaces的值 `setAuthorizationStatus:` API。

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
