---
-api-id: T:Windows.ApplicationModel.Activation.FileSavePickerActivatedEventArgs
-api-type: winrt class
---

<!-- Class syntax.
public class FileSavePickerActivatedEventArgs : Windows.ApplicationModel.Activation.IActivatedEventArgs, Windows.ApplicationModel.Activation.IActivatedEventArgsWithUser, Windows.ApplicationModel.Activation.IFileSavePickerActivatedEventArgs, Windows.ApplicationModel.Activation.IFileSavePickerActivatedEventArgs2
-->

# Windows.ApplicationModel.Activation.FileSavePickerActivatedEventArgs

## -description
Provides information about an activated event that fires when the user saves a file through the file picker and selects the app as the location.

> **JavaScript**
> This type appears as [WebUIFileSavePickerActivatedEventArgs](../windows.ui.webui/webuifilesavepickeractivatedeventargs.md).

## -remarks
Learn more about providing your app as a location where the user can save files in the [Windows.Storage.Pickers.Provider](../windows.storage.pickers.provider/windows_storage_pickers_provider.md) namespace reference.

A [FileSavePickerActivatedEventArgs](filesavepickeractivatedeventargs.md) object is passed to the app's activation point handler when the user saves a file through the file picker and selects the app as the location. This type of activation is indicated by the [ActivationKind.FileSavePicker](activationkind.md) value returned by the [Kind](filesavepickeractivatedeventargs_kind.md) property.

Apps written in JavaScript must listen for and handle [Windows.UI.WebUI.webUIApplication.activated](../windows.ui.webui/webuiapplication_activated.md) events.


<!--{annotation author="wolfs" time="10/23/2012 2:39:33 PM"}This isn't correct. The jupiter app model wires this up for you when they instantiate the Application object on the main STA. You handle activation scenarios by overriding the On* methods of Application. You don't ever have to use anything from the CoreApplication / Core namespace for all but the most fringe/advanced scenarios.-->
Windows Store app using C++, C#, or Visual Basic typically implement activation points by overriding methods of the [Application](../windows.ui.xaml/application.md) object. The default template app.xaml code-behind files always include an override for [OnLaunched](../windows.ui.xaml/application_onlaunched.md), but defining overrides for other activation points such as [OnFileSavePickerActivated](../windows.ui.xaml/application_onfilesavepickeractivated.md) is up to your app code.

All [Application](../windows.ui.xaml/application.md) overrides involved in an activation scenario should call [Window.Activate](../windows.ui.xaml/window_activate.md) in their implementations.

## -examples
The [File picker contracts sample](http://go.microsoft.com/fwlink/p/?linkid=231536) demonstrates how to respond to a **FileSavePicker** activation point.

```csharp

// fileSavePicker activated event handler
protected override void OnFileSavePickerActivated(FileSavePickerActivatedEventArgs args)
{
    var FileSavePickerPage = new SDKTemplate.FileSavePickerPage();
    FileSavePickerPage.Activate(args);
}

// Overloaded method to respond to fileSavePicker events
internal void Activate(FileSavePickerActivatedEventArgs args)
{
    // Perform tasks to prepare your app to display its file picker page

    // Get file picker UI
    fileSavePickerUI = args.FileSavePickerUI;

    Window.Current.Content = this;
    this.OnNavigatedTo(null);
    Window.Current.Activate();
}
```

For C#, `args` for an [OnFileSavePickerActivated](../windows.ui.xaml/application_onfilesavepickeractivated.md) override on the [Application](../windows.ui.xaml/application.md) object references a [FileSavePickerActivatedEventArgs](filesavepickeractivatedeventargs.md) object. The [OnFileSavePickerActivated](../windows.ui.xaml/application_onfilesavepickeractivated.md) override is in the App.xaml.cs file and the `Activate` method is in the FileSavePickerPage.xaml.cs file of the [File picker contracts sample](http://go.microsoft.com/fwlink/p/?linkid=231536).

## -see-also
[Windows.Storage.Pickers.Provider namespace](../windows.storage.pickers.provider/windows_storage_pickers_provider.md), [Windows.UI.WebUI.WebUIApplication.Activated event](../windows.ui.webui/webuiapplication_activated.md), [Windows.UI.Core.CoreApplicationView.Activated event](../windows.applicationmodel.core/coreapplicationview_activated.md), [OnFileSavePickerActivated](../windows.ui.xaml/application_onfilesavepickeractivated.md), [Application](../windows.ui.xaml/application.md), [File picker contracts sample](http://go.microsoft.com/fwlink/p/?linkid=231536), [File picker provider sample (Windows 10)](http://go.microsoft.com/fwlink/p/?LinkId=620543)