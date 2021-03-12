---
title: Настройка интерфейса
description: Настройка интерфейса
keywords: Настройка интерфейса
sort: 2
---

# Настройка интерфейса

### Настройка внешнего вида кнопок интерактива choice

Переопределить переменную uiManager класса MovikaPlayerViewController

```
open var uiManager: UIManager?
```

Структура UIManager содержит тему в которой вы можете перееопределить

Цвет текста кнопок
public var buttonTextColor: UIColor

Цвет кнопок
public var buttonBackgroundColor: UIColor = .white
