---
title: Документация Movika
description: Документация Movika SDK для web, iOS, Android
keywords: документация, movika, sdk, ios, android, web, интерактивное видео
sort: 0
---

# Документация Movika

## SDK

### Web Iframe
 
Интеграция Web SDK Movika на сайт осуществляется с помощью встраивания тега iframe в HTML разметку страницы.

 <iframe allowFullScreen src="https://movika.com/ru/player/movika-sdk-sample" allowFullScreen scrolling="no" frameborder="0">
 </iframe>

Пример тега **iframe**, отображающего интерактивный видеопроигрыватель размером 840x560 пикселей представлен ниже:

```
 <iframe style="width:840px; height:560px" allowFullScreen src="https://movika.com/ru/player/movika-sdk-sample">
 </iframe>
```

Параметры (атрибуты) iframe:

- **src** - содержит URL, указывающий на путь, содержащий интерактивный видеоконтент;
- **width** - задает ширину плеера проигрываемого видеоконтента;
- **height** - задает высоту плеера проигрываемого видеоконтента;
- **allowFullScreen** - разрешает или запрещает полноэкранное воспроизведение видео.

### Web SDK
Version 2.5

# Начало работы

## 1. Зарегистрируйте свое приложение в Movika Developer
Зарегистрируйте свое приложение в [Movika Developer](https://developer.movika.com) и используйте полученный ключ API. Для всех платформ (iOS, Android и Web) ключи создаются отдельно.

## 2. Добавьте ваш NPM-KEY
Добавьте файл .npmrc в корень проекта и замените ${NPM-KEY} на ваш

```
 _authToken=${NPM-KEY}
```

## 3. Скачайте SDK

```
 npm i @interactiveplatform/movika-player
```

## 4. Создайте плеер

```
 import React from 'react';
 import { movika } from '@interactiveplatform/movika-player'

 function App() {
 const videoRef = React.useRef(null)
 const videoContainerRef = React.useRef(null)

 React.useEffect(() => {
  const options = {
    ApiKey: &{ApiKey},
    manifest: 'url to manifest',
  }

  const mp = new movika.Player(videoRef.current, options)
  const co = new movika.ControlsOverlay(mp, videoContainerRef.current, videoRef.current)
  const interactive = new movika.Interactives(mp, options, videoRef.current)
 }, []);

 return (
      <div>
        <div ref={videoContainerRef}>
          <video ref={videoRef}/>
        </div>
      </div>
 )
 export default App
```

### Mobile SDK

Для добавления интерактивного плеера в свое мобильное приложение, воспользуйстель данной инструкцией
для платформы Android или iOS.

Чтобы использовать sdk вам так же понадобится получить API Key для ваших приложений. 

Зарегистрируйте свое приложение в [Movika Developer](https://developer.movika.com) и используйте полученный ключ API. Для всех платформ (iOS, Android и Web) ключи создаются отдельно.

*Для iframe API Key не требуется*

#### iOS SDK

##### Version 3.0.0-beta

Sdk integration [sample](https://github.com/movika/ios.sdk.sample.movika.com)
1. [Getting started](/sdk/ios-v3/get-started-ru.md)

#### Android SDK

0. [Начало работы](/sdk/android/getting-started-ru.md)
1. [Архитектура плеера](/sdk/android/player-arch-ru.md)
2. [События плеера](/sdk/android/player-events-ru.md)
3. [Конфигурация](/sdk/android/config-ru.md)
4. [Аудио-дорожки и субтитры](/sdk/android/audio-subtitles-ru.md)