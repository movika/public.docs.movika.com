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
            url "https://nexus.movika.com/repository/android/"
        }
    }
}
```

Затем подключите зависимости

```
implementation "com.movika.android:interactive-sdk:3.0.0-beta24"
implementation "org.jetbrains.kotlinx:kotlinx-coroutines-core:1.4.3"
implementation "org.jetbrains.kotlinx:kotlinx-coroutines-android:1.4.3"
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
	scope = lifecycleScope, // опционально
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

### Воспроизведение по ссылке
```
/* Замените ссылку демонстрационного манифеста на свою */
val manifestUrl = "https://asazin-cache.cdnvideo.ru/asazin/movika/stage/users/00/movie/2/manifest-v3.json"
interactivePlayer.runByUrl(
	url = manifestUrl,
	onSuccess = { /* Handle success load */ },
	onFailure = { /* Handle failure load */ }
)

```
### Воспроизведение с использованием готового объекта
```
val manifest: Manifest = getYourSomeManifest()
interactivePlayer.run(manifest)
```
