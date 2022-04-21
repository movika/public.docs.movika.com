---
title: Доступ к истории интерактивов
description: Доступ к истории интерактивов
keywords: Доступ к истории интерактивов
sort: 4
---

Для более детального отслеживания событий прохождения интерактивов пользователем, есть возможность реализовать собственную структуру истории.

# Иннициализация
Для создания объекта класса **MKInteractivePlayer** с собственной историей, нужно заранее создать и заполнить структуру **History** и затем передаеть ее в объект класса **MKPlayerState**
(_Стоит быть внимательным в передаче *Chapter ID*, в случае передачи невалидного *ID*, произойдет __fatalError__._ )

# Настройка манифеста
На этапе иннициализации манифеста через метод **setManifestAsset**, требуется передать заполненный объект **MKPLayerState** вторым аргументом. В этом случае отслеживание событий прохождения интерактивов осуществляется напрямую через структуру **MKPLayerState**, также возможно использование делегатов вместе с историей.

# Содержание структуры MKPlayerState
```
manifestId: String
currentChapterId: String
currentChapterTime: Double
nextChapterId: String?
currentHistory: History

History:
manifestId: String
manifestVersion: String
manifestBuild: Int
isCompleted: Bool
sessions: [Session]

Session:
id: String
startDate: Date
updateOn: Date?
visitedChapters: [VisitedChapter]
branches: [Branch]

Branch:
id: String
```
Все поля являются публичными __(public var)__, доступ идет напрямую.

