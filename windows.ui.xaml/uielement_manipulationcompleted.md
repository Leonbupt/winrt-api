---
-api-id: E:Windows.UI.Xaml.UIElement.ManipulationCompleted
-api-type: winrt event
---

<!-- Event syntax
public event Windows.UI.Xaml.Input.ManipulationCompletedEventHandler ManipulationCompleted
-->

# Windows.UI.Xaml.UIElement.ManipulationCompleted

## -description
Occurs when a manipulation on the [UIElement](uielement.md) is complete.

## -xaml-syntax
```xaml
<uiElement ManipulationCompleted="eventhandler"/>
```


## -remarks

For custom controls and interaction experiences, see [GestureRecognizer.ManipulationCompleted](../windows.ui.input/gesturerecognizer_manipulationcompleted.md).

An element must have a [ManipulationMode](uielement_manipulationmode.md) value other than **None** or **System** to be a manipulation event source. The default value of [ManipulationMode](uielement_manipulationmode.md) is **System**, which enables built-in control logic to process manipulations, but doesn't permit app code to handle manipulation events. If you want to handle manipulations, set [ManipulationMode](uielement_manipulationmode.md) to **All**, or to specific [ManipulationModes](../windows.ui.xaml.input/manipulationmodes.md) values. For more info, see [ManipulationMode](uielement_manipulationmode.md).

[ManipulationCompleted](uielement_manipulationcompleted.md) is a routed event. If the event is permitted to bubble up to parent elements because it goes unhandled, then it is possible to handle the event on parent elements even if [ManipulationMode](uielement_manipulationmode.md) is **None** or **System** on the parent element. For more info on the routed event concept, see [Events and routed events overview](http://msdn.microsoft.com/library/34c219e8-3efb-45bc-8bbd-6fd937698832).

For touch actions and also for interaction-specific or manipulation events that are consequences of a touch action, an element must be hit-test visible in order to be the event source and fire the event that is associated with the action. [UIElement.Visibility](uielement_visibility.md) must be [Visible](visibility.md). Other properties of derived types also affect hit-test visibility. For more info, see [Events and routed events overview](http://msdn.microsoft.com/library/34c219e8-3efb-45bc-8bbd-6fd937698832).

[ManipulationCompleted](uielement_manipulationcompleted.md) supports the ability to attach event handlers to the route that will be invoked even if the event data for the event is marked [Handled](../windows.ui.xaml.input/manipulationcompletedroutedeventargs_handled.md). See [AddHandler](uielement_addhandler_2121467075.md).


<!--The following remark is relevant for Windows 8 > 8.1 migration. See WBB 467590-->
### Windows 8 behavior

Windows 8 doesn't fire [ManipulationCompleted](uielement_manipulationcompleted.md) in cases where the inertial phase has started (and [ManipulationInertiaStarting](uielement_manipulationinertiastarting.md) has fired) but the user has tapped on the item before it's finished scrolling, which cancels the inertial phase visually. The issue is fixed starting with Windows 8.1; [ManipulationCompleted](uielement_manipulationcompleted.md) is fired as soon as the tap action cancels the inertial phase.

Apps that were compiled for Windows 8 but running on Windows 8.1 continue to use the Windows 8 behavior.

## -examples

## -see-also
[ManipulationStarted](uielement_manipulationstarted.md), [ManipulationStarting](uielement_manipulationstarting.md), [OnManipulationCompleted](../windows.ui.xaml.controls/control_onmanipulationcompleted_955700152.md), [Using manipulation events](http://msdn.microsoft.com/library/f10bafee-8792-4a57-ae84-aa11ab95355a), [XAML user input events sample](http://go.microsoft.com/fwlink/p/?linkid=231524)