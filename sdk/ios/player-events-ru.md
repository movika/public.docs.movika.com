---
title: События плеера
description: События плеера
keywords: События плеера
sort: 2 
---

# События плеера

Для отслеживания событий плеера требуется реализовать протокол **MKPlayerDelegate**
---

Метод вызывается при взаимодействии с плеером, результат находится в структуре **InteractionResult**
```
func mkplayer(_ player: MKPlayer, result: InteractionResult)
```

Метод вызывается при паузе/возобновлении видео, результат находится в переменной **isPause**
```
func mkplayer(_ player: MKPlayer, isPause: Bool)
```

Метод вызывается при отслеживании состояния видео, результат находится в структуре **MKPlayState**
```
func mkplayer(_ player: MKPlayer, didUpdate state: MKPlayState)
```

Метод вызывается в случае если интерактив ведет на эту ссылку, результат отслеживать через **URL**
```
func mkplayer(_ player: MKPlayer, didRequestOpen uri: URL)
```

Метод вызывается в конце видео, результат отслеживать через **MKManifest**
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
