---
title: Getting started
description: Getting started
keywords: Getting started
sort: 0
---

# Getting started

## 1. Add sdk from the pod

```
# Podfile
use_frameworks!

target 'YOUR_TARGET_NAME' do
  use_frameworks!
  pod 'MovikaSDK', :git => 'https://bitbucket.org/interactiveplatform/ios.sdk.movika.com.git'
end

```

Replace YOUR_TARGET_NAME, go to the Podfile folder and run the command:

```
$ pod install
```

## 2. Add your ApiKey

Register your app in the [Movika Developer](https://developer.movika.com) and copy the resulting API key.

Put your apiKey in AppDelegate class in the application(..) method inside lambda function didFinishLaunchingWithOptions

Import the framework

```
import MovikaSDK
```

Add Movika.shared.apiKey = API_KEY

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.
        Movika.shared.apiKey = API_KEY
        return true
    }
```

## 3. Create your player

1. Create UIView component MKInteractivePlayer

```
let player = MKInteractivePlayer (frame: view.frame)
self.view.addSubview (player)
```
   
2. Set the URL to the MKManifest JSON data. Use MKManifestAsset

```
player.setManifestAsset (MKURLManifestAsset (URL: URL))
```

3. To start playback, call the player's play method

```
player.play ()
```

4. Track player status using MKPlayerDelegate
```
let player = MKInteractivePlayer (frame: view.frame)
player.delegate = self
```
