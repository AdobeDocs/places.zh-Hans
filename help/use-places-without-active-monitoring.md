---
title: 使用Places Service，而不进行活动区域监控
description: 本节提供有关如何在不进行活动区域监控的情况下使用Places Service的信息。
exl-id: 0ba7949a-447e-4754-9b45-945e58e29541
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 1%

---

# 使用Places Service，而不进行活动区域监控 {#use-places-without-active-monitoring}

您的应用程序的用例可能不需要进行活动区域监控。 Places Service仍可用于将用户的位置数据与其他Experience Platform产品集成。

## 先决条件

开发人员将使用目标平台操作系统提供的API收集设备的位置。

>[!TIP]
>
>如果您的应用程序用例需要活动区域监控，请参阅 [将Places Service与您自己的监控解决方案结合使用](/help/using-your-own-monitor.md).

要使用Places Service，而不进行活动区域监控，请执行以下操作：

## 1.收集用户的位置

应用程序开发人员必须使用 `CoreLocation.framework` (iOS)或 `Location` 由Google Play服务(Android)提供的API。

有关更多信息，请参阅以下文档：

- [CoreLocation](https://developer.apple.com/documentation/corelocation) (Apple)
- [Google Play服务中的位置API](https://developer.android.com/training/location) (Google)

## 2.从SDK中检索附近的目标点

获取用户位置后，可以将其传递到SDK，以返回附近POI的列表。

### Android

以下是Android中使用 [`BroadcastReceiver`](https://codelabs.developers.google.com/codelabs/background-location-updates-android-o/index.html?index=..%2F..index#5):

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

以下是iOS的实施示例。 该代码显示了 [`locationManager:didUpdateLocations:`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager?language=objc) 方法 [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager?language=objc):

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

以下是iOS的实施示例。 该代码显示了 [`locationManager(_:didUpdateLocations:)`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager) 方法 [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager):

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

## 3.将Places数据附加到Analytics请求

通过调用 `getNearbyPointsOfInterest` API中，Places SDK将通过Launch中的数据元素，使与设备相关的所有POI数据都可用。 通过使用 [附加数据](https://aep-sdks.gitbook.io/docs/resources/user-guides/attach-data) 规则中，可以将Places数据自动添加到将来对Analytics的请求中。 这样，在收集设备位置时便无需对Analytics进行一次性调用。

请参阅 [将位置上下文添加到Analytics请求](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md) 以了解有关此主题的更多信息。

## 可选 — 当用户位于POI中时触发登入事件

>[!TIP]
>
>捕获Places数据的推荐方法是 [将Places数据附加到Analytics请求](#attach-places-data-to-your-analytics-requests).
>
>如果用例需要 [区域登入事件](places-ext-aep-sdks/places-extension/places-event-ref.md#processregionevent) 要由SDK触发，需要手动完成，如下所述。

返回的列表 `getNearbyPointsOfInterest` API包含 [自定义对象](places-ext-aep-sdks/places-extension/cust-places-objects.md) 指示用户当前是否在POI内。 如果用户在POI中，您可以让SDK触发该区域的登入事件。

>[!IMPORTANT]
>
>要防止您的应用程序在一次访问中触发多个条目事件，请保留您知道用户在哪些地区进入的列表。 在处理来自SDK的附近POI的响应时，仅当该区域不在您的列表中时，才会触发登入事件。
>
>在以下代码示例中， `NSUserDefaults` (iOS和 `SharedPreferences` (Android)用于管理区域列表：

### Android

以下代码示例显示了对的回调中提供的结果的处理 `getNearbyPointsOfInterest`, a `List<PlacesPOI>`:

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

以下代码示例显示了对的回调中提供的结果的处理 `getNearbyPointsOfInterest:limit:callback:errorCallback:`, `NSArray<ACPPlacesPoi *> *`:

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

以下代码示例显示了对的回调中提供的结果的处理 `getNearbyPoints(_ ofInterest: CLLocation, limit: UInt, callback: (([ACPPlacesPoi]?) -> Void)?, errorCallback: ((ACPPlacesRequestError) -> Void)?)`, `[ACPPlacesPoi]`:

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

## 完成实施示例

以下代码示例向您展示了如何检索设备的当前位置、触发必要的登入事件，以及确保在一次访问中不会获得同一位置的多个条目。

此代码示例包含的可选步骤为 [当用户位于POI中时触发条目事件](#trigger-entry-events-when-the-user-is-in-a-poi).

>[!IMPORTANT]
>
>这些片段是 **仅** 示例。 开发人员必须确定要如何实施该功能，并且决策时应考虑目标操作系统建议的最佳实践。

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

除了触发SDK中的Places Service条目事件之外，由于触发条目事件，SDK的其余部分还可以通过使用定义POI的所有数据 `data elements` Experience Platform Launch。 与Experience Platform Launch `rules`，您可以将Places Service数据动态附加到SDK处理的传入事件。 例如，您可以附加用户所在POI的元数据，并将该数据作为上下文数据发送到Analytics。

有关更多信息，请参阅 [将Places Service与其他Adobe解决方案结合使用](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md).
