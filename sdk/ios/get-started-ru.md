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
  pod 'MovikaSDK'
end

```

Замените YOUR_TARGET_NAME, перейдите в папку Podfile и выполните команду:

```
$ pod install
```

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

## 3. Создайте свой интерактивный плеер

1. Создайте UIView компонент MKInteractivePlayer

```
let player = MKInteractivePlayer(frame: view.frame)
self.view.addSubview(player)
```
   
2. Вставьте ссылку на данные (структура MKManifest) необходимые для воспроизведения фильма. Используйте MKURLManifestAsset

```
player.setManifestAsset(MKURLManifestAsset(url: URL))
```

3. Для начала воспроизведения вызовете у плеера метод play

```
player.play()
```

4. Отслеживайте состояние плеера используя MKPlayerDelegate
```
let player = MKInteractivePlayer(frame: view.frame)
player.delegate = self
```
