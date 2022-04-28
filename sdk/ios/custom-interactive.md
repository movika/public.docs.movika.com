In **MovikaSDK** two types of interaction with the movie are available: _Button_ and _Click_ on the video area. In addition to the built-in interactives, you can also add your own interactives to your projects.

Within the _SDK_, interactives are created through factories. Adding custom interactives is done through the standard implementation of **MKInteractivePlayer** and registering new factories in it. Custom interactives have a custom implementation instead of those already available.

### Add your own interactives like this:

1) Refer to the **MKDefaultsEventsContainer** class object
2) Call the _register_ method
3) In _register_, pass the interactive type (text key, for example: "fast_tap") and the **MKEventViewFactory** factory
4) The **MKEventViewFactory** factory that you pass will generate the **MKEventView** component
5) **MKEventView** is a component you will interact with in the interactive movie

[Implementation example](.../.../src/ios/custom/ViewController.txt) of a custom interactive.

### MKEventView.

This protocol is mainly responsible for the behavior and appearance of the interactives. The actions are described in the _eventResultCompletion_, and the view in the _view_ variable.
```
protocol MKEventView {
  // Transmit the result of the user interaction with the interactive.
  var eventResultCompletion: MKEventResultCompletion? { get set }
  
  // The view of the custom interactive
  var view: UIView? { get }

  // Method to be called when the interactive will disappear
  func eventViewWillDisappear()
}
``` 

### MKEventViewFactory

This protocol is responsible for creating a new type of factory, which implements a new custom interactive
```
protocol MKEventViewFactory {
  // Method that creates a new factory type
  func create(event: MKEvent, videoRect: CGRect) throws -> MKEventView?
}
```
___

The manifest is a JSON file with video data. Within the SDK, interactives are called containers. The manifest contains information about containers: type, number, time of appearance, fading, actions, etc. For example, the type of interactives is specified within the containers in the "type" column, and the name of the custom interactive is also specified there. 

[Manifest documentation](../sdk/android/custom-interactives-en.md) 
