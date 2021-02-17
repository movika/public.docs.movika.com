---
title: Документация Movika
description: Документация Movika SDK для web, iOS, Android
keywords: документация, movika, sdk, ios, android, web, интерактивное видео
sort: 0
---

# Документация Movika
Язык: [English](README.md), [Русский](README.ru.md)
## SDK

### Web

Интеграция Web SDK Movika на сайт осуществляется с помощью встраивания тега iframe в HTML разметку страницы.

Пример тега **iframe**, отображающего интерактивный видеопроигрыватель размером 840x560 пикселей представлен ниже:

```
 <iframe style="width:840px; height:560px" allowFullScreen src="https://movika.com/player/123Sd">
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

Чтобы использовать sdk вам так же понадобится получить API Key для ваших приложений. Напишите нам в
Telegram [@Salavatsad](https://t.me/Salavatsad) или на почту [support@movika.com](mailto:support@movika.com),
[sdk@movika.com](mailto:sdk@movika.com),
чтобы получить API key.

#### iOS SDK

1. [Начало работы](/ru/sdk/ios/get-started.md)
2. [Сохранение фильмов](/ru/sdk/ios/save-state.md)
3. [Настройка интерфейса](/ru/sdk/ios/ui-customization.md)
4. [Пользовательские интерактивы](/ru/sdk/ios/custom-events.md)

#### Android SDK

0. [Начало работы](/ru/sdk/android/getting-started.md)
1. [Получение данных для воспроизведения](/sdk/android/getting-movie-bundle.md)
2. [Воспроизведение](/ru/sdk/android/run-interactiveplayerview.md)
3. [Конфигурация плеера](/ru/sdk/android/config.md)
4. [События плеера](/ru/sdk/android/player-events.md)
5. [Кастомизация плеера](/ru/sdk/android/introduce-to-player-customization.md)
6. [Кастомизация элементов интерфейса паузы и воспроизведение](/ru/sdk/android/play-pause-customization.md)
7. [Кастомизация элементов интерфейса смены аудио-дорожек и субтитров](/ru/sdk/android/audio-subtitles-customization.md)
8. [Кастомизация интерактивов](/ru/sdk/android/interactive-customization.md)
