# Overview of WPF & UWP Differences

The Universal Windows Platform (UWP) has its roots in SilverLight instead of being based on the Windows Presentation Foundation (WPF). UWP is implemented natively in C++ instead of WPF which was written in C# and C++ for lower-level functions. Due to being completely different imlementations of XAML there are several differences in UWP compared to WPF. These differences may be new functionalitly, slightly different ways of doing things or, more commonly, WPF features missing in UWP. These differences are not documented by Microsoft as a summary which is prohibite for developers familiar with WPF and have to port existing code. This document is intended to provide an overview of the differences.

## XAML Features

This section lists the main differences (primarily from a XAML viewpoint) between UWP and WPF. A check under the WPF or UWP column indicates the platform has the feature. An 'X' means the feature is missing or, in some cases, is not as powerful.

### XAML Markup Extension

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>x:Uid for localization</td>
  <td>&#10006;</td>
  <td>&#10004;</td>
  <td>x:uid is a powerful localization system similar to what exists in Windows Forms. WPF is sorely missing this type of localization support. This is a clear advantage of UWP.</td>
 </tr>
 <tr>
  <td>x:Bind</td>
  <td>&#10006;</td>
  <td>&#10004;</td>
  <td>x:Bind has also become a powerful feature of UWP over WPF. Compiled bindings can be used for nearly anything and can replace other missing features like MultiBinding. Other advantages include debugging support as well as increased performance.</td>
 </tr>
  <tr>
  <td>x:Array</td>
  <td></td>
  <td></td>
  <td>x:Array isn't supported in UWP.</td>
 </tr>
 <tr>
  <td>x:Static</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td></td>
 </tr>
 <tr>
  <td>x:Type</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td></td>
 </tr>
 <tr>
  <td>Full Markup Extension</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>UWP only implements a subset of the full markup extension support in WPF. This area needs to be expanded upon in the future.</td>
 </tr>
</table>
 
### Binding
 
<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>OneWayToSource BindingMode</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td></td>
 </tr>
 <tr>
  <td>Binding to ConverterParameter</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td></td>
 </tr>
 <tr>
  <td>MultiBinding /
  IMultiValueConverter</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>Very useful feature in WPF for advanced binding scenearios no longer exists for UWP. UWP does have function binding with x:Bind though (Used to re-implement converter logic).</td>
 </tr>
 <tr>
  <td>ICommand</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>While the interface technically xists, ICommand is nothing like what it was in WPF. The programmer is now responsible for doing every little part of the command.</td>
 </tr>
</table>

### Styling

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>DataTriggers</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td></td>
 </tr>
 <tr>
  <td>VisualStateManager</td>
  <td>&#10006;</td>
  <td>&#10004;</td>
  <td>A different concept from WPF that takes the place of DataTriggers, this is very verbose and more often than not increases complexity compared to data triggers.

@Felix-Dev VisualStateManager does exist in WPF (it was added in .NET Framework 4.0). It's not as elegant as in UWP though, i.e. it has no VisuaStateManager.Setters property. That means you have to use Storyboards to set your values.</td>
 </tr>
 <tr>
  <td>Implicit DataTemplate</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>Set the DataType property of the DataTemplate to the corresponding type and the template is then applied automatically to all instances of that particular type</td>
 </tr>
 <tr>
  <td>Binding in Style setter</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>Any other than TemplateBinding isn't support in a template/style within UWP</td>
 </tr>
 <tr>
  <td>BasedOn</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>BasedOn={StaticResource {x:Type TextBlock} isn't supported in UWP</td>
 </tr>
</table>

### Other

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>LayoutTransform</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>Layout transform is needed to transform elements before layouting. This allows for easily changing textbox direction and then putting it in a table. RenderTransform, as it applies after layout, does not resize parent controls for transformed children.</td>
 </tr>
 <tr>
  <td>Window</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>For some good reasons UWP has no concept of a window. This is fine for mobile devices but can be a problem for purely desktop applications.</td>
 </tr>
 <tr>
  <td>Custom Cursor at runtime</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td></td>
 </tr>
 <tr>
  <td>Sub-pixel anti-aliasing</td>
  <td>&#10004;</td>
  <td>&#10006;</td>
  <td>Anti-aliasing in UWP along with rendering in general is poor compared to WPF. It's assumed this is for performance reasons on mobile devices and the web (silverlight).</td>
 </tr>
</table>
 
## Other Quirks

 * Several UWP controls have reentrancy issues. For example, changing the selected item while in a ComboBox SelectionChanged event is largely not possible and will result in a crash. This makes validation directly in the event handler nearly impossible.
 * UWP controls are generally not as powerful as the WPF counterparts. For example, for several years the ComboBox in UWP was not editable. The UWP DatePicker also does not allow typing in a specific date.
 * The UWP styling system is different enough from WPF to require extra effort during porting. UWP uses the VistualStateManger instead of concepts like DataTriggers or EventTriggers from WPF. Styling/Templating are one of the main differences.
 * UWP seems to follow only the XAML/2006 spec instead of [XAML/2009]((https://docs.microsoft.com/en-us/dotnet/desktop-wpf/xaml-services/xaml-2009-language-features)) supported by WPF 
 * Several UWP controls are sealed and new controls cannot derive from them

## Object Model Differences

<table>
 <tr>
   <th>Item</th>
   <th>Difference</th>
 </tr>
 <tr>
  <td>Thickness</td>
  <td>The Thickness struct exposes fields for Top, Bottom, Left and Right instead of dependency properties as in WPF. This means you cannot Bind or asign resources to an individual thickness parameter.</td>
 </tr>
</table>

## Controls

This section describes the differences in controls in vanilla WPF and UWP. Note that this section is likely incomplete and needs further review.

TODO

### References

 1. http://dansuleski.com/so-what-else-could-be-missing-in-uwp/
 2. https://github.com/microsoft/microsoft-ui-xaml/issues/719

