---
title: Getting data for playback
description: Getting data for playback
keywords: Getting data for playback
sort: 1 
---

# Getting data for playback

In order to play content, you must have an instance of a **MovieBundle** object or a string describing the manifest in .json format.
Also, if necessary, you can **create** this instance yourself without downloading from other places.
To get the **MovieBundle** instance, the SDK provides a standard solution using a **MovieBundleLoader** interface implementation
**AsyncMovieBundleLoader**. You can use following methods for downloading:

```
fun load(movie: Movie, listener: ((status: ProgressStatus) -> Unit)? = null)

fun load(manifestUrl: String, listener: ((status: ProgressStatus) -> Unit)? = null)
```

where Movie and ProgressStatus look like this:

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

If you have manifest in String format you can use **DefaultStringToGameManifestConverter**

```
val jsonManifest = ... // some game manifest
val gameId = "1"

val gameManifest: GameManifest = DefaultStringToGameManifestConverter().convert(jsonManifest, gameId)

// Then you should create MovieBundle. It is required for playing content in InteractivePlayerView

val movieBundle = MovieBundle(Movie(gameId, ""), gameManifest)

```
