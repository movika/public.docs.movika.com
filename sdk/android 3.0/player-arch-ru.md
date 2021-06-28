---
title: Структура плеера
description: Структура плеера
keywords: Структура плеера
sort: 1 
---

# Структура плеера

![схема структуры плеера](player-arch.png)

**SimpleInteractivePlayer** является фасадом над основными компонентами плеера. Для более тонкой настройки плеера следует использовать основные компоненты плеера напрямую без применения **SimpleInteractivePlayer**.

### Основные компоненты плеера:

 - **CoreInteractivePlayer** - ядро плеера, отвечающее за основную логику и абстрагированное от отображения. Для его работы необходимо предоставить реализацию интерфейса **EventController** и набор интерфейсов **PlayerComponents**.
 - **EventController** - программный интерфейс отвечающий за отображение интерактивов. В SDK присутствует реализация **EventController** по-умолчанию **DefaultEventController**, которая также предоставляет некоторый набор базовых интерактивов.
 - **PlayerComponents** - класс dto содержащий набор интерфейсов для работы с видеоплеером. В SDK присутствует стандартный видеоплеер **DefaultVideoPlayer**, который может предоставить данный набор.

### Пример использования основных компонентов плеера без применения SimpleInteractivePlayer
```
...

class MainActivity : AppCompatActivity() {

    lateinit var videoPlayer: DefaultVideoPlayer
    lateinit var eventController: DefaultEventController
    lateinit var corePlayer: CoreInteractivePlayer

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val rootView = FrameLayout(this)

        /* Создаём видеоплеер */
        videoPlayer = DefaultVideoPlayer(this)
        /* Восстановливаем сохранненоё состояния видеоплеера */
        savedInstanceState?.restoreDefaultVideoPlayerState(
            BUNDLE_KEY_VIDEO_PLAYER_STATE,
            videoPlayer
        )
        /* Добавляем видео плеера на разметку */
        rootView.addView(videoPlayer.view)

        /* Создаем реализацию EventController по-умолчанию - DefaultEventController */
        eventController = DefaultEventController(
            context = this,
            scope = lifecycleScope,
            /* Опционально передаем сохраненное состояние */
            initState = savedInstanceState?.getDefaultEventControllerState(
                BUNDLE_KEY_EVENT_CONTROLLER_STATE
            )
        )
        /* Добавляем контейнер для отображения интерактивов на разметку */
        rootView.addView(eventController.view)

        /* Создаём ядро плеера CoreInteractivePlayer */
        corePlayer = CoreInteractivePlayer(
            /* Передаем набор PlayerComponents, который предоставляет DefaultVideoPlayer */
            playerComponents = videoPlayer.playerComponents,
            /* Передаем ранее созданный DefaultEventController */
            eventController = eventController,
            scope = lifecycleScope
        )

        setContentView(rootView)

        /* Далее, чтобы плеер начал воспроизведение, нужно предоставить манифест */
        val url = "https://yout_manifest_url"
        /* 
         * Создаем загрузчик по-умолчанию. Для разовой загрузки он вполне подойдет, другие более
         * оптимальные методы описаны в разделе "Оптимизация"
         */
        val loader = DefaultManifestDownloader()
        lifecycleScope.launch {
            runCatching {
                val manifest = loader.load(url)
                withContext(Dispatchers.Main) {
                    /* Передаем полученный манифест ядру плеера */
                    corePlayer.run(
                        manifest, 
                        /* опционально передаем сохраненное состояние */
                        savedInstanceState?.getPlayerState(BUNDLE_KEY_CORE_PLAYER_STATE)
                    )
                    /* Запускаем воспроизведение */
                    corePlayer.play()
                    /* Так как экземпляр DefaultManifestDownloader больше не нужен, утилизируем его */
                    loader.release()
                }
            }.onFailure {
                /* Обрабатываем ошибку загрузки */
                Log.e(LOG_TAG, "Error! $it", it)
            }
        }


    }
    
    override fun onPause() {
        super.onPause()
        /* Оповещаем плеер о достижении жизненого цикала onPause */
        corePlayer.onPause()
    }

    override fun onResume() {
        super.onResume()
        /* Оповещаем плеер о достижении жизненого цикала onResume */
        corePlayer.onResume()
    }

    override fun onDestroy() {
        super.onDestroy()
        /* Оповещаем плеер о достижении жизненого цикала onResume */
        corePlayer.onDestroy()
        /* Уничтожаем наш экземпляр DefaultVideoPlayer */
        videoPlayer.destroy()
    }

    override fun onSaveInstanceState(outState: Bundle) {
        super.onSaveInstanceState(outState)
        /* Сохраняем состояния наших компонентов */
        outState.putPlayerState(BUNDLE_KEY_CORE_PLAYER_STATE, corePlayer.getState())
        outState.putDefaultEventControllerState(BUNDLE_KEY_EVENT_CONTROLLER_STATE, eventController.getState())
        outState.saveDefaultVideoPlayerState(BUNDLE_KEY_VIDEO_PLAYER_STATE, videoPlayer)
    }

    companion object {

        const val LOG_TAG = "MainActivity"

        const val BUNDLE_KEY_VIDEO_PLAYER_STATE = "video_player_state"
        const val BUNDLE_KEY_EVENT_CONTROLLER_STATE = "event_controller_state"
        const val BUNDLE_KEY_CORE_PLAYER_STATE = "core_player_state"
    }
}
```