---
title: Структура плеера
description: Структура плеера
keywords: Структура плеера
sort: 1 
---

![Image](https://raw.githubusercontent.com/movika/public.docs.movika.com/develop/images/ios_player-arch.png)
# Структура плеера
**MKInteractivePlayer** является основным классом для работы с плеером, созданным на основе **MKPlayer**. Если требуется более детальная настройка, следует использовать **MKPlayer**, в остальных случаях следует пользоваться **MKInteractivePlayer**.

### Описание основных компонентов для работы с плеером
- **MKInteractivePlayer** - является основным классом для работы с плеером, отвечающим за главную логику и создание плеера. Методы для управления воспроизведением плеером описаны в протоколе **MKPlayerPlayback**.
- **MKEventsContainer** - протокол, отвечающий за отображение интерактивов. Базовая реализация описана в классе **MKDefaultsEventsContainer**. Для собственной настройки возможно реализовать собственный класс и внедрить в **MKPLayer**. 
- **MKPlayerView** - протокол, отвечающий за очереди интерактивных видео, плейлист, создание вью. Базовая реализация описана в классе **MKDefaultPlayerView**.

### Методы управления плеером, класс MKInteractivePlayer
```
    reset() // Сброс плеера
  
    restart() // Перезапуск плеера
    
    pause() // Пауза
    
    play() // Запуск
  
    seek(to position: Double) // Переместиться на позицию position
  
    canSeek(to position: Double) -> Bool // Метод, возвращающий Bool на возможность перемотки на данную секунду 

    playNextEvent() // Проиграть следующий интерактив
  
    playNextChapter() // Проиграть следующую главу
  
    playFirstChapter() // Проиграть первую главу
  
    playPreviousChapter() // Проиграть предыдущую главу
  
    setNextChapter(with chapterId: String) // Установить следующую главу на chapterId
 
    replaceCurrentChapter(with chapterId: String) // Изменить данную главу на chapterId
```
