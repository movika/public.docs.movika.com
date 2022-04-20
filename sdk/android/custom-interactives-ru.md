---
title: Пользовательские интерактивы
description: Создание пользовательских интерактивов
keywords: Пользовательские интерактивы, кастомные интерактивы, пользовательские контейнеры, пользовательские контролы, кастомные контейнеры, кастомные контролы
sort: 6
---


# Фабрика пользовательских контейнеров
В рамках SDK интерактивы именуются контейнерами.
У каждого контейнера есть свой набор свойств.
В SDK предусмотрена возможность добавление таких контейнеров.
Добавление пользовательских контейнеров с помощью фабрик актуален, если 
используется **SimpleInteractivePlayer**, либо стандартная реализация _EventController_ 
**DefaultEventController**.  
**SimpleInteractivePlayer** и **DefaultEventController** реализуют интерфейс **ContainerFactoryProvider**  
Через методы данного интерфейса происходит добавление фабрик.

## ContainerFactoryProvider
Методы **ContainerFactoryProvider**  
    
    /** Добавление фабрики */
    fun addContainerFactory(item: FactoryItem)

    /** Удаление фабрики */
    fun removeContainerFactory(item: FactoryItem): Boolean

    /** Получить список всех фабрик */
    fun getAllContainerFactories(): List<FactoryItem>
    
    /** Удалить все фабрики */
    fun removeAllContainerFactories()

Будьте аккуратны!  
**SimpleInteractivePlayer** и **DefaultEventController** уже 
содержат одну фабрику для создания стандартных контейнеров. При вызове _removeAllContainerFactories_ 
эта фабрика будет удалена. Этот метод стоит вызывать, если не планируется использовать
стандартные контейнеры, либо необходимо предоставить пользовательскую реализацию стандартных контейнеров.

### FactoryItem
**ContainerFactoryProvider** оперирует объектами **FactoryItem**  
Структура класса **FactoryItem**:

    data class FactoryItem(
        val factory: ContainerFactory, 
        val priority: Float = 1f
    )

- _factory_ - фабрика контейнеров
- _priority_ - приоритет фабрики. Может быть любым значением с плавающей запятой.
При создании контейнера происходит перебор фабрик от большего к меньшему. Остановка 
происходит тогда, когда одна из фабрик смогла создать контейнер с заданным типом

## ContainerFactory
Интерфейс для создания контейнера.  
Описание интерфейса:  

    interface ContainerFactory {
        fun create(data: ContainerData, callback: EventCallback): ControlContainer?
    }

Интерфейс содержит всего один метод create. Данный метод создает экземпляр класса **ControlContainer**, 
необходимый для отображения контейнера на экране. Если реализация интерфейса не может
создать контейнер, основываясь на переданных данных, то следует вернуть _null_.  
Для создания контейнера передаются два параметра.  
- **ContainerData** - данные необходимые для создания контейнера.
- **EventCallback** - интерфейс для взаимодействия с логикой интерактивного плеера.

Возвращаемое значение является экземпляром класса, унаследованного от 
абстрактного класса ControlContainer. Данный класс отвечает за логику и отображение
контейнера. Абстрактный класс ControlContainer будет рассмотрен далее.

### ContainerData
Данный класс содержит в себе данные необходимые для создания контейнера.
Описание класса:

    data class ContainerData(
        val container: Container,
        val currentTime: Long,
        val history: History?,
        val state: Parcelable? = null
    )

- _container_ - информация о контейнере, которая была получена из манифеста
- _currentTime_ - Текущее время проигрываемой главы в миллисекундах
- _history_ - история прохождения. Иными словами, запись действий пользователя
- _state_ - сохраненное состояние. Необходимо для реализации восстановления состояния
после смены конфигурации.

Структура класса **Container** рассмотрена в разделе [Структура данных](data-structure-ru.md)

### EventCallback
Интерфейс для взаимодействия с логикой интерактивного плеера.  
Описание интерфейса


    fun interface EventCallback {
        fun onEvent(eventInvocation: EventInvocation)
    }

Если контейнеру необходимо оповестить логику интерактивного плеера о том,
что произошло какое-то событие (пользователь нажал кнопку и т.п.), то контейнеру
необходимо вызвать метод _onEvent_ передав объект **EventInvocation**, который описывает событие

#### EventInvocation
Класс, описывающий произошедшее событие

Описания класса EventInvocation

    class EventInvocation(
        /** Контейнер, который отослал данное событие */
        val container: Container,
        val event: Event,
        val blame: Control?
    )

Структуры классов **Event** и **Control** рассмотрены в разделе [Структура данных](data-structure-ru.md)

## ControlContainer

Для реализации логики и отображения контейнера, необходимо создать собственны класс, 
который должен быть унаследован от абстрактного класс ControlContainer

### Доступные поля
- ```val isAttached: Boolean``` - равняется true, если контейнер прикреплен к экрану (отображается на экране)
- ```val isDetached: Boolean``` - равняется true, если контейнер **был** откреплен от экрана
- ```protected val isPaused: Boolean``` - равняется true, если воспроизведение находится на паузе
- ```protected val lastPlaybackState: PlaybackStateListener.PlaybackState``` - хранит последнее известное состояние плеера
- ```open var autoRemoveView: Boolean = true``` - означает, удалять ли автоматически отображение при вызове detach().
Если выставить значение false, то необходимо самим позаботиться об удалении View с экрана. Для этого
необходимо вызвать метод removeView(). Внимание, при значении false нет никакой гарантии, что View не будет удалена
принудительно игровой логикой.

### Доступные методы
- ```open fun getView(): View?``` - возвращает класс View, либо его наследник, либо null. Иными словами, возвращается 
визуальное представление, которое будет помещено на экран. При унаследовании от 
класса ControlContainer, необходимо переопределить данный метод для возможности отображения данного контейнера на экране
- ```open getState(): Parcelable?``` - данный метод необходим для возможности сохранения состояния контейнера
при смене конфигурации или уничтожения Activity. При необходимости сохранения состояния 
необходимо переопределить данный метод, затем, как один из возможных вариантов, в конструкторе класса, унаследованного 
от ControlContainer, добавить параметр с типом Parcelable и передавать сохраненное состояние из вашей фабрики 
контейнеров (из класса ContainerData) в унаследованный от ControlContainer класс через конструктор
- ```fun onAttach()``` - вызывается после размещения контейнера на экране
- ```fun onPlay(time: Long)``` - вызывается, когда плеер переходит в состояние воспроизведения
- ```fun onPause(time: Long)``` - вызывается, когда плеер переходит в состояние паузы
- ```fun onDestroy()``` - вызывается при уничтожении интерактивного плеера
- ```fun onDetach()``` - вызывается при откреплении (исчезновении) контейнера с экрана
- ```protected fun runOnUi(task: () -> Unit)``` - вспомогательны метод, для возможности вызова действий в UI потоке
- ```fun removeView()``` - метод для ручного удаления отображения контейнера с экрана

# Рекомендации
Система внедрение пользовательских контейнеров достаточно гибкая.
Никто не мешает реализовывать отображение и расположение элементов
как угодно, но всё же, лучше следовать принятым в SDK best practice.

1. Не пренебрегайте указанными Control в Container. Используйте Control для создания ControlView
ориентируясь на поле **type**. Если вам достаточно стандартных реализаций ControlView, то вы можете воспользоваться
специальной фабрикой для их создания **DefaultControlViewFactory**. Следующий пункт в списке
позволит понять, как их размещать на экране. Более подробно про **ControlView** описано далее. 
2. Не пренебрегайте указанным Layout в Container. Более подробно
про Layout можно почитать в разделе [Структура данных](data-structure-ru.md). Если вам достаточно
типов Layout, что идут в комплекте с SDK, то вы можете воспользоваться стандартной фабрикой
**DefaultControlLayout**, которая позволяет создавать экземпляры ControlLayout. ControlLayout
необходим для расположения ControlView, которые были затронуты ранее. Рекомендуется полеченный View
вызовом метода getView у ControlLayout возвращать в методе getView вашей реализации ControlContainer.
Описание интерфейса ControlLayout:


    interface ControlLayout {
        fun getView(): View
    
        fun add(controlView: ControlView, layoutParams: LayoutParams?)
    
        fun add(controlViews: List<Pair<ControlView, LayoutParams?>>) {
            controlViews.forEach { add(it.first, it.second) }
        }
    }

## ControlView
ControlView по смыслу, является составным элементом
ControlContainer. ControlContainer решает, как расположить в себе ControlView.

Описание интерфейса ControlView:

    interface ControlView {
        fun getView(): View
        fun setEventCallback(callback: ControlEventCallback)
    }

- ```fun getView(): View``` - возвращает отображение
- ```fun setEventCallback(callback: ControlEventCallback)``` - устанавливает колбек
для передачи событий над ControlView

Описание ControlEventCallback:

    fun interface ControlEventCallback {
        fun onEvent(event: Event)
    }