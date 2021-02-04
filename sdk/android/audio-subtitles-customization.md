---
title: Кастомизация элементов интерфейса смены аудио-дорожек и субтитров
description: Кастомизация элементов интерфейса смены аудио-дорожек и субтитров
keywords: Кастомизация элементов интерфейса смены аудио-дорожек и субтитров
sort: 7
---

# Кастомизация элементов интерфейса смены аудиодорожек и субтитров

Для кастомизации в конфигурации плеера необходимо:

- выполнить необходимые шаги, которые описаны в разделе кастомизации интерфейса паузы/воспроизведения: [ссылка](/sdk/android/06-play-pause-customization.md)
- реализовать свой пользовательский интерфейс управления и разместить в необходимом месте
- осуществить взаимодействие вашего интерфейса с плеером посредством изменения полей **audio** и **subtitles** экземпляра класса, реализующего
  MediaOptionsControllerObservable, или, при необходимости, изменения поля **isSubtitlesEnabled** у того же экземпляра
- для отслеживания текущих установленных аудио-дорожки и субтитров с целью актуализации вашего интерфейса, подписаться на
  соответствующие события в MediaOptionsControllerObservable.

Экземпляр класса реализующий **MediaOptionsControllerObservable** хранится в поле **mediaOptionsControllerObservable**
класса InteractivePlayerView.
Данный экземпляр следует использовать только после готовности плеера к воспроизведению. Более подробную информацию о
событиях плеера можно найти по ссылке: [ссылка](/sdk/android/04-player-events.md).  
Для получения списка доступных аудиодорожек и субтитров необходимо у экземпляра класса, реализующего
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
