---
title: Воспроизведение
description: Воспроизведение
keywords: Воспроизведение
---

# Воспроизведение

Для воспроизведения необходимо воспользоваться **SimpleInteractivePlayerViewRunner**
реализацией интерфейса **InteractivePlayerViewRunner**   
Сам интерфейс выглядит так:
```
interface InteractivePlayerViewRunner {
    fun run(
        interactivePlayerView: InteractivePlayerView,
        movieBundle: MovieBundle,
        config: Config = Config(),
        savedState: Bundle? = null
    )

    @Throws(IllegalArgumentException::class)
    fun runByRawData(
        interactivePlayerView: InteractivePlayerView,
        manifest: String,
        gameId: String,
        config: Config = Config(),
        savedState: Bundle? = null
    )
}
```
Метод **run**  предназначен для запуска при наличии MovieBundle.  
Метод **runByRawData** предназначен для запуска манифеста в формате json.