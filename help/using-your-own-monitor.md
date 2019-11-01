---
title: 使用您自己的显示器
seo-title: 使用您自己的显示器
description: '您还可以使用监视服务，并通过使用Places扩展API与Places集成。 '
seo-description: '您还可以使用监视服务，并通过使用Places扩展API与Places集成。 '
translation-type: tm+mt
source-git-commit: a2e30282789d9834e5c65502e28ddb25f3c55dfa

---


# 使用您自己的显示器 {#using-your-monitor}

您还可以使用监视服务，并通过使用Places扩展API与Places集成。

## 注册地理围栏

如果您决定使用监视服务，请完成以下步骤，在您当前位置周围注册POI的地理位置：

### iOS

在iOS中，完成以下步骤：

1. 将从iOS的核心位置服务获取的位置更新传递到Places扩展。

1. 使用 `getNearbyPointsOfInterest` Places扩展API获取当前位 *置*`ACPPlacesPoi` 周围的n个对象的数组。

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
   
          [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
              [self startMonitoringGeoFences:nearbyPoi];
      }];
   
   }
   ```

1. 从获取的对象中提取信 `ACPPlacesPOI` 息并开始监控这些POI。

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center                                                                                                                              radius:currentRegion.radius                                                                                                                    identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
   
       }
   }
   ```

### Android

1. 将从Google play服务或Android位置服务获取的位置更新传递到Places Extension。

1. 使用 `getNearbyPointsOfInterest` Places Extension API获取当前位置周围 `PlacesPoi` 的n个对象的列表。

   ```java
       LocationCallback callback = new LocationCallback() {
               @Override
               public void onLocationResult(LocationResult locationResult) {
                   super.onLocationResult(locationResult);
   
                   Places.getNearbyPointsOfInterest(currentLocation, 10, new            AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois)
                   starMonitoringGeofence(pois);
               }
           });
   
               }
           };
   ```

1. 从获取的对象中提取数 `PlacesPOI` 据并开始监控这些POI。

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
               final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
               geofences.add(fence);
           }
   
           GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
           builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
           builder.addGeofences(geofences);
           builder.build();
           geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


调用 `getNearbyPointsOfInterest` API会导致网络调用，该调用获取当前位置周围的位置。

>[!IMPORTANT]
>
>您应该少调用API，或仅在用户位置发生显着变化时调用。

## 发布地理科学事件

### iOS

在iOS中，调用委 `processGeofenceEvent` 托中的Places API `CLLocationManager` 。 此API会通知您用户是已进入还是退出特定区域。

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```
