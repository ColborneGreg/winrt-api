---
-api-id: M:Windows.UI.Xaml.Interop.IBindableVectorView.GetAt(System.UInt32)
-api-type: winrt method
---

<!-- Method syntax
public object GetAt(System.UInt32 index)
-->

# Windows.UI.Xaml.Interop.IBindableVectorView.GetAt

## -description
Returns the item at the specified index in the vector.

## -parameters
### -param index
The zero-based index of the item in the vector to return.

## -returns
The item at the specified index.

## -remarks
This interface supports the creation of data bindable collections in C++. When programming with .NET, you should use [ObservableCollection(Of T)](XREF:TODO:T:System.Collections.ObjectModel.ObservableCollection`1) or implement [IList](https://msdn.microsoft.com/library/system.collections.ilist.aspx) and [INotifyCollectionChanged](https://msdn.microsoft.com/library/system.collections.specialized.inotifycollectionchanged.aspx).

## -examples

## -see-also
[XAML data binding sample](http://go.microsoft.com/fwlink/p/?linkid=226854)