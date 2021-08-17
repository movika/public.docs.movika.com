---
title: Документация Movika
description: Документация Movika SDK для web, iOS, Android
keywords: документация, movika, sdk, ios, android, web, интерактивное видео
sort: 0
---

# Документация Movika

## SDK

### Web
 
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

### Mobile SDK

Для добавления интерактивного плеера в свое мобильное приложение, воспользуйстель данной инструкцией
для платформы Android или iOS.

Чтобы использовать sdk вам так же понадобится получить API Key для ваших приложений. 

Зарегистрируйте свое приложение в [Movika Developer] (https://developer.movika.com) и используйте полученный ключ API. Для всех платформ (iOS, Android и Web) ключи создаются отдельно.

*Для iframe API Key не требуется*

#### iOS SDK

##### Version 3.0.0-beta

Sdk integration [sample](https://github.com/movika/ios.sdk.sample.movika.com)
1. [Getting started](/sdk/ios-v3/get-started-ru.md)

#### Android SDK

0. [Начало работы](/sdk/android/getting-started-ru.md)
1. [Получение данных для воспроизведения](/sdk/android/getting-movie-bundle-ru.md)
2. [Воспроизведение](/sdk/android/run-interactiveplayerview-ru.md)
3. [Конфигурация плеера](/sdk/android/config-ru.md)
4. [События плеера](/sdk/android/player-events-ru.md)
5. [Кастомизация плеера](/sdk/android/introduce-to-player-customization-ru.md)
6. [Кастомизация элементов интерфейса паузы и воспроизведение](/sdk/android/play-pause-customization-ru.md)
7. [Кастомизация элементов интерфейса смены аудио-дорожек и субтитров](/sdk/android/audio-subtitles-customization-ru.md)
8. [Кастомизация интерактивов](/sdk/android/interactive-customization-ru.md)
