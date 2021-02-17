---
title: Player customization
description: Player customization
keywords: Player customization
sort: 5
---

# Player customization

Player customization is possible by changing the values ​​of the ** InteractivePlayerView ** instance.
These manipulations must be performed before starting the player.
Possible values to change:

- timeMarginSeekToEventSec: Float - the minimum time interval before the start of the interactive up to which
  the user is allowed fast-forward to.
- customEventViewFactory: CustomEventViewFactory? - custom interactive factory
- interactiveFactory: InteractiveFactory? - factory of standard interactives
- customEventContainer: ViewGroup? - custom container in which interactives will be displayed