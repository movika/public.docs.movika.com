---
title: Готовый к использованию плеер
description: Готовый к использованию плеер
keywords: Готовый к использованию плеер
sort: 4
---

# Готовый к использованию

### MKEasyPlayer

MKEasyPlayer UIView компонент позволяющий с минимальными настройками добавить в ваш проект интерактивный плеер. 

Данное UIView включает в себя:
- MKPlayer (движок интерактивного видео);
- Дефолтная реализация MKPlayerView (слой отображения видео);
- Элементы управления воспроизведением (play, pause, перемотка назад, перемотка вперед);
- Полоса воспроизведения;
- Дебаг меню для отладки состояния фильма;

используйте данный код для того чтобы добавить MKEasyPlayer:

    
```
    let avplayer = AVPlayerView(frame: view.frame)
    avplayer.playerItemAdapter = AVPlayerItemAdapterImpl(videoConfig: VideoTypeConfiguration(videoType: videoType))
    self.view.addSubview(avplayer)

    let mkplayer = MKEasyPlayer(frame: view.frame)
    mkplayer.playerView = avplayer
    avplayer.avPlayerViewDelegate = mkplayer
```

для отображения дебаг меню используйте:
```
    mkplayer.isShowDebugView = isShowDebugView
```

для отслеживания состояния интерактивного фильма используйте:
```
\\implement MKPlayerDelegate 
mkplayer.delegate = self 
```


