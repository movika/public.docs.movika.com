## Получение данных для воспроизведения
Для воспроизведения необходимо иметь экземпляр объекта **MovieBundle** или строку, описывающую манифест в формате json. 
Также, при необходимости можно **создать** данный экземпляры самому не прибегая к загрузке. 
Для получения **MovieBundle** в SDK предусмотрено стандартное решение в виде реализации интерфейса 
**MovieBundleLoader** **AsyncMovieBundleLoader**. Для загрузки можно воспользоваться следующими методами:  
```
fun load(movie: Movie, listener: ((status: ProgressStatus) -> Unit)? = null)

fun load(manifestUrl: String, listener: ((status: ProgressStatus) -> Unit)? = null)
```

где Movie и ProgressStatus имеют следующий вид:
```
@Parcelize
data class Movie(
    val id: String,
    val manifestUrl: String
) : Parcelable

data class ProgressStatus(
    val current: Long = 0,
    val total: Long,
    val isComplete: Boolean = false,
    val data: MovieBundle? = null,
    val error: Throwable? = null
)
```

Если имеется уже готовая строка с манифестом, то можно воспользоваться **DefaultStringToGameManifestConverter**

```
val jsonManifes = ... // some game manifest
val gameId = "1"

val gameManifest: GameManifest = DefaultStringToGameManifestConverter().convert(jsonManifest, gameId)

// Затем необходимо создать MovieBundle. Он необходим для воспроизведения интерактивного контента InteractivePlayerView

val movieBundle = MovieBundle(Movie(gameId, ""), gameManifest)

```