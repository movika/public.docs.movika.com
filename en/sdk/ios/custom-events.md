---
title: Custom interactives
description: Custom interactives
keywords: Custom interactives
sort: 3
---

# Custom interactives

1. A view (interactive) is created, in most cases it inherited from UIView
2. The interactive class implements CustomEventViewProtocol protocol
3. The InteractiveEvent structure is passed to the interactive constructor, which contains basic information of the interactive (start time, end time, list of available story development options, type, etc.)

```
    public let id: Int
    public let chapterId: Int

    \\ Interactive type, always .custom for custom interactions
    public let type: InteractiveType

    \\ For custom interactives, any value can be specified that 
	\\ will identify your custom interactive, for example
    \\ "push_red_button"
    public let customType: String?

    \\ Start time of the interactive
    public let time: Double

    \\ The time after which the interactive will be removed from the scene
    public let timeout: Double

    \\ Additional data for embedded interactions
    public let eventData: EventData

    \\ Interactive header
    public let header: String

    \\ Interactive playbackType (for example interactives that should stop playback)
    public let playbackType: PlaybackType

    \\ Additional data is transferred to play custom
    \\ interactive
    public var tags: [String]?

```

4. The CustomEventResultDelegate class is passed to the interactive constructor, which allows you to transfer the result of user interaction with the interactive
5. By calling the resultSelected (index: Int) method, the interactive will transfer the result, after which it will be instantly removed from the scene
6. If you need to pass the result first and then display some animation, use the resultSelected (index: Int, instantlyDetach: true) methods, then after the animation completes use the detachFromParent () method
7. To create custom interactives, when creating a player controller, you need to pass a factory that creates a specific interactive based on customType
8. The custom interactive factory must implement CustomEventViewFactory protocol.
