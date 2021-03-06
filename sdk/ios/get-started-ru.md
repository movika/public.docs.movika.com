---
title: Начало работы
description: Начало работы
keywords: Начало работы
sort: 0
---

# Начало работы

## 1. Добавьте sdk через pod

```
# Podfile
use_frameworks!

target 'YOUR_TARGET_NAME' do
  use_frameworks!
  pod 'MovikaSDK', :git => 'https://bitbucket.org/interactiveplatform/ios.sdk.movika.com.git'
end

```


Зарегистрируйте свое приложение в [Movika Developer] (https://developer.movika.com) и используйте полученный ключ API. Для всех платформ (iOS, Android и Web) ключи создаются отдельно.

Замените YOUR_TARGET_NAME, перейдите в папку Podfile и выполните команду:

```
$ pod install
```

## 2. Добавьте ваш ApiKey

Для получения ключа API_KEY напишите на email sdk@movika.com либо support@movika.com.

В классе AppDelegate в методе application didFinishLaunchingWithOptions

Импортируйте фреймворк

```
import MovikaSDK
```

Добавьте Movika.shared.apiKey = API_KEY

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.
        Movika.shared.apiKey = API_KEY
        return true
    }
```

## 3. Создайте свой плеер

1. Создайте новый класс view controller и унаследйте его от класса MovikaPlayerViewController
2. Загрузите данные (стуктура GameManifest) необходимые для воспроизведения фильма, используя DefaultGameManifestDownloader метод load

```
let downloader = DefaultGameManifestDownloader(downloadManifestDelegate: self)
downloader.load(movie: Movie(id: movieId, manifestUrl: movieManifestLink), downloadWasEnded: { manifest, error  in
    if let error = error {
        print("Error loading manifeist \(error.localizedDescription)")
    } else {
        self.manifest = manifest
        print("Manifest ready for playing")
    }
})
```

3. Когда GameManifest будет загружен передайте его плееру вызвав метод класса контроллера setup. (Ссылка на тестовый манифест https://asazin-cache.cdnvideo.ru/asazin/tutorial/json/manifest.json)

```
 self.setup(playerRepository: DefaultPlayerRepository(),
                   manifest: manifest,
                   startFromSavePoint: false,
                   customEventViewFactory: nil)
 self.mkplayer.play()
```

4. Когда плеер завершит воспроизведения фильма будет вызван метод контроллера onMovieEnded, либо onMovieClose если пользователь нажмет на кнопку завершить воспроизведение

```
func onMovieClose() {
    self.dismiss(animated: true, completion:nil)
}

func onMovieEnded(history: InteractionHistory) {
    self.dismiss(animated: true, completion:nil)
}
```

Если вы хотите добавить плеер без наслеодования от MovikaPlayerViewController. Просто используйте UIView компонент MKEasyPlayer.  Для большего котроля над плеером используйте MKPlayer. В обоих UIView для запуска проекта используйте методы setup() и последующий play()
