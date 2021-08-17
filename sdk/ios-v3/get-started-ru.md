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

Замените YOUR_TARGET_NAME, перейдите в папку Podfile и выполните команду:

```
$ pod install
```

---
**NOTE**

Для получения доступа к репозиторию SDK https://bitbucket.org/interactiveplatform/ios.sdk.movika.com.git необходимо написать на support@movika.com.

---

## 2. Добавьте ваш ApiKey

В классе AppDelegate импортируйте фреймворк

```
import MovikaSDK
```

Зарегистрируйте свое приложение в [Movika Developer] (https://developer.movika.com) скопируйте полученный ключ API. Вставьте ключ в методе application didFinishLaunchingWithOptions

```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.
        Movika.shared.apiKey = API_KEY
        return true
    }
```
---
**NOTE**
Для разных платформ (iOS, Android и Web) ключи создаются отдельно.
---

## 3. Создайте свой интерактивный плеер

1. Создайте UIView компонент MKInteractivePlayer

```
let player = MKInteractivePlayer(frame: view.frame)
self.view.addSubview(player)
```
   
2. Вставьте ссылку на данные (структура MKManifest) необходимые для воспроизведения фильма, используя MKManifestAsset

```
player.setManifestAsset(MKURLManifestAsset(url: URL))
```

3. Для начала воспроизведения вызовете у плеера метод play

```
player.play()
```

4. Отслуживайте состояние плеера используя MKPlayerDelegate
```
let player = MKInteractivePlayer(frame: view.frame)
player.delegate = self
```