---
title: Настройка интерфейса
description: Настройка интерфейса
keywords: Настройка интерфейса
---

# Настройка интерфейса
### Настройте внешний вид элементов управления воспроизведением

Если необходимо настроить внешний вид меню паузы и кнопки остановки воспроизведения, просто переопределится методы класса контроллера 
- func createPauseMenu(parent: UIView) -> UIView 
- func createPauseButton(parent: UIView) -> UIView 
по умолчанию созданное view ну будет добавлено в parent, вызовете         parent.addSubview(pauseButton) если требуется отобразить кастомное отображение. 

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
