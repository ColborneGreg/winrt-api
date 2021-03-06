---
-api-id: T:Windows.UI.Xaml.Controls.InkToolbarCustomToolButton
-api-type: winrt class
---

<!-- Class syntax.
public class InkToolbarCustomToolButton : Windows.UI.Xaml.Controls.InkToolbarToolButton, Windows.UI.Xaml.Controls.IInkToolbarCustomToolButton
-->

# Windows.UI.Xaml.Controls.InkToolbarCustomToolButton

## -description

Represents an [InkToolbar](inktoolbar.md) button that invokes a non-pen tool, defined by the host app.

## -remarks

The [InkToolbar](inktoolbar.md) consists of two distinct groups of button types:

+ One group of "tool" buttons containing the built-in drawing ([InkToolbarBallpointPenButton](inktoolbarballpointpenbutton.md), [InkToolbarPencilButton](inktoolbarpencilbutton.md)), erasing ([InkToolbarEraserButton](inktoolbareraserbutton.md)), and highlighting ([InkToolbarHighlighterButton](inktoolbarhighlighterbutton.md)) buttons. Custom tools ([InkToolbarCustomPenButton](inktoolbarcustompenbutton.md) and [InkToolbarCustomToolButton](inktoolbarcustomtoolbutton.md)) are added here.

    > Feature selection is mutually exclusive.

+ A second group of "toggle" buttons containing the built-in ruler ([InkToolbarRulerButton](inktoolbarrulerbutton.md)) button. Custom toggles ([InkToolbarCustomToggleButton](inktoolbarcustomtogglebutton.md)) are added here.

    > Features are not mutually exclusive and can be used concurrently with other active tools.

Built-in buttons can be displayed by default, or you can specify which should be displayed by your app.

> You cannot change the display order of the built-in buttons. The default display order is: [InkToolbarBallpointPenButton](inktoolbarballpointpenbutton.md), [InkToolbarPencilButton](inktoolbarpencilbutton.md), [InkToolbarHighlighterButton](inktoolbarhighlighterbutton.md), [InkToolbarEraserButton](inktoolbareraserbutton.md), and [InkToolbarRulerButton](inktoolbarrulerbutton.md), with custom tool buttons appended to the radio button group and custom toggle buttons appended to the toggle button group.

## -examples
By default, [InkPresenter](inkcanvas_inkpresenter.md) processes all input as either an ink stroke or an erase stroke. This includes input modified by a secondary hardware affordance such as a pen barrel button, a right mouse button, or similar. However, [InkPresenter](inkcanvas_inkpresenter.md) can be configured to leave specific input unprocessed, which can then be passed through to your app for custom processing.

In this example, we define a custom tool button that, when selected, causes subsequent strokes to be processed and rendered as a selection lasso (dashed line) instead of ink. All ink strokes within the bounds of the selection area are set to [Selected](../windows.ui.input.inking/inkstroke_selected.md).

The following example steps through how to enable stroke selection through a custom tool button.

> [!NOTE]
> See [Inking controls](https://msdn.microsoft.com/en-us/windows/uwp/controls-and-patterns/inking-controls) for both [InkCanvas](inkcanvas.md) and [InkToolbar](inktoolbar.md) UX guidelines. The following recommendation is relevant to this example:
+ If providing stroke selection, we recommend using the "EF20" icon from the "Segoe MLD2 Assets" font for the tool button, with a "Selection tool" tooltip.


First, we set up the UI in MainPage.xaml.


+ We declare an [InkToolbarCustomToolButton](inktoolbarcustomtoolbutton.md) element (`customToolButton`) with a [Click](../windows.ui.xaml.controls.primitives/buttonbase_click.md) event listener that specifies the event handler (`customToolButton_Click`) where stroke selection is configured. (We've also added a set of buttons for copying, cutting, and pasting the stroke selection.)
+ We also add a [Canvas](canvas.md) element for drawing our selection stroke. Using a separate layer to draw the selection stroke leaves the [InkCanvas](inkcanvas.md) and its content untouched.




[TODO:AUTO_SNIPPET (SAMPLE_ID:Ink_Basic_InkToolbar)(SNIPPET_ID:UI_AddCustomTool)]We then handle the [Click](../windows.ui.xaml.controls.primitives/buttonbase_click.md) event for the [InkToolbarCustomToolButton](inktoolbarcustomtoolbutton.md) in the `MainPage.xaml.cs` code-behind file.

This handler configures the [InkPresenter](inkcanvas_inkpresenter.md) to pass unprocessed input through to the app.



> **For a more detailed step through of this code**
> See the [Pass-through input for advanced processing](https://msdn.microsoft.com/en-us/windows/uwp/input-and-devices/pen-and-stylus-interactions#pass-through-input-for-advanced-processing) section of [Pen interactions and Windows Ink in UWP apps](https://msdn.microsoft.com/en-us/windows/uwp/input-and-devices/pen-and-stylus-interactions).

We also specified an icon for the button using the [SymbolIcon](symbolicon.md) element and the [{x:Bind} markup extension](http://msdn.microsoft.com/library/529fbeb5-e589-486f-a204-b310acdc5c06) that binds it to a field defined in the code-behind file (`SelectIcon`).

The following snippet includes both the [Click](../windows.ui.xaml.controls.primitives/buttonbase_click.md) event handler and the definition of `SelectIcon` for this example.



[TODO:AUTO_SNIPPET (SAMPLE_ID:Ink_Basic_InkToolbar)(SNIPPET_ID:CustomToolMain)]

## -see-also
[Windows.UI.Xaml.Controls classes](windows_ui_xaml_controls_classes.md)