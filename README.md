# docs
Interactive Platform Documentation

##SDK 
### Mobile SDK
Для добавления интерактивного плеера в свое мобильное приложение, воспользуйстель данной инструкцией для Android, iOS

Чтобы использовать sdk вам так же понадобится получить API Key для ваших приложений. Напишите нам на email salavat@movika.com или fanis@movika.com, чтобы получить API key.  

#### iOS SDK
1. [Начало работы](https://github.com/movika/public.docs.movika.com/blob/ios/ios/sdk/get_started.md)
2. [Сохранение фильмов](https://github.com/movika/public.docs.movika.com/blob/ios/ios/sdk/save_state.md) 
3. [Настройка интерфейса](https://github.com/movika/public.docs.movika.com/blob/ios/ios/sdk/ui_customization.md) 
4. [Пользовательские интерактивы](https://github.com/movika/public.docs.movika.com/blob/ios/ios/sdk/custom_events.md)

#### Android SDK
1. Начало работы
2. Сохранение фильмов 
3. Настройка интерфейса 
4. Пользовательские интерактивы

### Web 
Интеграция Web SDK Movika со страницей сайта осуществляется с помощью встраивания тега <iframe>.

На странице сайта определяется местоположение тега <iframe>, который описывается следующими параметрами:   

src -  содержит URL, указывающий на путь, содержащий интерактивный видеоконтент;
width - задает ширину плеера проигрываемого видеоконтента;
height -  задает высоту плеера проигрываемого видеоконтента;
allowFullScreen - разрешает или запрещает полноэкранное воспроизведение видео.
Пример тега <iframe>, отображающего интерактивный видеопроигрыватель размером 840x560 пикселей представлен ниже:

```
 <iframe style="width:840px; height:560px" allowFullScreen src="https://movika.com/player/123Sd">
 </iframe>
```

