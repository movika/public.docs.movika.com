---
title: Public documentation of movika.com
description: Public documentation of movika.com
keywords: Public documentation of movika.com
---

# Public documentation of movika.com

Interactive Platform Documentation

## SDK

### Mobile SDK

Для добавления интерактивного плеера в свое мобильное приложение, воспользуйстель данной инструкцией для Android, iOS

Чтобы использовать sdk вам так же понадобится получить API Key для ваших приложений. Напишите нам на в Telegram [salavat@movika.com](https://t.me/Salavatsad) или на почту salavat@movika.com, fanis@movika.com, чтобы получить API key.

#### iOS SDK

1. [Начало работы](/ios/sdk/00-get-started.md)
2. [Сохранение фильмов](/ios/sdk/01-save-state.md)
3. [Настройка интерфейса](/ios/sdk/02-ui-customization.md)
4. [Пользовательские интерактивы](/ios/sdk/03-custom-events.md)

#### Android SDK

0. [Начало работы](/android/sdk/00-getting-started.md)
1. [Получение данных для воспроизведения](/android/sdk/01-getting-movie-bundle.md)
2. [Воспроизведение](/android/sdk/02-run-interactiveplayerview.md)
3. [Конфигурация плеера](/android/sdk/03-config.md)
4. [События плеера](/android/sdk/04-player-events.md)
5. [Кастомизация плеера](/android/sdk/05-introduce-to-player-customization.md)
6. [Кастомизация элементов интерфейса паузы и воспроизведение](/android/sdk/06-play-pause-customization.md)
7. [Кастомизация элементов интерфейса смены аудио-дорожек и субтитров](/android/sdk/07-audio-subtitles-customization.md)
8. [Кастомизация интерактивов](/android/sdk/08-interactive-customization.md)

### Web

Интеграция Web SDK Movika со страницей сайта осуществляется с помощью встраивания тега iframe.

На странице сайта определяется местоположение тега iframe, который описывается следующими параметрами:

src - содержит URL, указывающий на путь, содержащий интерактивный видеоконтент;
width - задает ширину плеера проигрываемого видеоконтента;
height - задает высоту плеера проигрываемого видеоконтента;
allowFullScreen - разрешает или запрещает полноэкранное воспроизведение видео.
Пример тега iframe, отображающего интерактивный видеопроигрыватель размером 840x560 пикселей представлен ниже:

```
 <iframe style="width:840px; height:560px" allowFullScreen src="https://movika.com/player/123Sd">
 </iframe>
```
