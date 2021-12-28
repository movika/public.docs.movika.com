---
title: События плеера
description: События плеера
keywords: События плеера
sort: 2 
---

# События плеера

Для прослушивания событий плеера, достаточно добавить необходимые слушатели. Для добавления, необходимо
обращаться к специальным открытым полям  интерфейса InteractivePlayer, который реализуют SimpleInteractivePlayer и CoreInteractivePlayer. Данные поля являются реализацией
**AbstractObservable<T>**, где T это тип слушателя.

```
interface AbstractObservable<T> {

    fun addObserver(observer: T)

    fun removeObserver(observer: T)
}
```

Для события, когда SDK является незарегистрированным (неправильный ключ)

```
val invalidSdkObservable: AbstractObservable<OnInvalidSdkListener>
```

Для оповещения о начале интерактива

```
val interactiveStartObservable: AbstractObservable<OnInteractiveStartListener>
```

Для оповещения о завершении интерактива

```
val interactiveEndObservable: AbstractObservable<OnInteractiveEndListener>
```

Для события изменения текущей главы

```
val currentChapterUpdateObservable: AbstractObservable<OnCurrentChapterUpdateListener>
```

Для события изменения списка глав

```
val chapterListChangeObservable: AbstractObservable<OnChapterListChangeListener>
```

Для события обновления истории воспроизведения и данных взаимодействия пользователя с текущим интерактивным роликом

```
val walkthroughHistoryChangeObservable: AbstractObservable<OnWalkthroughHistoryChangeListener>
```

Для оповещения об изменении состояния воспроизведения плеера (воспроизведение/пауза)

```
val playPauseObservable: AbstractObservable<PlayPauseListener>
```

Для оповещения конца интерактивного ролика

```
val gameEndObservable: AbstractObservable<OnGameEndListener>
```

Для оповещения о достижении конца тупиковой главы

```
val lastChapterEndObservable: AbstractObservable<OnEndChapterEndListener>
```

Для оповещения начала воспроизведения интерактивного ролика

```
val startObservable: AbstractObservable<OnStartListener>
```

## 	Обработка ошибок видеоплеера
Для обработки ошибок видеоплеера понадобится реализация интерфейса **PlayerErrorController**.
**PlayerErrorController** имеет следующие методы:

```
/* Попробовать возобновить воспроизведение после возникшей ошибки */
fun retryOnError()

/* Добавить колбек для ошибок */
fun addPlayerErrorListener(listener: PlayerErrorListener)

/* Убрать колбек для ошибок */
fun removePlayerErrorListener(listener: PlayerErrorListener)

```
Если в вашем проекте используется **SimpleInteractivePlayer** или **DefaultVideoPlayer**, то для получения **PlayerErrorController** необходимо:

- При использовании **SimpleInteractivePlayer**, он уже является реализвацией **PlayerErrorController**
- При использовании **DefaultVideoPlayer** необходимо обратиться к набору **PlayerComponents**
``` videoPlayer.playerComponents.playerErrorController```

## Обработка состояния воспроизведения видео
Для обработки состояния воспроизведения видео необходимо получить реализацию PlaybackObservable.
Если в вашем проекте используется **SimpleInteractivePlayer** или **DefaultVideoPlayer**, то для получения **PlayerErrorController** необходимо:
- При использовании **SimpleInteractivePlayer**, обратиться к полю **playbackObservable**
- При использовании **DefaultVideoPlayer** необходимо обратиться к набору **PlayerComponents**
  ``` videoPlayer.playerComponents.playbackController```

### Состояния воспроизведения видео:
| Тип | Описание |
|---|---|
|IDLE|Плеер простаивает. Нет видео в очереди|
|READY|Плеер готов к воспроизведению. Фактическое воспроизведение в данном случае зависит от того, находится ли плеер сейчас на паузе|
|BUFFERING|Происходит буфферизация/подгрузка видео. В данный момент плеер не готов к воспроизведению|
|ENDED|Текущее видео закончилось. После этого состояния начинает воспроизводиться следующее видео/глава при наличии|
