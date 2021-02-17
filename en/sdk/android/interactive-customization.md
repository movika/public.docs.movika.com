---
title: Interactive customization
description: Interactive customization
keywords: Interactive customization
sort: 8
---

# Interactive customization

Developer may want to create their own interactive types. This can be done either in a simple or complete way.

#### The simple way

The simple way is designed for processing custom interactives. The type variable should be declared with value "custom", and
customType field takes your custom value. E.g.:

Original manifest:

```
{
...
    actions: [
    ...
        {
        ...
        "type": "custom",
        "customType": "your_type",
        ...
        }
    ...
    ]
...
}
```

If the manifest file in .json format is not used, but the MovieBundle is created manually in code,
then your custom InteractiveEvent will look like this:

```
InteractiveEvent (
...
    type = InteractiveType.CUSTOM,
    customType = "your_type"
...
)
```

- For each different customType value, create a class that inherits from CustomEventView. This class is described in more detail below.
- Then implement CustomEventViewFactory to provide instances of these classes based on customType value.
- At last, you need to pass your custom factory to the InteractivePlayerView instance by setting ** customEventViewFactory ** field.

##### CustomEventView

It is an implementation of a custom interactive type that was created in a simple way.
Constructor receives an object of Parcelable type or null. Using this object
you can restore the state after re-creation. Developer must provide this object himself,
by overriding the ** open fun onSaveState (): Parcelable ** method.
Another parameter is an object of the ** CustomEventResultCallback ** type.
It is required for interaction with sdk. See CustomEventResultCallback section for more details.
Optionally, the CustomEventView constructor can be called with following parameters:
isDeatachOnTimeout - a flag indicating whether the interactive should be detached from the screen after specified time.
By default is true. If false, developer will need to manually detach it.
This can be done using the CustomEventResultCallback, which will be discussed later. Also, if the value of the given
flag is false, developer may find it useful to override the ** open fun onTimeOut () ** method, which is called when
interactive time is expired.
isSeekable - flag indicating whether the video can be rewound during interactive.

Also in this class, you need to override the field

`abstract val view: View`

This field contains an instance of the View class, which serves as visual part of the interactive.

#### CustomEventResultCallback

This class is used to interact with the SDK. An object of this type is passed in the constructor of CustomEventView class. This interface
provides 2 methods:

`fun onResult (chapterId: String, switchStrategy: SwitchStrategy = SwitchStrategy.DEFAULT)` - defines the next chapter.
It serves as a signal that the user has made an interaction with the interactive and the further outcome of events is now
defined. It should be called only once.
The optional parameter in this method is switchStrategy. Possible values:

- DEFAULT - video switch strategy is determined in the manifest file
- AWAIT - the current video will be played till the end, then the selected chapter will begin
- IMMEDIATELY - switch videos immediately without waiting for the current video to end.

`fun onComplete ()` - notifies about the completion of the interactive. When called, the interactive will be removed from the screen.

#### CustomEventViewFactory

Factory for creating 'CustomEventView's. It provides custom interactives that have been implemented
in a simple way.
Contains one method:

`fun create (event: InteractiveEvent, customEventResultCallback: CustomEventResultCallback, savedState: Parcelable?): CustomEventView`

The method accepts an InteractiveEvent with a description of the interactive, a CustomEventResultCallback for interacting with the sdk, and a saved state, if any.
The necessary information for creating custom interactives, e.g. tags and name, can be obtained from an instance of the InteractiveEvent class.

#### Full method (** Temporarily not supported **):

This method is a little more complicated to implement than the simple method, but it is more flexible and native-oriented. To use this method, you need the following:

- Create a class that inherits InteractiveView

- Create a class that inherits InteractivePresenter

- Create a class that implements InteractiveFactory

- Provide a class that implements InteractiveFactory by setting the value of the interactiveFactory variable in the InteractivePlayerView