## Получите доступ
Для получения доступа к SDK необходимо написать на [salavat@movika.com](salavat@movika.com) или на
[fanis@movika.com](fanis@movika.com). После одобрения, вам будет выдана связка **username** **password** для получения
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
implementation("com.movika:interactive-sdk:1.6.5")
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
```
val interactivePlayerView = InteractivePlayerView(context)
lifecycle.addObserver(interactivePlayerView)
```
### Добавьте плеер в вашу разметку
```
yourViewGroup.addView(interactivePlayerView)
```

## Загрузка и воспроизведения

Загрузите манифест. В данном примере для загрузки воспользуемся **AsyncMovieBundleLoader**, который является
реализацией **MovieBundleLoader**. Примечание: если имеется готовый манифест, то можно воспользоваться
**DefaultStringToGameManifestConverter**, который является реализацией **StringToGameManifestConverter**   
Затем запустите с помощью вспомогательного класса **SimpleInteractivePlayerViewRunner**
```
val url = "TODO URL"
AsyncMovieBundleLoader().load(url) { status ->
    if (status.isComplete && status.error != null) {
        val movieBundle = status.data!!
        
        SimpleInteractivePlayerViewRunner(context).run(
            interactivePlayerView,
            movieBundle,
            Config()
        )
    }
}

```