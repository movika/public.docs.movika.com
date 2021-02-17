---
title: Player configuration
description: Player configuration
keywords: Player configuration
sort: 3
---

# Player configuration

The basic configuration is set using the ** Config ** object, the transmission of which depends on the way the player is started
(using ** InteractivePlayerViewRunner **, or directly with the run(..) method of the ** InteractivePlayerView ** class)
Most of the parameters are directly related to player customization. Player customization will be described later.
Class fields of ** Config **:

- isUseDefaultPlayPauseController: Boolean - indicates whether the standard
  pause / play control interface should be used. If false, it is required to implement the pause button by the developer himself,
  this will be useful when implementing a custom pause menu. By default, this field is true.
- isUseDefaultPlaybackErrorUi: Boolean - indicates whether the standard error interface
  playback should be used. By default is true.
- isSeekEnable: Boolean - indicates whether user has the ability to fast-forward by double tap or not.
  By default is true.
- isDebugMode: Boolean - indicates whether debug mode is enabled in the form of debug menu during playback.
  By default is false.
- isLoop: Boolean - indicates whether interactive movie should be looped or not. If true, after the last chapter ends
  the first chapter would be played. By default is false.
- isCacheStartPartsOfNextChapters: Boolean - indicates whether initial fragments of following
  possible chapters should be cached or not. By default is true.
- isLocalVideoContent: Boolean - This parameter is optional. Serves for playback optimization. 
  Indicates the type of content that being used. If true - local content on device would be used,
  if false - there is no content on device (the content is accessed via https protocol).
  By default is false.
- isShowTimeBar: Boolean - indicates whether to show progress bar of the current chapter or not. By default
  is true.
