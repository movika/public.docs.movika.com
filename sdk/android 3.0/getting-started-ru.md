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
implementation("com.movika.android:interactive-sdk:$latest")
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

## Создайте плеер

Вы можете создать экземпляр вручную или получить из вашей разметки

```
val interactivePlayer = SimpleInteractivePlayer(
	context = context,
	config = Config(),
	scope = lifecycleScope, // опционально
	initState = savedInstanceState?.getBundle(bundleKey), // опционально
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
val manifestUrl = "https://YOUR_MANIFEST_URL"
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

Вы можете воспользоваться примером проекта: [ссылка](https://github.com/movika/android.sdk.sample.movika.com)
