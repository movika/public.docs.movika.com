---
title: Getting started
description: Getting started
keywords: Getting started
sort: 0
---

# Начало работы

###  Пример проекта на [GitHub](https://github.com/movika/android.sdk.sample.movika.com)

## Получите доступ

Чтобы получить Android **ApiKey** и задать **AppName** для SDK перейдите на https://developer.movika.com/ и создайте приложение Android

## Добавьте зависимости в Gradle

Подключите наш репозиторий

```
allprojects {
    repositories {
        maven {
            url "https://nexus.movika.net/repository/android/"
        }
    }
}
```

Затем подключите зависимости

```
implementation "com.movika.android:interactive-sdk:3.2.2"
```
Убедитесь, что минимальная версия Android SDK не ниже 23
```
...
android {
    ...
    defaultConfig {
        ...
        minSdkVersion 23
        ...
    }
    ...
}
...
```
## Добавьте правила в ProGuard
```
-keep class com.movika.player.sdk** { *; }
```
## Добавьте ваш ApiKey, AppName, AppVersion в классе, который наследуется от Application()

```
class App : Application() {
	...
    override fun onCreate() {
        super.onCreate()
        MovikaSdk.setup(InitConfig(apiKey, appName, appVersion), this)
    }
    ...
}
```
## Добавьте необходимые разрешения в манифест приложения

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    ...>

    <uses-permission android:name="android.permission.INTERNET" />
    ...

</manifest>
```

## Создайте плеер

Вы можете создать экземпляр вручную или получить из вашей разметки

```
val interactivePlayer = SimpleInteractivePlayer(
	context = context,
	config = Config(),
	initBundleState = savedInstanceState?.getBundle(bundleKey), // опционально
)
// Добавьте плеер в вашу разметку
yourViewGroup.addView(interactivePlayer.view)
```

### Далее привяжите плеер к жизненному циклу Activity/Fragment

```
lifecycle.addObserver(interactivePlayer)
```

### Затем добавьте в onSaveInstanceState вашего Activity или Fragment для сохранения состояния

```
override fun onSaveInstanceState(outState: Bundle) {
    super.onSaveInstanceState(outState)
    val bundle = interactivePlayer.onSaveInstanceState()
    outState.putBundle(bundleKey, bundle)
}
```

## Загрузка и воспроизведение

### Воспроизведение _интерактивного_ видео по ссылке
```
/* Замените ссылку демонстрационного манифеста на свою */
val url = "https://asazin-cache.cdnvideo.ru/asazin/movika/stage/users/00/movie/2/manifest-v3.json"
interactivePlayer.run(ManifestURLAssets(url))
```

### Воспроизведение _обычного_ видео по ссылке
```
/* Замените ссылку демонстрационного видео на свою */
val url = "https://asazin-cache.cdnvideo.ru/asazin/movika/stage/users/00/movie/2/5_360.mp4"
interactivePlayer.run(VideoURLAssets(url))
```

### Воспроизведение с использованием готового объекта интерактивного видео (манифеста)
```
val manifest: Manifest = getYourSomeManifest()
interactivePlayer.run(PreparedManifestAssets(manifest))
```

## Обработка ошибок

```
interactivePlayer.errorObservable.addObserver { error ->
    val msg = when (error) {
        is AssetsLoadException -> "Manifest load error!"
        is InvalidApiKeyException -> "Invalid Api key!"
        is ExpiredApiKeyException -> "Expired Api key!"
        is IncompatibleManifestVersionException -> "Incompatible manifest version ${error.receivedVersion}"
        else -> error::class.simpleName
    }
    Toast.makeText(this, msg, Toast.LENGTH_LONG).show()
}
```

Обработка ошибок **видео** плеера описана в разделе "**События плеера**"