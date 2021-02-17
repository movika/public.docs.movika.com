---
title: Movika Documentation 
description: Movika Documentation  SDK web, iOS, Android
keywords: documentation, movika, sdk, ios, android, web, interactive video
sort: 0
---

# Movika Documentation  
Язык: [English](README.md), [Русский](README.ru.md)
## SDK

### Web

Integration of Web SDK Movika to the site is carried out by embedding the iframe tag in the HTML markup of the page. 

Example tag **iframe**, displaying an interactive video player with a size of 840x560 pixels is shown below:

```
 <iframe style="width:840px; height:560px" allowFullScreen src="https://movika.com/player/123Sd">
 </iframe>
```

Parameters (attributes) iframe:

- **src** - contains a URL pointing to a path containing interactive video content ;
- **width** - sets the width of the video content player ;
- **height** - sets the height of the video content player ;
- **allowFullScreen** - enables or disables full-screen video playback.

### Mobile SDK

To add an interactive player to your mobile application, use the following instructions
for Android or iOS platform. 

To use sdk you also need to get API Key for your applications. Write to us at 
Telegram [@Salavatsad](https://t.me/Salavatsad) or by mail [support@movika.com](mailto:support@movika.com),
[sdk@movika.com](mailto:sdk@movika.com),
to get the API key.

#### iOS SDK

1. [Getting started](/en/sdk/ios/get-started.md)
2. [Saving movie state](/en/sdk/ios/save-state.md)
3. [Interface customization](/en/sdk/ios/ui-customization.md)
4. [Custom interactives](/en/sdk/ios/custom-events.md)

#### Android SDK

0. [Getting started](/en/sdk/android/getting-started.md)
1. [Getting data for playback](/en/sdk/android/getting-movie-bundle.md)
2. [Playback](/en/sdk/android/run-interactiveplayerview.md)
3. [Player configuration](/en/sdk/android/config.md)
4. [Player events](/en/sdk/android/player-events.md)
5. [Player customization](/en/sdk/android/introduce-to-player-customization.md)
6. [Customize pause and play](/sdk/android/play-pause-customization.md)
7. [Customization of interface elements for switching audio tracks and subtitles](/en/sdk/android/audio-subtitles-customization.md)
8. [Interactive customization](/en/sdk/android/interactive-customization.md)
