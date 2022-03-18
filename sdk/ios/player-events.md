---
title: Player events
description: Player Events
keywords: Player Events
sort: 2 
---

# Player Events

To track player events you need to implement the **MKPlayerDelegate** protocol
---

The method is called when interacting with the player, the result is in the **InteractionResult** structure
```
func mkplayer(_ player: MKPlayer, result: InteractionResult)
```

This method is called on pause/resume video, the result is stored in **isPause** variable
```
func mkplayer(_ player: MKPlayer, isPause: Bool)
```

This method is called while watching video state, the result is located in **MKPlayState** structure
```
func mkplayer(_ player: MKPlayer, didUpdate state: MKPlayState)
```

The method is called if the interactive leads to this link, trace the result through **URL**
```
func mkplayer(_ player: MKPlayer, didRequestOpen uri: URL)
```

The method is called at the end of the video, track the result via **MKManifest**
```
func mkplayer(_ player: MKPlayer, didEndPlaying manifest: MKManifest)
```

The method is called before starting to show the interactive in the current chapter **Chapter**
```
func mkplayer(_ player: MKPlayer, willShowEventForChapter chapter: chapter)
```

The method is called when a new chapter starts playing **Chapter**
```
func mkplayer(_ player: MKPlayer, showChapter chapter: Chapter)
```

The method is called when the interactive appears in a chapter **Chapter**
```
func mkplayer(_ player: MKPlayer, didAppearEventWithChapter chapter: Chapter)
```

## Video player error handling
To handle video player errors, you need to implement the following method

```
func mkplayer(_ player: MKPlayer, error: Error)
```

### Video playback states

- In case you need to access video playback states, you need to access **AVPlayer** located in **MKDefaultPlayerView**.
