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

| Наименование    | Обязательный | Тип    | По умолчанию | Описание                                                                                            |
| --------------- | ------------ | ------ | ------------ | --------------------------------------------------------------------------------------------------- |
| manifest        | Да           | String | -            | Манифест интерактивного фильма                                                                      |
| apiKey          | Да           | String | -            | apiKey, полученный после регистрации приложения в [Movika Developer](https://developer.movika.com)  |
| appName         | Да           | String | -            | appName, полученный после регистрации приложения в [Movika Developer](https://developer.movika.com) |
| preferredFormat | Нет          | String | HLS          | Предпочтительный формат для воспроизведения. Доступные значения: MP4 и HLS                          |

### Методы Player:

#### destroy()

Удаляет все слушатели и очищает все свойства экземпляра класса Player.

```
  const mp = new Player(mediaElement, playerOptions)

  // destroy method
  mp.destroy()
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
| endOfVideoScreen | Нет          | Boolean | true         | Показать элемент окончания видео |

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
