## События плеера
Для прослушивания событий плеера, достаточно добавить необходимые слушатели. Для добавления, необходимо 
обращаться к специальным открытым полям класса InteractivePlayerView. Данные поля являются реализацией 
**AbstractObservable<T>**, где T это тип слушателя.
```
interface AbstractObservable<T> {

    fun addObserver(observer: T)

    fun removeObserver(observer: T)
}
```

Для события, когда SDK является не зарегистрированным (неправильный ключ например)
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

Для оповещения готовности плеера к воспроизведению
```
val readyObservable: AbstractObservable<OnReadyListener>
```
Для оповещения об ошибки воспроизведения плеера. Может быть полезен, если в конфигурации плеера
 isUseDefaultPlaybackErrorUi принимает значение false, например
```
val playbackErrorObservable: AbstractObservable<OnPlaybackErrorListener>
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
val endChapterEndObservable: AbstractObservable<OnEndChapterEndListener>
```
Для оповещения начала воспроизведения интерактивного ролика
```
val startObservable: AbstractObservable<OnStartListener>
```
[**Временно не поддерживается**] Для оповещения изменения (например при выборе) текущей аудио-дорожки 
или субтитров
```
val trackSelectionObservable: AbstractObservable<TrackSelectionListener>
```
