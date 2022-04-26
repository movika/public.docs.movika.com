---
title: SimpleInteractivePlayer configuration 
description: SimpleInteractivePlayer configuration
keywords: SimpleInteractivePlayer configuration
sort: 3 
---

# Конфигурация SimpleInteractivePlayer

Для изменения некоторых настроек **SimpleInteractivePlayer** необходимо передать в его конструктор экземпляр класса **Config**, который содержит следующие поля:

| Название | Тип | По-умолчанию | Описание |
|---|---|---|---|
| isDebugMode | Boolean | false | обозначает, включен ли режим отладки в виде debug menu во время воспроизведения |
| isLocalVideoContent | Boolean | false | данный параметр не является обязательным. Служит для оптимизации воспроизведения. Обозначает, тип воспроизводимого контента по расположению. true - контент находится на устройстве, false - контента не находится на устройстве (доступ к контенту осуществляется по протоколу https). |
| isShowDefaultTimeBar | Boolean | true | обозначает, показывать ли шкалу прогресса текущей главы |
