---
title: Get started
description: Get started
keywords: Get started
sort: 0
---

# Introduction

This guide contains a list of steps to get started using our SDK. You will learn how to connect Movika player to the application and what player options will be available to you.

# Get started

## 1. Register your application with Movika Developer

Register your application with [Movika Developer] (https://developer.movika.com). After registration, you will see a table with all your previously registered applications. We need the **appName** and **apiKey** fields for authentication in the SDK.

## 2. Add your NPM-KEY

To gain access to download the SDK, you will need to obtain an access key. To obtain it, please contact support@movika.com. After obtaining the access token, add the .npmrc file to the project root and replace $ {NPM-KEY} with the obtained access token.

```
 _authToken=${NPM-KEY}
```

## 3. Download SDK

```
 npm i @interactiveplatform/movika-player
```

## 4. Create a player

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

    const mp = new movika.Player(videoRef.current, options)
    const mco = new movika.ControlsOverlay(mp, videoContainerRef.current, controlsOverlayOptions)
    const mi = new movika.Interactives(mp)

    return () => {
			mp.destroy()
			co.destroy()
			int.destroy()
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

After all the steps (1-4) have been completed correctly, your Movika player should be displayed.

![web player movika](https://raw.githubusercontent.com/movika/public.docs.movika.com/feature/web-sdk-doc-2.5/images/web-player-screen.png)
