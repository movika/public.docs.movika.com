---
title: Начало работы
description: Начало работы
keywords: Начало работы
sort: 0
---

# Вступление

Данное руководство содержит список действий для начала использования нашего SDK. Вы узнаете, как подключить проигрыватель Movika в приложение и какие параметры проигрывателя будут вам доступны.

# Начало работы

## 1. Зарегистрируйте свое приложение в Movika Developer

Зарегистрируйте свое приложение в [Movika Developer](https://developer.movika.com). После регистрации вы увидите таблицу со всеми своими ранее зарегистрированными приложениями. Поля **appName** и **apiKey** нам понадобится для аутентификации в SDK.

## 2. Добавьте ваш NPM-KEY

Для получения доступа на скачивание SDK вам потребуется получить ключ доступа. Для его получения обратитесь к sdk@movika.com. После получения ключа доступа добавьте файл .npmrc в корень проекта и замените ${NPM-KEY} на полученный ключ доступа.

```
 _authToken=${NPM-KEY}
```

## 3. Скачайте SDK

```
 npm i @interactiveplatform/movika-player
```

## 4. Создайте плеер

```
 import React from 'react';
 import { movika } from '@interactiveplatform/movika-player'

 function App() {
  const videoRef = React.useRef(null)
  const videoContainerRef = React.useRef(null)

  React.useEffect(() => {
    const playerOptions = {
      apiKey: <YOUR_API_KEY>,
      appName: <YOUR_APP_NAME>,
      manifest: '<URL_TO_MANIFEST>',
    }

    const controlsOverlayOptions = {
      endOfMovieScreen: true,
    }

    const mp = new movika.Player(videoRef.current, playerOptions)
    const mco = new movika.ControlsOverlay(mp, videoContainerRef.current, controlsOverlayOptions)
    const mi = new movika.Interactives(mp)

    return () => {
			mp.destroy()
			mco.destroy()
			mi.destroy()
		}
 }, []);

	const style = {
		width: '100vw',
		height: 'calc((9 / 16) * 100vw)',
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

После правильного выполнения всех шагов (1-4), у вас должен отобразиться плеер Movika.

![Веб плеер movika](https://raw.githubusercontent.com/movika/public.docs.movika.com/feature/web-sdk-doc-2.5/images/web-player-screen.png)
