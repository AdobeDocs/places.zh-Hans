---
title: 不使用活动区域监视的Places服务
description: 本节提供有关如何在没有活动区域监视的情况下使用Places服务的信息。
exl-id: 0ba7949a-447e-4754-9b45-945e58e29541
TQID: https://experienceleague.adobe.com/xUmdMOa5CvDZSxKFeyse-3vHsUwvm2s04-sIG0FnnCs
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: bef6f891-2e8a-425e-8f99-7ddf22070daa
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
subfeature_v2:
  - id: b572b7ff-a413-4173-b2b4-d7d3874f1b9b
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
  - id: ee602049-8a18-43df-9299-a689a025a371
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 786
ht-degree: 0%

---

# 不使用活动区域监视的Places服务 {#use-places-without-active-monitoring}

应用程序的用例可能不需要主动区域监控。 Places Service仍可用于将用户的位置数据与其他Experience Platform产品集成。

## 先决条件

开发人员将使用目标平台操作系统提供的API来收集设备的位置。

>[!TIP]
>
>如果您的应用用例需要主动区域监控，请参阅[将Places服务用于您自己的监控解决方案](/help/using-your-own-monitor.md)。

要在不使用活动区域监视的情况下使用Places服务，请执行以下操作：

## &#x200B;1. 收集用户的位置

应用程序开发人员必须使用Google Play Services (Android)提供的`CoreLocation.framework` (iOS)或`Location` API来收集设备的当前位置。

有关更多信息，请参阅以下文档：

- [CoreLocation](https://developer.apple.com/documentation/corelocation) (Apple)
- Google Play Services中的[位置API](https://developer.android.com/training/location) (Google)

## &#x200B;2. 从SDK检索附近的目标点

获取用户的位置后，您可以将其传递到SDK以取回附近POI的列表。

### Android

以下是Android中使用[`BroadcastReceiver`](https://codelabs.developers.google.com/codelabs/background-location-updates-android-o/index.html?index=..%2F..index#5)的示例实现：

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }
}
```

### Objective-C

以下是iOS的实施示例。 代码显示[`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager?language=objc)中[`locationManager:didUpdateLocations:`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager?language=objc)方法的实现：

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}
```

### Swift

以下是iOS的实施示例。 代码显示[`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager)中[`locationManager(_:didUpdateLocations:)`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager)方法的实现：

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}
```

## &#x200B;3. 将Places数据附加到您的Analytics请求

通过调用`getNearbyPointsOfInterest` API，Places SDK将通过Launch中的数据元素提供与设备相关的所有POI数据。 通过使用[附加数据](https://aep-sdks.gitbook.io/docs/resources/user-guides/attach-data)规则，可以将Places数据自动添加到将来向Analytics发出的请求中。 这样一来，在收集设备位置时，便无需一次性调用Analytics。

有关此主题的更多信息，请参阅[将位置上下文添加到Analytics请求](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md)。

## 可选 — 当用户处于POI中时触发进入事件

>[!TIP]
>
>捕获Places数据的推荐方法是[将Places数据附加到您的Analytics请求](#attach-places-data-to-your-analytics-requests)。
>
>如果用例要求由SDK触发[region entry event](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#processregionevent)，则需要手动完成，如下所示。

`getNearbyPointsOfInterest` API返回的列表包含[自定义对象](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#additional-classes-and-enums)，用于指示用户当前是否在POI内。 如果用户处于POI中，您可以让SDK触发该区域的进入事件。

>[!IMPORTANT]
>
>要防止应用程序在一次访问中触发多个进入事件，请保留您知道用户已进入的地区的列表。 处理来自SDK的附近POI的响应时，仅当该地区不在您的列表中时才会触发进入事件。
>
>在以下代码示例中，`NSUserDefaults` (iOS)和`SharedPreferences` (Android)用于管理区域列表：

### Android

以下代码示例显示了对`getNearbyPointsOfInterest` （即`List<PlacesPOI>`）回调中提供的结果的处理：

```java
void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
    // get the list of regions we know the user is already within from SharedPreferences
    SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
    Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

    // loop through new placesPOIS and post entry events for pois that aren't already in our list
    // also create the new list of regions that the user is in
    Set<String> updatedRegionsUserIsIn = new HashSet<String>();
    for (PlacesPOI poi : nearbyPois) {
        // check if the user is in this poi
        if (poi.containsUser()) {
            // the user is in the poi, now we need to make sure we haven't already recorded this entry event
            if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                Geofence poiGeofence = new Geofence.Builder()
                    .setRequestId(poi.getIdentifier())
                    .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                    .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                    .setExpirationDuration(Geofence.NEVER_EXPIRE)
                    .build();
                Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
            }

            // add the region to our new list of regions
            updatedRegionsUserIsIn.add(poi.getIdentifier());
        }
    }

    // update SharedPreferences with our new list of regions
    SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
    editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
}
```

### Objective-C

以下代码示例显示了对`getNearbyPointsOfInterest:limit:callback:errorCallback:` （即`NSArray<ACPPlacesPoi *> *`）回调中提供的结果的处理：

```objectivec
- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

以下代码示例显示了对`getNearbyPoints(_ ofInterest: CLLocation, limit: UInt, callback: (([ACPPlacesPoi]?) -> Void)?, errorCallback: ((ACPPlacesRequestError) -> Void)?)` （即`[ACPPlacesPoi]`）回调中提供的结果的处理：

```swift
func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

## 完整的实施示例

以下代码示例显示了如何检索设备的当前位置、触发必要的进入事件以及确保一次访问不会获得同一位置的多个条目。

此代码示例包括可选步骤[，即当用户处于POI](#trigger-entry-events-when-the-user-is-in-a-poi)中时触发进入事件。

>[!IMPORTANT]
>
>这些代码片段仅&#x200B;**是**&#x200B;示例。 开发人员必须确定如何实施该功能，并且该决策应考虑目标操作系统推荐的最佳实践。

### Android

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                    handleUpdatedPOIs(pois);
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }

    void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
        // get the list of regions we know the user is already within from SharedPreferences
        SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
        Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

        // loop through new placesPOIS and post entry events for pois that aren't already in our list
        // also create the new list of regions that the user is in
        Set<String> updatedRegionsUserIsIn = new HashSet<String>();
        for (PlacesPOI poi : nearbyPois) {
            // check if the user is in this poi
            if (poi.containsUser()) {
                // the user is in the poi, now we need to make sure we haven't already recorded this entry event
                if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                    Geofence poiGeofence = new Geofence.Builder()
                        .setRequestId(poi.getIdentifier())
                        .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                        .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                        .setExpirationDuration(Geofence.NEVER_EXPIRE)
                        .build();
                    Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
                }

                // add the region to our new list of regions
                updatedRegionsUserIsIn.add(poi.getIdentifier());
            }
        }

        // update SharedPreferences with our new list of regions
        SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
        editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
    }
}
```


### Objective-C

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
        [self handleUpdatedPOIs:nearbyPoi];
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}

- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
        self.handleUpdatedPOIs(nearbyPoi!)
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}

func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

由于触发了进入事件，因此除了在SDK中触发Places Service进入事件之外，SDK的其他人还可以通过Experience Platform Launch中的`data elements`使用定义您的POI的所有数据。 使用Experience Platform Launch `rules`，您可以将Places服务数据动态附加到SDK处理的传入事件。 例如，您可以附加用户所在的POI的元数据，然后将该数据作为上下文数据发送到Analytics。

有关详细信息，请参阅[将Places服务与其他Adobe解决方案结合使用](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)。
