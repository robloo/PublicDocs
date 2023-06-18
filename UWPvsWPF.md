最后更新时间 2021年11月06日  | 使用 CC BY-SA 4.0 协议分发

# WPF 与 UWP 区别总览

通用 Windows 平台（UWP）起源于 SilverLight，而不是基于 Windows Presentation Foundation（WPF）。UWP 是用 C++ 实现的，而不是用 C# 和 C++（底层功能）编写的 WPF。UWP 由于是一个完全不同的 XAML 实现，旨在包括更多的资源限制的设备，并支持更多的编程语言，UWP 与 WPF 相比有几个不同之处。这些差异可能是 UWP 的新功能，稍微不同的做事方式，或者更常见的是 UWP 中缺少的 WPF 功能。这些差异并没有被微软总结出来，这对熟悉 WPF 的开发者来说是一个障碍，他们必须要移植现有的代码。本文档旨在提供一个差异的概述。

## XAML / 对象模型

This section lists the main differences (primarily from a XAML viewpoint) between UWP and WPF. 

Legend:

 * ✔ Indicates the platform (defined by the WPF or UWP column) has the feature
 * ❌ Indicates the feature is generally missing in the platform
 * ⚡ Indicates the feature is only partially implemented compared to other platforms

### Markup Extensions & Directives

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>x:Array Extension</td>
  <td>✔</td>
  <td>❌</td>
  <td>x:Array isn't supported in UWP.</td>
 </tr>
 <tr>
  <td>x:Bind Extension</td>
  <td>❌</td>
  <td>✔</td>
  <td>The x:Bind markup extension has become a powerful feature of UWP over WPF. Compiled function bindings can be used for nearly anything and can replace other missing features like MultiBinding in most situations. Other advantages of x:Bind include debugging support as well as increased performance because it's compiled. UWP originally did not support x:Bind in control templates; however, support was added in Windows 10 version 1809.</td>
 </tr>
 <tr>
  <td>x:Load Attribute</td>
  <td>❌</td>
  <td>✔</td>
  <td>You can use x:Load to optimize the startup, visual tree creation, and memory usage of your XAML app. Using x:Load has a similar visual effect to Visibility, except that when the element is not loaded, its memory is released and internally a small placeholder is used to mark its place in the visual tree.</td>
 </tr>
 <tr>
  <td>x:Static Extension</td>
  <td>✔</td>
  <td>❌</td>
  <td>The x:Static markup extension isn't implemented in UWP. In WPF this is used to access a static by-value code entity (constant, property, field, or enum).</td>
 </tr>
 <tr>
  <td>x:Type Extension</td>
  <td>✔</td>
  <td>❌</td>
  <td>The x:Type markup extension isn't implemented in UWP. In WPF this is used to get a type similar to `Type.GetType()`.</td>
 </tr>
 <tr>
  <td>x:TypeArguments Directive</td>
  <td>✔</td>
  <td>❌</td>
  <td>The x:TypeArguments directive isn't implemented in UWP which causes problems with generics. Missing this requires some work-arounds with classes and creating a non-generic class to use in XAML from a generic one.</td>
 </tr>
 <tr>
  <td>x:Uid Directive / .resw for localization</td>
  <td>⚡</td>
  <td>✔</td>
  <td>x:Uid exists in both WPF and UWP. However, using it to localize properties is quite a bit more complex in WPF (using LocBaml, csv files, the commmand line in a manual process). UWP provides a much more integrated localization system using x:Uid and .resw files similar to what existed in Windows Forms. WPF is sorely missing this type of localization support and this is a clear advantage of UWP.</td>
 </tr>
 <tr>
  <td>{DynamicResource} Extension</td>
  <td>✔</td>
  <td>❌</td>
  <td>The DynamicResource markup extension resolves and assigns the resource value to a XAML attribute at runtime only when its needed (as opposed to StaticResource which is resolved and assigned when XAML is first loaded). DynamicResource is fairly common in WPF but doesn't exist in UWP. A partial work-around requires custom markup extensions.</td>
 </tr>
 <tr>
  <td>{ThemeResource} Extension</td>
  <td>❌</td>
  <td>✔</td>
  <td>The ThemeResource markup extension resolves and assigns the resource value to a XAML attribute depending on the active theme (light/dark/high-contrast). Resource values are automatically re-evaluated when the theme changes.</td>
 </tr>
 <tr>
  <td>Full Markup Extension</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP only implements a subset of the full markup extension support in WPF. This area needs to be expanded upon in the future.</td>
 </tr>
</table>
 
### Binding / Dependency Property System
 
<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>Coercion</td>
  <td>✔</td>
  <td>❌</td>
  <td>Coercion of Dependency Properties is not supported in UWP.</td>
 </tr>
 <tr>
  <td>Data (Input) Validation</td>
  <td>✔</td>
  <td>❌</td>
  <td>The entire WPF data validation system including the classes/inferfaces: ValidationRule (and all standard implementations), Binding.ValidationRules, IDataErrorInfo, INotifyDataErrorInfo, Binding.ValidatesOnNotifyDataErrors, etc. is not implemented in UWP. This will be added in WinUI 3.0 but the story for using this within the UWP app model with WinUI 3.0 is less clear.</td>
 </tr>
 <tr>
  <td>DependencyProperty. RegisterReadOnly / 
  DependencyPropertyKey</td>
  <td>✔</td>
  <td>❌</td>
  <td>Read-only dependency properties are used in WPF for collections and other properties that should never be set, even through binding. It is especially useful for control development. UWP doesn't support this and only implements get-only property accessors which still allow unwanted changes with binding.</td>
 </tr>
 <tr>
  <td>OneWayToSource BindingMode</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>Binding to ConverterParameter</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>MultiBinding /
  IMultiValueConverter</td>
  <td>✔</td>
  <td>❌</td>
  <td>Very useful feature in WPF for advanced binding scenearios no longer exists for UWP. UWP does have function binding with x:Bind though (Used to re-implement converter logic).</td>
 </tr>
 <tr>
  <td>ICommand</td>
  <td>✔</td>
  <td>⚡</td>
  <td>While the interface technically exists, ICommand is nothing like what it was in WPF. The programmer is now responsible for doing every little part of the command. This was improved in Windows 10 version 1809 which added XamlUICommand and StandardUICommand.</td>
 </tr>
 <tr>
  <td>RelativeSource / AncestorType</td>
  <td>✔</td>
  <td>⚡</td>
  <td>Not nearly as powerful in UWP, relative source only supports `{RelativeSource Self}` and `{RelativeSource TemplatedParent}` as compared to more powerful expressions in WPF like `{RelativeSource PreviousData}` or `{Binding RelativeSource={RelativeSource Mode=PreviousData, AncestorType={x:Type TextBox}}`.</td>
 </tr>
 <tr>
  <td>StringFormat</td>
  <td>✔</td>
  <td>❌</td>
  <td>XAML such as `{Binding DateValue, StringFormat=Date: {0:dddd yyyy-MM-dd}}` isn't supported in UWP and requires custom converters.</td>
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
  <td>DataTriggers / PropertyTrigger / EventTrigger within Style.Triggers</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>VisualStateManager</td>
  <td>⚡</td>
  <td>✔</td>
  <td>A different concept from WPF that takes the place of DataTriggers, this is very verbose and more often than not increases complexity compared to data triggers.

@Felix-Dev VisualStateManager does exist in WPF (it was added in .NET Framework 4.0). It's not as elegant as in UWP though, i.e. it has no VisuaStateManager.Setters property. That means you have to use Storyboards to set your values.</td>
 </tr>
 <tr>
  <td>Implicit DataTemplate</td>
  <td>✔</td>
  <td>❌</td>
  <td>Set the DataType property of the DataTemplate to the corresponding type and the template is then applied automatically to all instances of that particular type</td>
 </tr>
 <tr>
  <td>Binding in Style setter</td>
  <td>✔</td>
  <td>❌</td>
  <td>Any other than TemplateBinding isn't support in a template/style within UWP</td>
 </tr>
 <tr>
  <td>BasedOn default Style</td>
  <td>✔</td>
  <td>⚡</td>
  <td>`BasedOn={StaticResource {x:Type TextBlock}` isn't supported in UWP but works in WPF. Instead, BasedOn requires the use of a key which is a problem as not all default styles define one. This is a specific example of the missing x:Type markup extension in UWP.</td>
 </tr>
</table>

---

### Classes/Objects

This section primarily describes differences in controls and properties at the object or class level. As the number of differences in this section may become quite large, classes and properties are listed alphabetically and grouped together where it makes sense. Only the most used and fundamental controls are included here. See the *Controls* section for a high-level understanding of all controls.

**Grid**

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>BorderBrush</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's Grid. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>BorderThickness</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's Grid. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>ColumnSpacing / RowSpacing</td>
  <td>❌</td>
  <td>✔</td>
  <td>Similar to StackPanel.Spacing, the Grid's ColumnSpacing and RowSpacing properties provide a quick way to set a uniform horizortal and/or vertical distance between all child controls in a Grid. This was added to UWP and does not exist in WPF.</td>
 </tr>
 <tr>
  <td>CornerRadius</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's Grid. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>Padding</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's Grid. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>ShowGridLines</td>
  <td>✔</td>
  <td>❌</td>
  <td>While this property exists in WPF, it was only intended for debugging purposes and not production quality code (https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.grid.showgridlines). As such, it was removed from UWP.</td>
 </tr>
</table>

**StackPanel**

Additional properties such as WPF's `HasLogicalOrientation`, `HorizontalOffset` and `VerticalOffset` are purposely excluded from this section as they aren't considered useful.

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>AreHorizontalSnapPointsRegular / AreScrollSnapPointsRegular / AreVerticalSnapPointsRegular</td>
  <td>❌</td>
  <td>✔</td>
  <td>Information on snapping points does not exist in WPF's StackPanel.</td>
 </tr>
 <tr>
  <td>BackgroundSizing</td>
  <td>❌</td>
  <td>✔</td>
  <td>https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.stackpanel.backgroundsizing</td>
 </tr>
 <tr>
  <td>BorderBrush</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's StackPanel. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>BorderThickness</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's StackPanel. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>CornerRadius</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's StackPanel. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>ExtentHeight</td>
  <td>✔</td>
  <td>❌</td>
  <td>https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.stackpanel.extentheight</td>
 </tr>
 <tr>
  <td>ExtentWidth</td>
  <td>✔</td>
  <td>❌</td>
  <td>https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.stackpanel.extentwidth</td>
 </tr>
 <tr>
  <td>Padding</td>
  <td>❌</td>
  <td>✔</td>
  <td>This property does not exist in WPF's StackPanel. It was added in UWP to help flatten the visual tree instead of requiring the use of a Border.</td>
 </tr>
 <tr>
  <td>Spacing</td>
  <td>❌</td>
  <td>✔</td>
  <td>The Spacing property is a quick way to set a uniform distance between all child controls in a StackPanel. This was added to UWP and does not exist in WPF.</td>
 </tr>
</table>

**UIElement**

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
<tr>
  <td>IsVisible / IsVisibleChanged Event</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP has no way of tracking which controls are actually visible on the display. WPF has the UIElement.IsVisible property and the IsVisibleChanged event. This hinders the ability to optimize controls for performance.</td>
 </tr>
 <tr>
  <td>Visibility with Visibility.Hidden</td>
  <td>✔</td>
  <td>⚡</td>
  <td>UWP does not include the Visibility.Hidden enum value used for UIElement.Visibility. Hidden in WPF allowed a control to still be used in measure/layout but appear invisible when rendered for display.</td>
 </tr>
 <tr>
  <td>Clip</td>
  <td>✔</td>
  <td>⚡</td>
  <td>Both WPF and UWP have UIElement.Clip properties. However, WPF can take any Geometry allowing for non-rectangular clipping. UWP can only use a RectangleGeometry for clipping. WPF: public Geometry UIElement.Clip, UWP: public RectangleGeometry UIElement.Clip</td>
 </tr>
 <tr>
  <td>ClipToBounds</td>
  <td>✔</td>
  <td>❌</td>
  <td>In WPF it's possible to clip child contents to the parents bounds by setting ClipToBounds to True. UWP doesn't have this property at all. The work-around is to use UIElement.Clip which can only do rectangular clipping.</td>
 </tr>
 <tr>
  <td>LayoutTransform</td>
  <td>✔</td>
  <td>❌</td>
  <td>Layout transform is needed to transform elements before layouting. This allows for easily changing textbox direction and then putting it in a table. RenderTransform, as it applies after layout, does not resize parent controls for transformed children. See Transform3D for the UWP equivalent.</td>
 </tr>
 <tr>
  <td>Projection</td>
  <td>❌</td>
  <td>✔</td>
  <td>A 3-D projection effect applied to the element. Is more or less obsolete, use Transform3D instead.</td>
 </tr>
 <tr>
  <td>Transform3D</td>
  <td>❌</td>
  <td>✔</td>
  <td>Use the Transform3D property to apply a 3-D transform matrix to a XAML element. This lets you create effects where two-dimensional UI appears to exist in 3-D space relative to the user. Transform3D behaves much like RenderTransform, but allows transforms in three-dimensional space and not just two dimensions. It also support animations.</td>
 </tr>
</table>

**Minor Changes**

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>Header / HeaderTemplate</td>
  <td>❌</td>
  <td>✔</td>
  <td>Several controls in UWP support an additional Header content and HeaderTemplate property. This allows for quickly adding a description or title above a control which is useful in data-input scenarios. UWP controls with a header property include: ComboBox, DatePicker, ListViewBase, PasswordBox, TextBox, TimePicker, ToggleSwitch. Notably, the header property is not present on some controls such as: Button and CheckBox.</td>
 </tr>
 <tr>
  <td>ItemsControl. AlternationIndex / AlternationCount</td>
  <td>✔</td>
  <td>❌</td>
  <td>WPF has an easy way to change the style of items in a list using ItemsControl.AlternationIndex and ItemsControl.AlternationCount. This allows, for example, to change the background color of a listed item for even/odd entries. UWP doesn't support this at all in any controls. The partial work-around in UWP is to create a new control deriving from the framework's implementation and override the PrepareContainerForItemOverride() method.</td>
 </tr>
 <tr>
  <td>Thickness</td>
  <td>✔</td>
  <td>⚡</td>
  <td>The Thickness struct exposes fields for Top, Bottom, Left and Right instead of dependency properties as in WPF. This means you cannot Bind or asign resources to an individual thickness parameter.</td>
 </tr>
 <tr>
  <td>Size / Rect / Point</td>
  <td>✔</td>
  <td>✔</td>
  <td>Size, Rect and Point are fully supported in both WPF and UWP. However, UWP uses single-precision float types for properties instead of double in WPF. This creates an incompatiblity when porting code.</td>
 </tr>
</table>

**Unimplemented Classes**

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>Adorner</td>
  <td>✔</td>
  <td>❌</td>
  <td>https://docs.microsoft.com/en-us/dotnet/framework/wpf/controls/adorners-overview</td>
 </tr>
 <tr>
  <td>Supplemental Shapes: Arrow, Callout, Star, etc</td>
  <td>✔</td>
  <td>❌</td>
  <td>Several shapes present in WPF are missing in UWP.</td>
 </tr>
 <tr>
  <td>VisualBrush / DrawingBrush</td>
  <td>✔</td>
  <td>❌</td>
  <td>VisualBrush is not a XAML brush in UWP. Instead, must fall back to composition brushes which are not 1:1 equivalent. DrawingBrush is not supported at all in UWP.</td>
 </tr>
 <tr>
  <td>Window</td>
  <td>✔</td>
  <td>❌</td>
  <td>For some good reasons UWP has no concept of a window. This is fine for mobile devices but can be a problem for purely desktop applications. Without a window, there is no way to control an app's size or position. There are currently proposals to add this in the transition to WinUI 3.0.</td>
 </tr>
</table>

---

### Other

<table>
 <tr>
   <th>Item</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>Notes</th>
 </tr>
 <tr>
  <td>Custom Cursor at runtime</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>Sub-pixel anti-aliasing</td>
  <td>✔</td>
  <td>❌</td>
  <td>Anti-aliasing in UWP along with rendering in general is poor compared to WPF. It's assumed this is for performance reasons on mobile devices and the web (Silverlight).</td>
 </tr>
 <tr>
  <td>Nested Types in XAML</td>
  <td>✔</td>
  <td>❌</td>
  <td>Nesting different types in XAML is generally not possible in UWP. Code such as `&lt;ListBox.ItemsSource&gt;&lt;x:Array&gt;&lt;s:string&gt;foo&lt;s/:string&gt;&lt;x/:Array&gt;` works in WPF but not in UWP.</td>
 </tr>
 <tr>
  <td>Event Tunneling / Event Bubbling / Routed Events</td>
  <td>✔</td>
  <td>⚡</td>
  <td>A lot more events are simply direct in UWP. Some cases of event bubbling such as ButtonBase.Click to parent are not supported in UWP. Event Tunneling, a concept fully supported in WPF, isn't support at all in UWP.</td>
 </tr>
</table>

## Quirks

 * Several UWP controls have reentrancy issues. For example, changing the selected item while in a ComboBox SelectionChanged event is largely not possible and will result in a crash. This makes validation directly in the event handler nearly impossible.
 * UWP controls are generally not as powerful as the WPF counterparts. For example, for several years the ComboBox in UWP was not editable. The UWP DatePicker also does not allow typing in a specific date.
 * UWP has no support for data (input) validation. This is a large issue for line-of-business apps migrating from WPF to UWP that heavily use this feature in view models or binding.
 * The UWP styling system is different enough from WPF to require extra effort during porting. UWP uses the VistualStateManger instead of concepts like DataTriggers or EventTriggers from WPF. Styling/Templating are one of the main differences.
 * The ResourceDictionary XAML markup in UWP supports far fewer features than in WPF.
 * UWP seems to follow only the XAML/2006 spec instead of [XAML/2009]((https://docs.microsoft.com/en-us/dotnet/desktop-wpf/xaml-services/xaml-2009-language-features)) supported by WPF 
 * Several UWP controls are sealed and new controls cannot derive from them
 * For advanced rendering, UWP has fewer features built in. This requires falling back to Win2D or composition more often.
 * There are several namespaces differences in UWP and WPF. For example, WPF has System.Windows.Media.Colors while UWP moves this to Windows.UI.Colors.
 * TextBlock and TextBox, for example, do not allow 'null' values for string-type Text properties. Setting null to `Text` will crash the app at runtime. This is one of the largest concerns when porting over from WPF as WPF accepts null without an issue; yet the same code may crash in UWP. The solution is to use `.Text = stringValue ?? string.Empty;` for all controls instead of setting a string directly.
 * In WPF it was possible to build templates using the [FrameworkElementFactory Class](https://docs.microsoft.com/en-us/dotnet/api/system.windows.frameworkelementfactory?view=netcore-3.1) without using XAML. This allowed for entire UI's to be created without markup (since instantiating controls is already possible in C# directly). However, the burden of maintaining two different ways of doing things became too much and Microsoft dropped this ability in UWP and deprecated it for WPF. Instead, it's necessary to write template XAML as a string in code then pass it to XamlReader.Load().
 * In WPF it was possible to get the reference to a control generated from a template using [`Control.Template.FindName("controlName")`](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/controls/how-to-find-controltemplate-generated-elements?view=netframeworkdesktop-4.8). This was very useful combined with data binding when you needed to get a control instance. In UWP `Template.FindName` does not exist. This means to get the control generated from a template you must walk the visual tree using `VisualTreeHelper.GetChild()`. In practice this introduces a timing factor and makes it more difficult than in WPF (you must be sure the template is fully generated).

## Controls

For a list of supported controls and a comparison of their differences, refer to the separate [XAML Framework Controls](https://github.com/robloo/PublicDocs/blob/master/XAMLFrameworkControls.md#Controls) document. This document was originally included here but was separated to allow expansion and inclusion of other frameworks.

## 引用

 1. http://dansuleski.com/so-what-else-could-be-missing-in-uwp/
 2. https://github.com/microsoft/microsoft-ui-xaml/issues/719

## 附加资料

 * https://github.com/jbe2277/waf/wiki/UWP-vs.-WPF

## License

This document is licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
