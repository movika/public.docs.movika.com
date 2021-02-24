---
title: Customization of interface elements for switching audio tracks and subtitles
description: Customization of interface elements for switching audio tracks and subtitles
keywords: Customization of interface elements for switching audio tracks and subtitles
sort: 7
---

# Customization of interface elements for switching audio tracks and subtitles

For this customization in the player configuration you need to:

- complete the necessary steps, which are described in the section on customizing the pause / play interface: [link] (/sdk/android/play-pause-customization.md)
- implement your user interface and place it in the required place
- implement the interaction of your interface with the player by changing the **audio** and **subtitles** fields of the instance of the class that implements
  MediaOptionsControllerObservable, or, if necessary, changing the **isSubtitlesEnabled** field on the same instance
- to keep track of the currently used audio tracks and subtitles in order to update your interface, subscribe to
  the corresponding events in the MediaOptionsControllerObservable.

An instance of the class implementing **MediaOptionsControllerObservable** is stored in the **mediaOptionsControllerObservable** field of
the InteractivePlayerView class.
This copy should be used only after the player is ready for playback. More information on
player events can be found at: [link] (/sdk/android/player-events.md).
To get a list of available audio tracks and subtitles, you need to call availableAudio () and availableSubtitles() methods of the class that implements
MediaOptionsControllerObservable, respectively.

#### List of available fields and methods of **MediaOptionsControllerObservable**

```
// Get and change language of the audio.
var audio: Locale

// Get and change language of the subtitles.
var subtitles: Locale

// Get and change current display state of the subtitles.
var isSubtitlesEnabled: Boolean

// Returns a list of available languages for an audio.
fun availableAudio(): List<Locale>

// Returns a list of available subtitle languages.
fun availableSubtitles(): List<Locale>

// Tracking changes in the language of an audio.
fun addOnAudioChangeListener(listener: OnAudioChangeListener)
fun removeOnAudioChangeListener(listener: OnAudioChangeListener)

// Tracking subtitle language changes.
fun addOnSubtitlesChangeListener(listener: OnSubtitlesChangeListener)
fun removeOnSubtitlesChangeListener(listener: OnSubtitlesChangeListener)

// Track changes in the list of available audio track languages.
fun addOnAvailableAudioChangeListener(listener: OnAvailableAudioChangeListener)
fun removeOnAvailableAudioChangeListener(listener: OnAvailableAudioChangeListener)

// Tracking changes in the list of available subtitle languages.
fun addOnAvailableSubtitlesChangeListener(listener: OnAvailableSubtitlesChangeListener)
fun removeOnAvailableSubtitlesChangeListener(listener: OnAvailableSubtitlesChangeListener)

// Tracking subtitle display state changes.
fun addOnSubtitlesEnabledChangeListener(listener: OnSubtitlesEnabledChangeListener)
fun removeOnSubtitlesEnabledChangeListener(listener: OnSubtitlesEnabledChangeListener)
```
