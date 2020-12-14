---
title: События плеера
description: События плеера
keywords: События плеера
---

# События плеера

Для прослушки событий плеера, достаточно добавить необходимые слушатели  с помощью следующих методов:   

Для события, когда SDK является не зарегистрированным (неправильный ключ например)
```
fun addOnInvalidSdkListener(listener: OnInvalidSdkListener)
```

Для оповещения о начале интерактива
```
fun addOnInteractiveStartListener(listener: OnInteractiveStartListener)
```
Для оповещения о завершении интерактива
```
fun addOnInteractiveEndListener(listener: OnInteractiveEndListener)
```

Для события изменения текущей главы
```
fun addOnCurrentChapterUpdateListener(listener: OnCurrentChapterUpdateListener)
```

Для события изменения списка глав
```
fun addOnChapterListChangeListener(listener: OnChapterListChangeListener)
```

Для события обновления истории воспроизведения и данных взаимодействия пользователя с текущим интерактивным роликом
```
fun addOnWalkthroughHistoryChangeListener(listener: OnWalkthroughHistoryChangeListener)
```

Для оповещения готовности плеера к воспроизведению
```
fun addOnReadyListener(listener: OnReadyListener)
```
##### Некоторые слушатели устанавливаются путем изменения значения полей InteractivePlayerView:  
Метод, вызываемый во время ошибки воспроизведения плеера. Может быть полезен, если в конфигурации плеера
 isUseDefaultPlaybackErrorUi принимает значение false, например
```
var onPlaybackErrorListener: ((error: Throwable) -> Unit)?
```
Для оповещения об изменении состояния воспроизведения плеера (воспроизведение/пауза)
```
var playPauseListener: PlayPauseListener?
```
Для оповещения конца интерактивного ролика
```
var onGameEndListener: OnGameEndListener?
```
Для оповещения о достижении конца тупиковой главы
```
var onEndChapterEndListener: OnEndChapterEndListener?
```
Для оповещения начала воспроизведения интерактивного ролика
```
var onStartListener: OnStartListener?
```
Для оповещения изменения (например при выборе) текущей аудио-дорожки или субтитров
```
var trackSelectionListener: TrackSelectionListener?
```
