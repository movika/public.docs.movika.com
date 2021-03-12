---
title: Пользовательский плеер
description: Пользовательский плеер
keywords: Пользовательский плеер
sort: 5
---

# Пользовательский плеер

### MKPlayer

Движок интерактивного видео - определяет последовательность воспроизведения видео, исходя из действия пользоватлей. 

Для того чтобы данный компонет мог отображать видео неообходмио подключить к классу реализацию MKPlayerView. (AVPlayerView реализация по умолчанию)

```
mkplayer.playerView = playerView
```

### MKPlayerView
Реализайте данный протокол для своего любимого плеера (AVPlayer / IJKplayer / Other...) или используйте готовый класс AVPlayerView и подключите его к движку MKPlayer 

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

