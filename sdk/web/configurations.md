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
5. **utils** - contains a list of helper functions for implementing custom interactives

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

#### attachManifest({manifest, initialChapter, continueHistory})

Attaches the new manifest. The old manifest is detached automatically.

Parameters:

| Name            | Required | Type             | Default | Description                                                |
| --------------- | -------- | ---------------- | ------- | ---------------------------------------------------------- |
| manifest        | Yes      | String \| Object | -       | Interactive movie manifest URL or object                   |
| initialChapter  | No       | String           | -       | Chapter ID indicating which chapter to start playback from |
| continueHistory | No       | Boolean          | true    | Decides whether to continue the story or start a new one   |

```
  const mp = new Player(mediaElement, playerOptions)
  ...
  mp.attachManifest({manifest: myManifest, initialChapter: "chapterId", continueHistory: false})
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
  new Interactives(playerInstance, controlOverlayInstance)
```

### **Parameters:**

| Name                   | Required | Type                   | Default | Description                             |
| ---------------------- | -------- | ---------------------- | ------- | --------------------------------------- |
| playerInstance         | Yes      | playerInstance         | -       | An instance of the Player class         |
| controlOverlayInstance | Yes      | controlOverlayInstance | -       | An instance of the ControlOverlay class |

### Methods:

#### addFactory(type, fn)

Adds a custom interactive (container) to the list of available interactives (containers)

Parameters

| Name | Required | Type     | Description                                                 |
| ---- | -------- | -------- | ----------------------------------------------------------- |
| type | Да       | String   | Unique type of custom interactive                           |
| fn   | Да       | Function | Function to create custom interactive objects based on type |

```
  const mi = new Interactives(playerInstance, controlOverlayInstance)

  // add new interactive
  mi.addFactory('type', (container) => {
    if (container.type.trim().toLowerCase() === 'type') {
		  return new MyInteractive(container)
	  }
  })
```

#### removeFactory(type)

Removes a custom interactive (container) from the list of available interactives (containers)

Parameters

| Name | Required | Type   | Description                       |
| ---- | -------- | ------ | --------------------------------- |
| type | Да       | String | Unique type of custom interactive |

#### destroy()

Removes all listeners and clears all properties of the Player instance.

```
  const mi = new Interactives(playerInstance, controlOverlayInstance)

  // remove interactive
  mi.removeFactory('type')
```

## utlis

### new Container(container)

#### Properties:

| Name      | Type   | Description                                                       |
| --------- | ------ | ----------------------------------------------------------------- |
| container | Object | The `Container` property from the manifest                        |
| factories | Map    | A collection of available factory functions for creating controls |
| controls  | Array  | List of current controls                                          |

#### Methods:

#### constructor(container)

Parameters

| Name      | Required | Type   | Description                                |
| --------- | -------- | ------ | ------------------------------------------ |
| container | Yes      | Object | The `Container` property from the manifest |

<!-- #### run()

Matches the types of controls from the current manifest with the passed controls - addControlFactory -->

#### addControlFactory(type, factoryFn)

Add the control factory

Parameters

| Name      | Required | Type     | Description                                      |
| --------- | -------- | -------- | ------------------------------------------------ |
| type      | Да       | String   | Unique type of control                           |
| factoryFn | Да       | Function | Function to create control objects based on type |

#### removeControlFactory(type)

Remove the control factory

Parameters

| Name | Required | Type   | Description                       |
| ---- | -------- | ------ | --------------------------------- |
| type | Да       | String | Unique type of custom interactive |

### new ChoiceContainer(container)

#### Properties:

| Name   | Type           | Description                      |
| ------ | -------------- | -------------------------------- |
| layout | RelativeLayout | Instance of class RelativeLayout |

#### Methods:

#### constructor(container)

Parameters

| Name      | Required | Type   | Description                                       |
| --------- | -------- | ------ | ------------------------------------------------- |
| container | Yes      | Object | `Container` with type `Choice` from the manifest. |

#### createView(callback)

Creates a view and registers event handlers.

Parameters

| Name     | Required | Type     | Description                                                                                                                   |
| -------- | -------- | -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| callback | Yes      | Function | The callback requires 1 required argument - [action](../android/data-structure.md#структура-action) and is called on an event |

#### removeView()

Removes the container HTMLElement

#### hide()

Hides the container HTMLElement

#### show()

Shows the container HTMLElement if it was previously hidden

#### getElement()

Returns the container element

### new ButtonControl(control)

#### Properties:

| Name    | Type   | Description                                    |
| ------- | ------ | ---------------------------------------------- |
| control | Object | `Control` with type `Button` from the manifest |

#### Methods:

#### constructor(container)

Parameters

| Name    | Required | Type   | Description                                    |
| ------- | -------- | ------ | ---------------------------------------------- |
| control | Yes      | Object | `Control` with type `Button` from the manifest |

#### createView(options)

Creates a view of the control

Parameters

| Name             | Required | Type        | Description                                      |
| ---------------- | -------- | ----------- | ------------------------------------------------ |
| options.parent   | Yes      | HTMLElement | Parent element where the control will be created |
| options.layoutFn | Yes      | Function    | Function to apply control layout                 |

#### setEvents(element, callback)

Adds event listeners for controls

Parameters

| Name     | Required | Type        | Description                               |
| -------- | -------- | ----------- | ----------------------------------------- |
| element  | Yes      | HTMLElement | Element that will listen for events       |
| callback | No       | Function    | The function to be called after the event |

#### getElements()

Returns the HTMLElement of the control

### RelativeLayout()

#### Properties:

| Name   | Type   | Description                                                  |
| ------ | ------ | ------------------------------------------------------------ |
| layout | Object | The `Layout` property with type `Relative` from the manifest |

#### Methods:

#### constructor(layout)

Parameters

| Name   | Required | Type   | Description                                                  |
| ------ | -------- | ------ | ------------------------------------------------------------ |
| layout | Yes      | Object | The `Layout` property with type `Relative` from the manifest |

#### setContainerLayout(target)

Applies styles to the container HTMLElement

Parameters

| Name   | Required | Type        | Description                               |
| ------ | -------- | ----------- | ----------------------------------------- |
| target | Yes      | HTMLElement | The HTMLElement to apply layout styles to |

#### setControlLayout(target, layoutParams)

Applies styles to the control HTMLElement

Parameters

| Name         | Required | Type        | Description                                                         |
| ------------ | -------- | ----------- | ------------------------------------------------------------------- |
| target       | Yes      | HTMLElement | The HTMLElement to apply layout styles to                           |
| layoutParams | Yes      | Object      | The `layoutParams` property of a specific control from the manifest |

### createAreaControl(target, layoutParams)

Returns a AreaControl object

Parameters

| Name    | Required | Type   | Description                                   |
| ------- | -------- | ------ | --------------------------------------------- |
| control | Yes      | String | `Control` with type `Area` from the manifest. |

### createButtonControl(control)

Returns a ButtonControl object

Parameters

| Name    | Required | Type   | Description                                    |
| ------- | -------- | ------ | ---------------------------------------------- |
| control | Yes      | String | `Control` with type `Button` from the manifest |

### createChoiceContainer(container)

Returns a ChoiceContainer object

Parameters

| Name      | Required | Type   | Description                                      |
| --------- | -------- | ------ | ------------------------------------------------ |
| container | Yes      | String | `Container` with type `Choice` from the manifest |

### createRelativeLayout(layout)

Returns a RelativeLayout object

Parameters

| Name   | Required | Type   | Description                                                |
| ------ | -------- | ------ | ---------------------------------------------------------- |
| layout | Yes      | String | The `layout` property of type `Relative` from the manifest |

### getRootEl()

Returns the parent HTMLElement where the containers should be placed
