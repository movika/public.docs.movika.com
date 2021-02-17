---
title: Customize pause and play
description: Customize pause and play
keywords: Customize pause and play
sort: 6
---

# Customize pause and play

Attention! The standard implementation of the pause interface contains a menu for selecting audio tracks and subtitles, if any exist.
When changing the interface to a custom one, you will optionally need to implement the user interface
for audio tracks and subtitles selection. This article contains a description of customizing audio tracks and subtitles:
[link] (/sdk/android/audio-subtitles-customization.md).
For customization using player configuration you need to:

- set ** isUseDefaultPlayPauseController ** value to ** false **.
- implement your user interface and place it in the required place
- implement the interaction of your interface with the player by calling the play() and pause() methods
- to track the states of the player's playback in order to update your interface, subscribe to
  relevant events by accessing the ** playPauseObservable ** field of the ** InteractivePlayerView ** class