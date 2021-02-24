---
title: Interface customization
description: Interface customization
keywords: Interface customization
sort: 2
---

# Interface customization

### Customize appearance of the playback controls

If you need to customize the appearance of the pause menu and the playback pause button, simply override the controller class methods

- func createPauseMenu (parent: UIView) -> UIView
- func createPauseButton (parent: UIView) -> UIView
  By default, the created view will not be added to its parent, call parent.addSubview(pauseButton) if you want to display it in a custom view.

### Customize appearance of interactive buttons

Override uiManager variable of MovikaPlayerViewController class

```
open var uiManager: UIManager?
```

The UIManager structure contains a theme in which you can override

Button text color
public var buttonTextColor: UIColor

Button color
public var buttonBackgroundColor: UIColor = .white
