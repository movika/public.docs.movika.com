---
title: Встраивание Movika
description: Встраивание Movika
keywords: Встраивание Movika
sort: 4
---

# Встраивание Movika (DEPRECATED)

Интеграция Web SDK Movika на сайт осуществляется с помощью встраивания тега iframe в HTML разметку страницы.

 <iframe allowFullScreen src="https://movika.com/ru/player/movika-sdk-sample" allowFullScreen scrolling="no" frameborder="0">
 </iframe>

Пример тега **iframe**, отображающего интерактивный видеопроигрыватель размером 840x560 пикселей представлен ниже:

```
 <iframe style="width:840px; height:560px" allowFullScreen src="https://movika.com/ru/player/movika-sdk-sample">
 </iframe>
```

Параметры (атрибуты) iframe:

- **src** - содержит URL, указывающий на путь, содержащий интерактивный видеоконтент;
- **width** - задает ширину плеера проигрываемого видеоконтента;
- **height** - задает высоту плеера проигрываемого видеоконтента;
- **allowFullScreen** - разрешает или запрещает полноэкранное воспроизведение видео.
