---
-api-id: T:Windows.UI.Input.Inking.InkDrawingAttributes
-api-type: winrt class
-api-device-family-note: xbox
---

<!-- Class syntax.
public class InkDrawingAttributes : Windows.UI.Input.Inking.IInkDrawingAttributes, Windows.UI.Input.Inking.IInkDrawingAttributes2, Windows.UI.Input.Inking.IInkDrawingAttributes3, Windows.UI.Input.Inking.IInkDrawingAttributes4
-->

# Windows.UI.Input.Inking.InkDrawingAttributes

## -description
Provides properties associated with the drawing of an [InkStroke](inkstroke.md).

## -remarks
[InkDrawingAttributes](inkdrawingattributes.md) can be set globally through the [SetDefaultDrawingAttributes](inkmanager_setdefaultdrawingattributes_1436218448.md) method of an [InkManager](inkmanager.md) object or an [InkStrokeBuilder](inkstrokebuilder.md) object. They can also be set on an individual [InkStroke](inkstroke.md) object through the [DrawingAttributes](inkstroke_drawingattributes.md) property.

> [!NOTE]
> : This class is not agile, which means that you need to consider its threading model and marshaling behavior. For more info, see [Threading and Marshaling (C++/CX)](http://go.microsoft.com/fwlink/p/?linkid=258275) and [Using Windows Runtime objects in a multithreaded environment (.NET)](http://go.microsoft.com/fwlink/p/?linkid=258277).

## -examples
The following example demonstrates how to set a default drawing attribute for all strokes managed by an [InkManager](inkmanager.md) object (`inkManager`).

```javascript

var inkManager = new Windows.UI.Input.Inking.InkManager();
var drawingAttributes = 
     new Windows.UI.Input.Inking.InkDrawingAttributes();
// True is the Default value for fitToCurve.
drawingAttributes.fitToCurve = false;
// Set color to red (default is black).
drawingAttributes.color = 
     Windows.UI.ColorHelper.fromArgb(255, 255, 0, 0); 
inkManager.setDefaultDrawingAttributes(drawingAttributes);

```

```csharp
// Create the InkManager instance.
Windows.UI.Input.Inking.InkManager inkManager = 
  new Windows.UI.Input.Inking.InkManager();
Windows.UI.Input.Inking.InkDrawingAttributes drawingAttributes = 
  new Windows.UI.Input.Inking.InkDrawingAttributes();
// True is the Default value for fitToCurve.
drawingAttributes.FitToCurve = false;
// Set color to red (default is black).
drawingAttributes.Color = Windows.UI.Colors.CornflowerBlue;
inkManager.SetDefaultDrawingAttributes(drawingAttributes);

```

The following example demonstrates how to set a drawing attribute for a specific stroke.

> [!NOTE]
> You cannot set the [DrawingAttributes](inkstroke_drawingattributes.md) property of the stroke directly. You must create a copy of the [InkDrawingAttributes](inkdrawingattributes.md) of the stroke, set the desired values for that [InkDrawingAttributes](inkdrawingattributes.md) object, and then assign the new [InkDrawingAttributes](inkdrawingattributes.md) to the [DrawingAttributes](inkstroke_drawingattributes.md) of the stroke, as shown here.

```javascript
inkManager.getStrokes().forEach(function (stroke)
{
  var drawingAttributes = stroke.drawingAttributes;
  drawingAttributes.penTip = 
       Windows.UI.Input.Inking.PenTipShape.rectangle;
  stroke.drawingAttributes = drawingAttributes;
}
```

```csharp

// Get the InkStroke objects.
IReadOnlyList<InkStroke> inkStrokes = inkManager.GetStrokes();
Windows.UI.Input.Inking.InkStroke cloneStroke = 
  inkStrokes.GetAt(index).Clone();
Windows.UI.Input.Inking.InkDrawingAttributes drawingAttributes = 
  cloneStroke.DrawingAttributes;
drawingAttributes.PenTip = Windows.UI.Input.Inking.PenTipShape.Rectangle;
cloneStroke.DrawingAttributes = drawingAttributes;
```

For the complete example, see [Ink App sample](http://go.microsoft.com/fwlink/p/?linkid=231622).

## -see-also
[Windows.UI.Input.Inking.InkManager.SetDefaultDrawingAttributes](inkmanager_setdefaultdrawingattributes_1436218448.md), [Windows.UI.Input.Inking.InkStroke.DrawingAttributes](inkstroke_drawingattributes.md), [UI.Xaml.Controls.InkToolbar.InkDrawingAttributes](../windows.ui.xaml.controls/inktoolbar_inkdrawingattributes.md), [Pen and stylus interactions](http://msdn.microsoft.com/library/3da4f2d2-5405-42a1-9ed9-3a87bcd84c43), [Get started: Support ink in your UWP app](https://docs.microsoft.com/en-us/windows/uwp/get-started/ink-walkthrough), [Ink analysis sample (basic) (C#)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-analysis-basic.zip), [Ink handwriting recognition sample (C#)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-handwriting-reco.zip), [Save and load ink strokes from an Ink Serialized Format (ISF) file](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store.zip), [Save and load ink strokes from the clipboard](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-store-clipboard.zip), [Ink toolbar location and orientation sample (basic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness.zip), [Ink toolbar location and orientation sample (dynamic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-ink-toolbar-handedness-dynamic.zip), [Coloring book sample](https://aka.ms/cpubsample-coloringbook), [Family notes sample](https://aka.ms/cpubsample-familynotessample), [Inking sample (JavaScript)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Ink), [Simple inking sample (C#/C++)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleInk), [Complex inking sample (C++)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ComplexInk), [Ink analysis sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/InkAnalysis)

