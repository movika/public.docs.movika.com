---
title: Конфигурации
description: Конфигурации
keywords: Конфигурации
sort: 1
---

# Конфигурации

### Из библиотеки movika-player экспортируются следующие классы и объекты:

1. **Player** - предназначен для воспроизведения медиа.
2. **ControlsOverlay** - предназначен для отображения элементов плеера.
3. **Interactives** - предназначен для отображения игровых ("интерактивных") элементов плеера.
4. **Events** - содержит список доступных событий для подписки.

## **Player**

### Конструктор Player:

```
  new Player(mediaElement, playerOptions)
```

### Параметры Player:

| Наименование  | Обязательный | Тип              | По умолчанию | Описание            |
| ------------- | ------------ | ---------------- | ------------ | ------------------- |
| mediaElement  | Да           | HTMLVideoElement | -            | DOM-элемент         |
| playerOptions | Да           | Object           | -            | Конфигурации плеера |

### Параметры playerOptions:

| Наименование       | Обязательный | Тип              | По умолчанию | Описание                                                                                                                                                                   |
| ------------------ | ------------ | ---------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| src                | Да           | String \| Object | -            | Указывает URL-адрес видеофайла или манифеста интерактивного фильма. Поддерживает .m3u8, .mp4, .json расширения. Также работает с объектом манифеста интерактивного фильма. |
| apiKey             | Да           | String           | -            | apiKey, полученный после регистрации приложения в [Movika Developer](https://developer.movika.com)                                                                         |
| appName            | Да           | String           | -            | appName, полученный после регистрации приложения в [Movika Developer](https://developer.movika.com)                                                                        |
| preferredExtension | Нет          | String           | m3u8         | Предпочтительное расширение файла для воспроизведения. Доступные значения: mp4 и m3u8                                                                                      |
| initialChapter     | Нет          | String           | -            | Идентификатор главы, указывающий с какой главы нужно начать воспроизведение                                                                                                |
| initialHistory     | Нет          | Object           | -            | Если передан валидный объект истории, то плеер продолжит записывать историю в этот объект. Если объект истории невалидный, создаст новый объект истории.                   |
| autoplay           | No           | boolean          | -            | Указывает, что видео начнет воспроизводиться, как только оно будет готово.                                                                                                 |
| loop               | No           | boolean          | -            | Указывает, что видео будет начинаться заново после того, как он закончится.                                                                                                |
| width              | No           | Number           | -            | Устанавливает ширину видеоплеера в пикселях.                                                                                                                               |
| height             | No           | Number           | -            | Устанавливает высоту видеоплеера в пикселях.                                                                                                                               |
| muted              | No           | boolean          | -            | Указывает, что звук у видео должен быть отключен.                                                                                                                          |
| controls           | No           | boolean          | -            | Указывает, что должны отображаться дефолтные элементы управления HTMLVideoElement.                                                                                         |

### Методы Player:

#### destroy()

Удаляет все слушатели и очищает все свойства экземпляра класса Player.

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.destroy()
  ...
```

#### getHistory()

Возвращает историю интерактивного фильма.

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  const hist = mp.getHistory()
  ...
```

#### attachManifest(manifest, initialChapter)

Прикрепляет новый манифест. Старый манифест автоматически отсоединяется.

Параметры:

| Наименование   | Обязательный | Тип              | Описание                                                                    |
| -------------- | ------------ | ---------------- | --------------------------------------------------------------------------- |
| manifest       | Да           | String \| Object | Ссылка или объект на манифест интерактивного фильма                         |
| initialChapter | Нет          | String           | Идентификатор главы, указывающий с какой главы нужно начать воспроизведение |

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.attachManifest(manifest, initialChapter)
  ...
```

#### play()

Видеоплеер начинает воспроизведение

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.play()
  ...
```

#### pause()

Видеоплеер останавливает воспроизведение

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.pause()
  ...
```

#### mute()

Отключает звук в видеоплеере

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.mute()
  ...
```

#### unmute()

Включает звук в видеоплеере

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.unmute()
  ...
```

## **ControlsOverlay**

### Конструктор ControlsOverlay:

```
  new ControlsOverlay(playerInstance, containerElement, controlsOverlayOptions)
```

### Параметры ControlsOverlay:

| Наименование           | Обязательный | Тип            | По умолчанию | Описание                                                                                                 |
| ---------------------- | ------------ | -------------- | ------------ | -------------------------------------------------------------------------------------------------------- |
| playerInstance         | Да           | playerInstance | -            | Экземпляр класса Player                                                                                  |
| containerElement       | Да           | HTMLElement    | -            | Элемент, внутри которого будут находится сам плеер, элементы управления плеера и игровые элементы плеера |
| controlsOverlayOptions | Нет          | Object         | -            | Конфигурации ControlsOverlay                                                                             |

### Параметры controlsOverlayOptions:

| Наименование     | Обязательный | Тип     | По умолчанию | Описание                         |
| ---------------- | ------------ | ------- | ------------ | -------------------------------- |
| width            | Нет          | String  | 100%         | Ширина контейнера                |
| height           | Нет          | String  | 100%         | Высота контейнера                |
| endOfVideoScreen | Нет          | Boolean | false        | Показать элемент окончания видео |

### Методы ControlsOverlay:

#### destroy()

Удаляет все слушатели и очищает все свойства экземпляра класса ControlsOverlay.

```
  const co = new ControlsOverlay(playerInstance, containerElement, controlsOverlayOptions)

  // destroy method
  co.destroy()
```

## Interactives

### Конструктор ControlsOverlay:

```
  new Interactives(playerInstance)
```

### Параметры Interactives:

| Наименование   | Обязательный | Тип            | По умолчанию | Описание                |
| -------------- | ------------ | -------------- | ------------ | ----------------------- |
| playerInstance | Да           | playerInstance | -            | Экземпляр класса Player |

### Методы ControlsOverlay:

#### destroy()

Удаляет все слушатели и очищает все свойства экземпляра класса Interactives.

```
  const mi = new Interactives(playerInstance)

  // destroy method
  mi.destroy()
```
