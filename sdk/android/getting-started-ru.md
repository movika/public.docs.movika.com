---
title: Начало работы
description: Начало работы
keywords: Начало работы
sort: 0
---

# Начало работы

## Получите доступ

Для получения доступа к SDK необходимо написать на sdk@movika.com или на support@movika.com. После одобрения, вам будет выдана связка **username** **password** для получения
доступа к библиотеке, **apiKey** и **appName** для функционирования SDK.

## Добавьте зависимости в Gradle

После получения доступа, в файле build.gradle уровня модуля необходимо добавить репозиторий, заменив значения полей username и password
на полученные

```
allprojects {
    repositories {
        maven {
            credentials {
                username "your_username"
                password "your_password"
            }
            url "https://nexus.movika.com/repository/android/"
        }
    }
}
```

Затем подключите зависимость

```
implementation("com.movika:interactive-sdk:2.0.0")
```

## Добавьте ваш ApiKey, AppName, AppVersion в классе, который наследуется от Application()

```
class App : Application() {
    override fun onCreate() {
        super.onCreate()
        MovikaSdk.setup(InitConfig(apiKey, appName, appVersion))
    }
}
```

## Создайте плеер

Вы можете создать экземпляр вручную или получить из вашей разметки

#### Вручную

```
val interactivePlayerView = InteractivePlayerView(context)
// Добавьте плеер в вашу разметку
yourViewGroup.addView(interactivePlayerView)
```

#### Из разметки

```
val interactivePlayerView = findViewById<InteractivePlayerView>(R.id.your_id)
```

### Далее привяжите плеер к жизненному циклу Activity/Fragment

```
lifecycle.addObserver(interactivePlayerView)
```

### Затем добавьте в onSaveInstanceState вашего Activity или Fragment для сохранения состояния

```
override fun onSaveInstanceState(outState: Bundle) {
    super.onSaveInstanceState(outState)
    interactivePlayerView.onSaveInstanceState(outState)
}
```

## Загрузка и воспроизведение

Загрузите манифест. В данном примере для загрузки воспользуемся **AsyncMovieBundleLoader**, который является
реализацией **MovieBundleLoader**. Примечание: если имеется локально готовый манифест в формате json, то можно воспользоваться
**DefaultStringToGameManifestConverter**, который является реализацией **StringToGameManifestConverter**

```
val url = "TODO URL"
AsyncMovieBundleLoader().load(url) { status ->
    if (status.isComplete && status.error != null) {
        val movieBundle = status.data!!
        interactivePlayerView.run(
            movieBundle,
            Config(),
            // Опциональный аргумент. Необходим, для востановления состояния после пересоздания Activity/Fragment
            savedInstanceState
        )
    }
}

```

Вы можете воспользоваться примером проекта: [ссылка](https://github.com/movika/android.sdk.sample.movika.com)
