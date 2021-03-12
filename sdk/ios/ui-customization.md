---
title: Interface customization
description: Interface customization
keywords: Interface customization
sort: 2
---

# Interface customization

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
