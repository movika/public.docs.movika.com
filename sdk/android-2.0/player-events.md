---
title: Player Events
description: Player events
keywords: Player events
sort: 4 
---

# Player events

In order to listen to the player's events, just add the necessary listeners. To add them, you will need to
use special public fields of the InteractivePlayerView class. These fields are implementation of
**AbstractObservable <T>**, where T is the listener type.

```
interface AbstractObservable <T> {

    fun addObserver (observer: T)

    fun removeObserver (observer: T)
}
```

For events when SDK is unregistered (wrong key)

```
val invalidSdkObservable: AbstractObservable <OnInvalidSdkListener>
```

To notify about the beginning of the interactive

```
val interactiveStartObservable: AbstractObservable <OnInteractiveStartListener>
```

To notify about the end of the interactive

```
val interactiveEndObservable: AbstractObservable <OnInteractiveEndListener>
```

For the current chapter change event

```
val currentChapterUpdateObservable: AbstractObservable <OnCurrentChapterUpdateListener>
```

For chapter list change event

```
val chapterListChangeObservable: AbstractObservable <OnChapterListChangeListener>
```

For the event of updating the playback history and data about user interaction with the current interactive video

```
val walkthroughHistoryChangeObservable: AbstractObservable <OnWalkthroughHistoryChangeListener>
```

To notify the player's readiness for playback

```
val readyObservable: AbstractObservable <OnReadyListener>
```

To notify about a player playback error. It can be useful if in the player's configuration
isUseDefaultPlaybackErrorUi is false

```
val playbackErrorObservable: AbstractObservable <OnPlaybackErrorListener>
```

To notify about a change in the player's playback status (play / pause)

```
val playPauseObservable: AbstractObservable <PlayPauseListener>
```

To notify about the end of an interactive video

```
val gameEndObservable: AbstractObservable <OnGameEndListener>
```

To notify about reaching of the end of a last chapter

```
val endChapterEndObservable: AbstractObservable <OnEndChapterEndListener>
```

To notify about the start of playback of an interactive video

```
val startObservable: AbstractObservable <OnStartListener>
```

### Audio track and subtitle change events

To track such events, you need to refer to the field

```
val mediaOptionsControllerObservable: MediaOptionsControllerObservable?
```

Attention! The value of this field is available only after the player is ready
to playback. To watch for readiness of the player, refer to the field

```
val readyObservable: AbstractObservable <OnReadyListener>
```

Each time the **run** method is called, this field will be overwritten.
The **MediaOptionsControllerObservable** interface is described in more detail in this article: [link] (/sdk/android/audio-subtitles-customization.md).
