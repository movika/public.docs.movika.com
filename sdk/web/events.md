---
title: Events
description: Events
keywords: Events
sort: 2
---

# Events

To listen to player events, you just need to add the necessary listeners. All currently available events can be obtained from the **Events** object, which is exported from the movika-player library.

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

  // Subscribe to video end event
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

All events currently available are listed below:

| Name                                         | Description                                                                                        |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| movika.Events.END\_VIDEO                     | Fires when the movie ends                                                                          |
| movika.Events.REPLAY\_CHAPTER                | Fires when you click on the revision buttons for the current chapter of the movie                  |
| movika.Events.SEEK\_TO\_CHAPTER\_INTERACTIVE | Fires when you press the chapter rewind button to the beginning of the appearance of game elements |
| movika.Events.CHANGE\_VIDEO\_VOLUME          | Fires when the sound changes                                                                       |
| movika.Events.TOGGLE\_VIDEO\_FULLSCREEN      | Fires when entering full screen mode and exiting full screen mode                                  |
| movika.Events.ATTACH\_MANIFEST               | Fires when a new manifest is connected to the player                                               |
