---
title: Audio tracks and subtitles
description: Audio tracks and subtitles
keywords: Audio tracks and subtitles
sort: 4
---

# Аудиодорожки и субтитры
В стандартном видеоплеере ExoVideoPlayer и SimpleInteractivePlayer предусмотреный аудиодорожки и субтитры.
Для взаимодействия с аудиодорожками и субтитрами необходимо получить экземпляр MediaOptionsController

Если используется SimpleInteractivePlayer:
```
val controller = simpleInteractivePlayer.mediaOptionsController
```
Если используется ExoVideoPlayer:
```
val controller = exoVideoPlayer.mediaOptionsController
```

Для получения списка доступных аудиодорожек и субтитров текущего видео необходимо у экземпляра класса, реализующего
MediaOptionsControllerObservable, вызвать методы availableAudio() и availableSubtitles() соответственно.

#### Список доступных полей и методов **MediaOptionsControllerObservable**

```
// Получение и изменение текущего языка аудиодорожки.
var audio: Locale

// Получение и изменение текущего языка субтитров.
var subtitles: Locale

// Получение и изменение текущего состояния отображения субтитров.
var isSubtitlesEnabled: Boolean

// Возвращает список доступных языков аудиодорожки.
fun availableAudio(): List<Locale>

// Возвращает список доступных языков субтитров.
fun availableSubtitles(): List<Locale>

// Отслеживание изменений языка аудиодорожки.
fun addOnAudioChangeListener(listener: OnAudioChangeListener)
fun removeOnAudioChangeListener(listener: OnAudioChangeListener)

// Отслеживание изменений языка субтитров.
fun addOnSubtitlesChangeListener(listener: OnSubtitlesChangeListener)
fun removeOnSubtitlesChangeListener(listener: OnSubtitlesChangeListener)

// Отслеживание изменений списка доступных языков аудиодорожки.
fun addOnAvailableAudioChangeListener(listener: OnAvailableAudioChangeListener)
fun removeOnAvailableAudioChangeListener(listener: OnAvailableAudioChangeListener)

// Отслеживание изменений списка доступных языков субтитров.
fun addOnAvailableSubtitlesChangeListener(listener: OnAvailableSubtitlesChangeListener)
fun removeOnAvailableSubtitlesChangeListener(listener: OnAvailableSubtitlesChangeListener)

// Отслеживание изменений состояния отображения субтитров.
fun addOnSubtitlesEnabledChangeListener(listener: OnSubtitlesEnabledChangeListener)
fun removeOnSubtitlesEnabledChangeListener(listener: OnSubtitlesEnabledChangeListener)
```
