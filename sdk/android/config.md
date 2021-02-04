---
title: Конфигурация плеера
description: Конфигурация плеера
keywords: Конфигурация плеера
sort: 3
---

# Конфигурация плеера

Базовая конфигурация задается с помощью объекта **Config**, передача которого зависит от способа запуска плеера
(с помощью **InteractivePlayerViewRunner**, или напрямую в метод run класса **InteractivePlayerView**)  
Многие параметры связаны непосредственно с кастомизацией плеера. Кастомизация плеера будет описана позднее.
Поля класса **Config**:

- isUseDefaultPlayPauseController: Boolean - обозначает, будет ли использоваться стандартный
  интерфейс управления паузой/воспроизведение. При значении false разработчику будет необходимо реализовать кнопку паузы самому,
  это будет полезно при реализации кастомного меню паузы. По умолчанию данное поле принимает значение true.
- isUseDefaultPlaybackErrorUi: Boolean - обозначает, использовать ли стандартный интерфейс ошибки
  воспроизведения. По умолчанию принимает значение true.
- isSeekEnable: Boolean - обозначает, включена ли возможность перемотки пользователем по двойному тапу.
  По умолчанию принимает значение true.
- isDebugMode: Boolean - обозначает, включен ли режим отладки в виде debug menu во время воспроизведения.
  По умолчанию принимает значение false.
- isLoop: Boolean - обозначает, будет ли зациклен интерактивный ролик. При значении true, после завершения
  тупиковой главы, будет воспроизведена начальная глава. По умолчанию принимает значение false.
- isCacheStartPartsOfNextChapters: Boolean - обозначает, будут ли кешироваться начальные фрагменты следующих
  возможных глав. По умолчанию принимает значение true.
- isLocalVideoContent: Boolean - данный параметр не является обязательным. Служит для оптимизации
  воспроизведения. Обозначает, тип воспроизводимого контента по расположению. true - контент находится на устройстве,
  false - контента не находится на устройстве (доступ к контенту осуществляется по протоколу https).
  По умолчанию принимает значение false.
- isShowTimeBar: Boolean - обозначает, показывать ли шкалу прогресса текущей главы. По умолчанию
  принимает значение true.