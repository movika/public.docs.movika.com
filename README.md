---
title: Movika Documentation
description: Movika Documentation  SDK web, iOS, Android
keywords: documentation, movika, sdk, ios, android, web, interactive video
sort: 0
---

# Movika Documentation

## SDK

### Web

Integration of the Movika Web SDK to your site can be done by embedding iframe in the HTML markup of the page.

 <iframe allowFullScreen src="https://movika.com/ru/player/movika-sdk-sample" allowFullScreen scrolling="no" frameborder="0">
 </iframe>

Example of the tag **iframe**, displaying an interactive video player with a size of 840x560 pixels is shown below:

```
 <iframe style="width:840px; height:560px" allowFullScreen src="https://movika.com/ru/player/movika-sdk-sample">
 </iframe>
```

Parameters (attributes) of the iframe:

- **src** - URL path of the interactive video content ;
- **width** - sets the width of the video player ;
- **height** - sets the height of the video player ;
- **allowFullScreen** - enables or disables full-screen video playback.

### Mobile SDK

To add an interactive player to your mobile application, use the following instructions
for Android or iOS platform.

To use the sdk you also need to get an API Key for your applications. 

Register your App in the [Movika Developer](https://developer.movika.com) and copy the resulting API key. Keys are generated separately for all platforms (iOS, Android and Web).

*For iframe API Key not required*

#### iOS SDK
Version 3.0.0-beta

Пример интеграции sdk https://github.com/movika/ios.sdk.sample.movika.com
1. [Getting started](/sdk/ios/v3/get-started.md)

Version 2.1.1

Sdk integration sample https://github.com/movika/ios.sdk.sample.movika.com

1. [Getting started](/sdk/ios/get-started.md)
2. [Saving movie state](/sdk/ios/save-state.md)
3. [Interface customization](/sdk/ios/ui-customization.md)
4. [Custom interactives](/sdk/ios/custom-events.md)
5. [Ready-to-use player](/sdk/ios/mk-easy-player.md)
6. [Custom player](/sdk/ios/mkplayer.md)

#### Android SDK

0. [Getting started](/sdk/android/getting-started.md)
1. [Getting data for playback](/sdk/android/getting-movie-bundle.md)
2. [Playback](/sdk/android/run-interactiveplayerview.md)
3. [Player configuration](/sdk/android/config.md)
4. [Player events](/sdk/android/player-events.md)
5. [Player customization](/sdk/android/introduce-to-player-customization.md)
6. [Customize pause and play](/sdk/android/play-pause-customization.md)
7. [Customization of interface elements for switching audio tracks and subtitles](/sdk/android/audio-subtitles-customization.md)
8. [Interactive customization](/sdk/android/interactive-customization.md)
