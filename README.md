# geocoding_client

A Flutter plugin for [Geocoding API](https://developers.google.com/maps/documentation/geocoding/overview) provided by one of the Google Maps Platform APIs.
iOSはまだ対応できてないよ。

## Getting Started

1. GoogleMapのAPIキーを設定してね。
https://pub.dev/packages/google_maps_flutter

2. pubspec.ymlのdependenciesに下記を追加してね。

``` yml
dependencies:
  geocoding_client:
    git:
      url: https://github.com/NIRANKEN/geocoding_client.git
      ref: 0.0.2
```

## Usage

### 場所の名前から住所と緯度経度を取得する

``` dart
import 'package:google_maps_flutter/google_maps_flutter.dart';

// ...

var client = GeocodingClient.instance;
List<PlaceMark> places = await client.getGeocode("場所の名前");
for (var placeMark in placeMarks) {
  logger.d('name: ${placeMark.name}, address: ${placeMark.address}, latLng: ${placeMark.latLng}'); 
}
```

### 座標から住所情報を取得する


``` dart
import 'package:google_maps_flutter/google_maps_flutter.dart';

// ...

const LatLng latLng = LatLng(26.6979421, 127.88);

var client = GeocodingClient.instance;
Place place = Place.fromPlaceMark(await client.getPlaceMark(latLng));
logger.d("address: ${placemark.address}, latLng: ${placemark.latLng}");
```
