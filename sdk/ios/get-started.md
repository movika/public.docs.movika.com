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
  pod 'MKAnalytics', :git => 'https://bitbucket.org/interactiveplatform/ios.metrics.movika.com.git'
  pod 'MKLogger', :git => 'https://bitbucket.org/lenar-gilyazov/mklogger.git'
end

```

To get access to git repositories, make an inquiry to the sdk@movika.com or support@movika.com.

Replace YOUR_TARGET_NAME, go to the Podfile folder and run the command:

```
$ pod install
```

## 2. Add your ApiKey

To get an API_KEY, make an inquiry to the support@movika.com.

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

1. Create a new class view controller and inherit it from the MovikaPlayerViewController class
2. Load the data (GameManifest structure) needed to play the movie using the DefaultGameManifestDownloader load(..) method

```
let downloader = DefaultGameManifestDownloader(downloadManifestDelegate: self)
downloader.load(movie: Movie(id: movieId, manifestUrl: movieManifestLink), downloadWasEnded: { manifest, error  in
    if let error = error {
        print("Error loading manifeist \(error.localizedDescription)")
    } else {
        self.manifest = manifest
        print("Manifest ready for playing")
    }
})
```

3. When the GameManifest is loaded, pass it to the player by calling controller class setup(..) method. (Link to test manifest https://bitbucket.org/Ortyom/mobileassets/raw/HEAD/vertical/json/manifest.json)

```
 self.setup(playerRepository: DefaultPlayerRepository(),
                   manifest: manifest,
                   startFromSavePoint: false,
                   customEventViewFactory: nil)
```

4. When the player finishes playing the movie, controller's method onMovieEnded will be called, or onMovieClose if the user clicks on the button to end playback

```
func onMovieClose() {
    self.dismiss(animated: true, completion:nil)
}

func onMovieEnded(history: InteractionHistory) {
    self.dismiss(animated: true, completion:nil)
}
```
