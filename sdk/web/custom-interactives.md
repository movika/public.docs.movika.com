---
title: Сustom interactives
description: Сustom interactives
keywords: Сustom interactives
sort: 5
---

## Introduction

In addition to the built-in interactives, it is possible to add your own interactives - _custom interactives_.

First you need to understand what a [manifest](../android/data-structure.md) is. The manifest contains information for playing interactive video. Within the SDK, interactives are referred to as containers. **Further interactives will be called containers.**

Before you create a custom container, you need to [describe it in the manifest](../android/custom-interactives.md#описание-пользовательского-контейнера-в-manifestjson).

## Creating a Custom Container

In the SDK, containers are added using [Interactives](configurations.md#interactives).

To create a container, you can use classes, functions that are in [utils](configurations.md#utlis).

An example of a ready-made custom container can be viewed [here](configurations.md).

**Creating a custom container consists of the following steps:**

1. We inherit our custom container from `utils.Container`.
2. To add a custom control, use the `.addControlFactory(type, factoryFn)` method.
3. The following [methods](configurations.md#new-choicecontainercontainer) must be defined on the custom container:
   - `createView(callback)`
   - `show()`
   - `hide()`
   - `removeView()`
   - `getElement()`
4. The `createView` - `callback` parameter takes [event.action](../android/data-structure.md#структура-action) as an argument. And it should be called on certain events. These events are determined by the creator of the custom container.
5. After the description of the look and behavior, you need to add the custom container to the _SDK_. To do this, use the `interactivesInstance.addFactory(type, factoryFn)` method.

**Аdaptability**

Custom containers and controls should be responsive. To do this, you can use the `CSS properties` provided by _SDK_.

- `--video-content-width` - video width
- `--video-content-height` - video height
- `--player-width` - width of the `video` element
- `--player-height` - height of the `video` element
