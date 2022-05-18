---
title: Configurations
description: Configurations
keywords: Configurations
sort: 1
---

# Configurations

### The following classes and objects are exported from the movika-player library:

1. **Player** - designed to play media.
2. **ControlsOverlay** - designed to display the elements of the player.
3. **Interactives** - designed to display game ("interactive") elements of the player.
4. **Events** - contains a list of available events for subscription.

## Player

### Constructor:

```
  new Player(mediaElement, playerOptions)
```

### **Player parameters**:

| Name          | Required | Type             | Default | Description           |
| ------------- | -------- | ---------------- | ------- | --------------------- |
| mediaElement  | Yes      | HTMLVideoElement | -       | DOM-element           |
| playerOptions | Yes      | Object           | -       | Player configurations |

### **PlayerOptions parameters:**

| Name               | Required | Type             | Default | Description                                                                                                                                                       |
| ------------------ | -------- | ---------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| src                | Yes      | String \| Object | -       | Specifies the URL of the video file or interactive movie manifest. Supports .m3u8, .mp4, .json extensions. Also works with the interactive movie manifest object. |
| apiKey             | Yes      | String           | -       | apiKey obtained after registering the application with [Movika Developer](https://developer.movika.com)                                                           |
| appName            | Yes      | String           | -       | appName obtained after registering the application with [Movika Developer](https://developer.movika.com)                                                          |
| preferredExtension | No       | String           | m3u8    | Preferred playback extension. Available values: mp4 and m3u8                                                                                                      |
| initialChapter     | No       | String           | -       | Chapter ID indicating which chapter to start playback from                                                                                                        |
| initialHistory     | No       | Object           | -       | If a valid history object is passed, the player will continue to write history to that object. If the history object is invalid, create a new history object.     |
| autoplay           | No       | boolean          | -       | Specifies that the video will start playing as soon as it is ready                                                                                                |
| loop               | No       | boolean          | -       | Specifies that the video will start over again, every time it is finished                                                                                         |
| width              | No       | Number           | -       | Sets the width in pixels of the video player                                                                                                                      |
| height             | No       | Number           | -       | Sets the height in pixels of the video player                                                                                                                     |
| muted              | No       | boolean          | -       | Specifies that the audio output of the video should be muted                                                                                                      |
| controls           | No       | boolean          | -       | Specifies that the default HTMLVideoElement controls should be displayed                                                                                          |

### Methods:

#### destroy()

Removes all listeners and clears all properties of the Player instance.

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.destroy()
  ...
```

#### getHistory()

Returns the history of the interactive movie.

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  const hist = mp.getHistory()
  ...
```

#### attachManifest(manifest, initialChapter)

Attaches the new manifest. The old manifest is detached automatically.

Parameters:

| Name           | Required | Type             | Description                                                |
| -------------- | -------- | ---------------- | ---------------------------------------------------------- |
| manifest       | Yes      | String \| Object | Interactive movie manifest URL or object                   |
| initialChapter | No       | String           | Chapter ID indicating which chapter to start playback from |

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.attachManifest(manifest, initialChapter)
  ...
```

#### play()

The video player starts playing

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.play()
  ...
```

#### pause()

The video player stops playing

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.pause()
  ...
```

#### mute()

Mutes the sound in the video player

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.mute()
  ...
```

#### unmute()

Turns on the sound in the video player

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.unmute()
  ...
```

## ControlsOverlay

### Constructor:

```
  new ControlsOverlay(playerInstance, containerElement, controlsOverlayOptions)
```

### **ControlsOverlay parameters:**

| Name                   | Required | Type           | Default | Description                                                                                      |
| ---------------------- | -------- | -------------- | ------- | ------------------------------------------------------------------------------------------------ |
| playerInstance         | Yes      | playerInstance | -       | An instance of the Player class                                                                  |
| containerElement       | Yes      | HTMLElement    | -       | The element that will contain the player itself, player controls and game elements of the player |
| controlsOverlayOptions | No       | Object         | -       | ControlsOverlay configurations                                                                   |

### **ControlsOverlayOptions parameters:**

| Name             | Required | Type    | Default | Description               |
| ---------------- | -------- | ------- | ------- | ------------------------- |
| width            | No       | String  | 100%    | Container width           |
| height           | No       | String  | 100%    | Container height          |
| endOfVideoScreen | No       | Boolean | false   | Show video ending element |

### Methods:

#### destroy()

Removes all listeners and clears all properties of the ControlsOverlay instance.

```
  const co = new ControlsOverlay(playerInstance, containerElement, controlsOverlayOptions)

  // destroy method
  co.destroy()
```

## Interactives

### Constructor:

```
  new Interactives(playerInstance)
```

### **Interactives parameters:**

| Name           | Required | Type           | Default | Description                     |
| -------------- | -------- | -------------- | ------- | ------------------------------- |
| playerInstance | Yes      | playerInstance | -       | An instance of the Player class |

### Methods:

#### destroy()

Removes all listeners and clears all properties of the Player instance.

```
  const mi = new Interactives(playerInstance)

  // destroy method
  mi.destroy()
```
