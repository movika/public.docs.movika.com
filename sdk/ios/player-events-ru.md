---
title: События плеера
description: События плеера
keywords: События плеера
sort: 2 
---

# События плеера

Для отслеживания событий плеера требуется реализовать протокол **MKPlayerDelegate**
---

Результата взаимодействия содержится в структуре **InteractionResult**
```
func mkplayer(_ player: MKPlayer, result: InteractionResult)
```

Отслеживание, находится ли видео на паузе
```
func mkplayer(_ player: MKPlayer, isPause: Bool)
```

Отслеживание состояния видео через структуру **MKPlayState**
```
func mkplayer(_ player: MKPlayer, didUpdate state: MKPlayState)
```

Отслеживать через **URL** в случае если интерактив ведет на эту ссылку
```
func mkplayer(_ player: MKPlayer, didRequestOpen uri: URL)
```

Отслеживать если закончилось видео
```
func mkplayer(_ player: MKPlayer, didEndPlaying manifest: MKManifest)
```

Метод вызывается перед началом показа интерактива в текущей главе **Chapter**
```
func mkplayer(_ player: MKPlayer, willShowEventForChapter chapter: Chapter)
```

Метод вызывается при начале воспроизведения новой главы **Chapter**
```
func mkplayer(_ player: MKPlayer, showChapter chapter: Chapter)
```

Метод вызывается при появлении интерактива в главе **Chapter**
```
func mkplayer(_ player: MKPlayer, didAppearEventWithChapter chapter: Chapter)
```

## 	Обработка ошибок видеоплеера
Для обработки ошибок видеоплеера требуется реализовать следующий метод

```
func mkplayer(_ player: MKPlayer, error: Error)
```

### Состояния воспроизведения видео

- В случае если нужно получить доступ к состоянию воспроизведению видеоролика, нужно получить доступ к **AVPlayer** находящийся в **MKDefaultPlayerView**.
