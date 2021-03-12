---
title: Custom player
description: Custom player
keywords: Custom player
sort: 5
---

# Custom player

### MKPlayer

Interactive video engine is a sequence of video playback using user actions.

In order for this component to be able to display video, it must be connected to the class to use MKPlayerView. (Default AVPlayerView implementation)

```
mkplayer.playerView = playerView
```

### MKPlayerView
Implement this protocol for your favorite player (AVPlayer / IJKplayer / Other ...) or use the ready-made AVPlayerView class and connect it to the MKPlayer engine

```
public protocol MKPlayerView {
  var delegate: MKPlayerViewDelegate? { get set }
  func play()
  func pause()
  func advanceToNextItem()
  func seek(position: Double)
  func insert(playerItem: PlayerItem,
              startTimePosition: Double,
              completionHandler: @escaping () -> Void)
  func preload(items: [PlayerItem])
  func cancelLoading()
  func removeNextVideos() -> Int
  func removeAll() -> Int
  func currentTime() -> Double
  func currentItemDuration() -> Double
  func setVideoGravity(videoGravity: VideoGravity)
}
```