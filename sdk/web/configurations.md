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

```
  new Player(mediaElement, playerOptions)
```

### **Player parameters**:

| Name          | Required | Type             | Default | Description           |
| ------------- | -------- | ---------------- | ------- | --------------------- |
| mediaElement  | Yes      | HTMLVideoElement | -       | DOM-element           |
| playerOptions | Yes      | Object           | -       | Player configurations |

### **PlayerOptions parameters:**

| Name     | Required | Type   | Default | Description                                                                                              |
| -------- | -------- | ------ | ------- | -------------------------------------------------------------------------------------------------------- |
| manifest | Yes      | String | -       | Interactive film manifest                                                                                |
| apiKey   | Yes      | String | -       | apiKey obtained after registering the application with [Movika Developer](https://developer.movika.com)  |
| appName  | Yes      | String | -       | appName obtained after registering the application with [Movika Developer](https://developer.movika.com) |

## ControlsOverlay

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
| width            | No       | String  | "100%"  | Container width           |
| height           | No       | String  | "100%"  | Container height          |
| endOfVideoSсreen | No       | Boolean | true    | Show video ending element |

## Interactives

```
  new Interactives(playerInstance)
```

### **Interactives parameters:**

| Name           | Required | Type           | Default | Description                     |
| -------------- | -------- | -------------- | ------- | ------------------------------- |
| playerInstance | Yes      | playerInstance | -       | An instance of the Player class |
