---
title: Воспроизведение
description: Воспроизведение
keywords: Воспроизведение
---

## Воспроизведение
Для воспроизведения необходимо вызвать метод run у интерактивного плеера **InteractivePlayerView**
Сам метод выглядит так:
```
fun run(
    movieBundle: MovieBundle,
    config: Config,
    savedInstanceState: Bundle? = null
)
```

- movieBundle - содержит описание интерактивного фильма.
- config - конфигурация интерактивного плеера.
- savedInstanceState - экземпляр класса Bundle. Данный аргумент является опциональным. Необходим для 
восстановления состояния после пересоздания Activity/Fragment.