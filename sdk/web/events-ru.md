---
title: События
description: События
keywords: События
sort: 2
---

# События

Для прослушивания событий плеера достаточно добавить необходимые слушатели. Все доступные на данный момент события можно получить из объекта **Events**, который экспортируется из библиотеки movika-player.

```
import React from 'react';
import { movika } from '@interactiveplatform/movika-player'

function App() {
  const videoRef = React.useRef(null)
  const videoContainerRef = React.useRef(null)

  React.useEffect(() => {
    const options = {
      apiKey: <YOUR_API_KEY>,
      appName: <YOUR_APP_NAME>,
      manifest: '<URL_TO_MANIFEST>',
    }

    const mp = new movika.Player(videoRef.current, options)
    const mco = new movika.ControlsOverlay(mp, videoContainerRef.current, videoRef.current)
    const mi = new movika.Interactives(mp, options, videoRef.current)
  }, []);

  // Подписка на событие окончания видео
  videoRef.current.addEventListener(movika.Events.END_VIDEO, () => {
    console.log('here')
  })

  const style = {
    height: 'calc((9 / 16) * 100vw)',
    width: '100vw',
  }

  return (
    <div style={style}>
      <div ref={videoContainerRef}>
        <video ref={videoRef}/>
      </div>
    </div>
  )
}

export default App
```

Ниже перечислены все события, доступные на данный момент:

| Наименование                              | Описание                                                                               |
| ----------------------------------------- | -------------------------------------------------------------------------------------- |
| movika.Events.END_VIDEO                   | Срабатывает при окончании фильма                                                       |
| movika.Events.REPLAY_CHAPTER              | Срабатывает при нажатии на кнопки пересмотра текущей главы фильма                      |
| movika.Events.SEEK_TO_CHAPTER_INTERACTIVE | Срабатывает при нажатии на кнопку перемотки главы в начало появления игровых элементов |
| movika.Events.CHANGE_VIDEO_VOLUME         | Срабатывает при изменении звука                                                        |
| movika.Events.TOGGLE_VIDEO_FULLSCREEN     | Срабатывает при входе в полноэкранного режима и выходе из полноэкранного режима        |
| movika.Events.ATTACH_MANIFEST             | Срабатывает при подключении в плеер нового манифеста                                   |
