最后更新时间 2021年11月06日  | 使用 CC BY-SA 4.0 协议分发

# WPF 与 UWP 区别总览

通用 Windows 平台（UWP）起源于 SilverLight，而不是基于 Windows Presentation Foundation（WPF）。UWP 是用 C++ 实现的，而不是用 C# 和 C++（底层功能）编写的 WPF。UWP 由于是一个完全不同的 XAML 实现，旨在包括更多的资源限制的设备，并支持更多的编程语言，UWP 与 WPF 相比有几个不同之处。这些差异可能是 UWP 的新功能，稍微不同的做事方式，或者更常见的是 UWP 中缺少的 WPF 功能。这些差异并没有被微软总结出来，这对熟悉 WPF 的开发者来说是一个障碍，他们必须要移植现有的代码。本文档旨在提供一个差异的概述。

## XAML / 对象模型

本节列出了 UWP 和 WPF 之间的主要区别（主要是从 XAML 的角度）。

图例：

 * ✔ 表示平台（由 WPF 或 UWP 列定义）具有该功能。
 * ❌ 表示该功能在该平台上普遍缺失
 * ⚡ 表示与其他平台相比，该功能只是部分实现。

### 标记扩展和指令

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>x:Array 扩展</td>
  <td>✔</td>
  <td>❌</td>
  <td>x:Array 在 UWP 中不受支持</td>
 </tr>
 <tr>
  <td>x:Bind 扩展</td>
  <td>❌</td>
  <td>✔</td>
  <td>x:Bind 标记扩展已经成为 UWP 相对于 WPF 的一个强大功能。编译时函数绑定几乎可以用于任何事情，并且在大多数情况下可以取代其他缺失的功能，如 MultiBinding。x:Bind 的其他优势包括调试支持，以及由于它是编译时绑定而性能不错。UWP 最初不支持 ControlTemplate 中的 x:Bind；但是，在 Windows 10 的 1809 版本中增加了支持。</td>
 </tr>
 <tr>
  <td>x:Load 特性</td>
  <td>❌</td>
  <td>✔</td>
  <td>你可以使用 x:Load 来优化你的 XAML 应用程序的启动、可视化树的创建和内存使用。使用 x:Load 有一个类似于 Visibility 的视觉效果，除了当元素没有被加载时，它的内存会被释放，内部会使用一个小的占位符来标记它在视觉树中的位置。</td>
 </tr>
 <tr>
  <td>x:Static 扩展</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP 中没有实现 x:Static 标记扩展。在 WPF 中，这被用来访问一个静态的值类型代码实体（常量、属性、字段或枚举）。</td>
 </tr>
 <tr>
  <td>x:Type 扩展</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP 中没有实现 x:Type 标记扩展。在 WPF 中，这被用来获取一个类似于 `Type.GetType()` 的类型。</td>
 </tr>
 <tr>
  <td>x:TypeArguments 指令</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP 中没有实现 x:TypeArguments 指令，这导致了泛型的问题。缺少了这一点，就需要用类来解决一些问题，并在 XAML 中创建一个非泛型的类来使用。</td>
 </tr>
 <tr>
  <td>x:Uid 指令 / .resw 本地化</td>
  <td>⚡</td>
  <td>✔</td>
  <td>x:Uid 在 WPF 和 UWP 中都存在。然而，在 WPF 中使用它来本地化属性是相当复杂的（使用 LocBaml，csv 文件，手动过程中的命令行）。UWP 提供了一个更集成的本地化系统，使用 x:Uid 和 .resw 文件，类似于 Windows Forms 中存在的。WPF 严重缺乏这种类型的本地化支持，这是 UWP 的一个明显优势。</td>
 </tr>
 <tr>
  <td>{DynamicResource} 扩展</td>
  <td>✔</td>
  <td>❌</td>
  <td>动态资源（DynamicResource）标记扩展在运行时只在需要的时候解析和分配资源值给 XAML 属性（与静态资源相反，静态资源在 XAML 第一次加载时就被解析和分配）。DynamicResource 在 WPF 中相当常见，但在 UWP 中不存在。一个部分的解决方法需要自定义标记扩展。</td>
 </tr>
 <tr>
  <td>{ThemeResource} 扩展</td>
  <td>❌</td>
  <td>✔</td>
  <td>ThemeResource 标记扩展根据系统活动主题（亮/暗/高对比度）解析并将资源值分配给一个 XAML 属性。当系统主题改变时，资源值会自动重新计算。</td>
 </tr>
 <tr>
  <td>完整标记扩展</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP 只实现了 WPF 中完整标记扩展支持的一个子集。这个领域需要在未来进行扩展。</td>
 </tr>
</table>
 
### 绑定/依赖属性系统
 
<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>强制转换（Coercion）</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP 中不支持依赖属性的强制转换（Coercion）。</td>
 </tr>
 <tr>
  <td>数据（输入）验证</td>
  <td>✔</td>
  <td>❌</td>
  <td>整个WPF的数据验证系统包括类/接口： ValidationRule（以及所有的标准实现），Binding.ValidationRules，IDataErrorInfo，INotifyDataErrorInfo，Binding.ValidatesOnNotifyDataErrors 等在 UWP 中没有实现。这将在 WinUI 3.0 中添加，但在 WinUI 3.0 的 UWP 应用模型中使用这个的情况不太清楚。</td>
 </tr>
 <tr>
  <td>DependencyProperty. RegisterReadOnly / 
  DependencyPropertyKey</td>
  <td>✔</td>
  <td>❌</td>
  <td>只读依赖属性在 WPF 中用于集合和其他属性，即使通过绑定也不应该被设置。它对控件的开发特别有用。UWP 不支持这一点，只实现了只读属性访问器，这仍然允许通过绑定进行不必要的改变。</td>
 </tr>
 <tr>
  <td>OneWayToSource 绑定模式</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>绑定到 ConverterParameter</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>多路绑定 /
  IMultiValueConverter</td>
  <td>✔</td>
  <td>❌</td>
  <td>WPF 中非常有用的高级绑定场景的功能在 UWP 中不再存在。不过 UWP 有 x:Bind 的函数绑定（用于重新实现转换器逻辑）。</td>
 </tr>
 <tr>
  <td>ICommand</td>
  <td>✔</td>
  <td>⚡</td>
  <td>虽然接口在技术上存在，但 ICommand 与 WPF 中的情况完全不同。现在程序员要负责实现命令的每一个小部分。这在 Windows 10 1809 版本中得到了改善，该版本增加了 XamlUICommand 和 StandardUICommand。</td>
 </tr>
 <tr>
  <td>RelativeSource / AncestorType</td>
  <td>✔</td>
  <td>⚡</td>
  <td>在 UWP 中并不强大，相对源只支持 `{RelativeSource Self}` 和 `{RelativeSource TemplatedParent}`，相比之下，WPF 中的表达式更强大，如 `{RelativeSource PreviousData}` 或 `{Binding RelativeSource={RelativeSource Mode=PreviousData, AncestorType={x:Type TextBox}}`。</td>
 </tr>
 <tr>
  <td>StringFormat</td>
  <td>✔</td>
  <td>❌</td>
  <td>类似于 `{Binding DateValue, StringFormat=Date: {0:dddd yyyy-MM-dd}}` 的XAML 在 UWP 中不支持，需要自定义转换器。</td>
 </tr>
</table>

### 样式

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>DataTriggers / PropertyTrigger / Style.Triggers 中的 EventTrigger</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>VisualStateManager</td>
  <td>⚡</td>
  <td>✔</td>
  <td>一个与 WPF 不同的概念取代了 DataTriggers，这是非常冗长的，与数据触发器相比，更多的时候会增加复杂性。

@Felix-Dev VisualStateManager 在 WPF 中确实存在（它被添加到 .NET Framework 4.0 中）。但它不像 UWP 那样优雅，也就是说，它没有 VisuaStateManager.Setters 属性。这意味着你必须使用 Storyboards 来设置你的值。</td>
 </tr>
 <tr>
  <td>隐式 DataTemplate</td>
  <td>✔</td>
  <td>❌</td>
  <td>将 DataTemplate 的 DataType 属性设置为相应的类型，然后模板就会自动应用于该特定类型的所有实例。</td>
 </tr>
 <tr>
  <td>Style setter 中的 Binding</td>
  <td>✔</td>
  <td>❌</td>
  <td>除了 TemplateBinding 之外，UWP 在 template/style 内不支持绑定。</td>
 </tr>
 <tr>
  <td>BasedOn 默认样式</td>
  <td>✔</td>
  <td>⚡</td>
  <td>`BasedOn={StaticResource {x:Type TextBlock}}` 在 UWP 中不支持，但在 WPF 中可以使用。相反，BasedOn 需要使用一个键，这是一个问题，因为不是所有的默认样式都定义一个键。这是 UWP 中缺少 x:Type 标记扩展的一个具体例子。</td>
 </tr>
</table>

---

### 类与对象

本节主要描述对象或类层面上的控制和属性的差异。由于本节中的差异数量可能会变得相当大，所以类和属性是按字母顺序排列的，并在有意义的地方归为一组。这里只包括最常用的和最基本的控件。请参阅*控件*部分以了解所有控件的高层次情况。

**Grid**

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>BorderBrush</td>
  <td>❌</td>
  <td>✔</td>
  <td>这个属性在 WPF 的 Grid 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
 </tr>
 <tr>
  <td>BorderThickness</td>
  <td>❌</td>
  <td>✔</td>
  <td>这个属性在 WPF 的 Grid 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
 </tr>
 <tr>
  <td>ColumnSpacing / RowSpacing</td>
  <td>❌</td>
  <td>✔</td>
  <td>与 StackPanel.Spacing 类似，Grid 的 ColumnSpacing 和 RowSpacing 属性提供了一种快速的方法来设置 Grid 中所有子控件之间统一的水平和/或垂直距离。这是在 UWP 中添加的，在 WPF 中不存在。</td>
 </tr>
 <tr>
  <td>CornerRadius</td>
  <td>❌</td>
  <td>✔</td>
  <td>这个属性在 WPF 的 Grid 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
 </tr>
 <tr>
  <td>Padding</td>
  <td>❌</td>
  <td>✔</td>
  <td>这个属性在 WPF 的 Grid 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
 </tr>
 <tr>
  <td>ShowGridLines</td>
  <td>✔</td>
  <td>❌</td>
  <td>虽然这个属性在 WPF 中存在，但它只用于调试目的，而不是生产质量代码（https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.grid.showgridlines）。因此，它被从 UWP 中移除。</td>
 </tr>
</table>

**StackPanel**

额外的属性，如 WPF 的 `HasLogicalOrientation`、`HorizontalOffset` 和 `VerticalOffset`被特意排除在本节之外，因为它们被认为并不实用。

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>AreHorizontalSnapPointsRegular / AreScrollSnapPointsRegular / AreVerticalSnapPointsRegular</td>
  <td>❌</td>
  <td>✔</td>
  <td>在 WPF 的 StackPanel 中不存在关于抓取点（Snap Points）的信息。</td>
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
  <td>这个属性在 WPF 的 StackPanel 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
 </tr>
 <tr>
  <td>BorderThickness</td>
  <td>❌</td>
  <td>✔</td>
  <td>这个属性在 WPF 的 StackPanel 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
 </tr>
 <tr>
  <td>CornerRadius</td>
  <td>❌</td>
  <td>✔</td>
  <td>这个属性在 WPF 的 StackPanel 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
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
  <td>这个属性在 WPF 的 StackPanel 中并不存在。它被添加到 UWP 中，以帮助扁平化视觉树，而不是要求使用一个 Border。</td>
 </tr>
 <tr>
  <td>Spacing</td>
  <td>❌</td>
  <td>✔</td>
  <td>Spacing 属性是设置 StackPanel 中所有子控件之间统一距离的一种快速方法。这是在 UWP 中添加的，在 WPF 中不存在。</td>
 </tr>
</table>

**UIElement**

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
<tr>
  <td>IsVisible / IsVisibleChanged 事件</td>
  <td>✔</td>
  <td>❌</td>
  <td>UWP 没有办法跟踪哪些控件在显示屏上实际可见。WPF 有 UIElement.IsVisible 属性和 IsVisibleChanged 事件。这阻碍了优化控件性能的能力。</td>
 </tr>
 <tr>
  <td>Visibility.Hidden 状态</td>
  <td>✔</td>
  <td>⚡</td>
  <td>UWP 不包括用于 UIElement.Visibility.Hidden 的枚举值。在 WPF 中，Hidden 允许一个控件仍然在测量/布局中使用，但在渲染显示时不可见。</td>
 </tr>
 <tr>
  <td>Clip</td>
  <td>✔</td>
  <td>⚡</td>
  <td>WPF 和 UWP 都有 UIElement.Clip 属性。然而，WPF 可以使用任何 Geometry，允许非矩形剪裁。UWP 只能使用一个 RectangleGeometry 进行剪切。WPF: public Geometry UIElement.Clip, UWP: public RectangleGeometry UIElement.Clip</td>
 </tr>
 <tr>
  <td>ClipToBounds</td>
  <td>✔</td>
  <td>❌</td>
  <td>在 WPF 中，通过设置 ClipToBounds 为 True，可以将子控件按照父控件的尺寸进行裁剪。UWP 根本就没有这个属性。解决办法是使用 UIElement.Clip，它只能做矩形的剪切。</td>
 </tr>
 <tr>
  <td>LayoutTransform</td>
  <td>✔</td>
  <td>❌</td>
  <td>布局转换是需要在布局前转换元素的。这允许轻松地改变文本框的方向，然后把它放在一个表格里。RenderTransform，因为它是在布局后应用的，所以不会为被转换的子元素调整父控件的大小。参见 Transform3D，了解 UWP 的等同物。</td>
 </tr>
 <tr>
  <td>Projection</td>
  <td>❌</td>
  <td>✔</td>
  <td>应用于元素的 3-D 投影效果。多多少少已经过时了，用 Transform3D 代替。</td>
 </tr>
 <tr>
  <td>Transform3D</td>
  <td>❌</td>
  <td>✔</td>
  <td>使用 Transform3D 属性将一个 3-D 转换矩阵应用到一个 XAML 元素。这可以让你创造出二维用户界面相对于用户来说似乎存在于三维空间的效果。Transform3D 的行为很像 RenderTransform，但允许在三维空间而不仅仅是二维空间进行变换。它也支持动画。</td>
 </tr>
</table>

**一些小变动**

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>Header / HeaderTemplate</td>
  <td>❌</td>
  <td>✔</td>
  <td>UWP 的一些控件支持额外的 Header 内容和 HeaderTemplate 属性。这允许在控件上方快速添加描述或标题，这在数据输入场景中很有用。具有 Header 属性的 UWP 控件包括：ComboBox, DatePicker, ListViewBase, PasswordBox, TextBox, TimePicker, ToggleSwitch。值得注意的是，标题属性不存在于某些控件上，例如：Button 和 CheckBox。</td>
 </tr>
 <tr>
  <td>ItemsControl. AlternationIndex / AlternationCount</td>
  <td>✔</td>
  <td>❌</td>
  <td>WPF 有一个简单的方法，使用 ItemsControl.AlternationIndex 和 ItemsControl.AlternationCount 来改变列表中项目的风格。例如，这允许改变偶数/多数条目的列表项的背景颜色。UWP 的任何控件都不支持这一点。在 UWP 中的部分解决方法是创建一个新的控件，它来自于框架的实现，并覆盖 PrepareContainerForItemOverride() 方法。</td>
 </tr>
 <tr>
  <td>Thickness</td>
  <td>✔</td>
  <td>⚡</td>
  <td>Thickness 结构暴露了顶部、底部、左侧和右侧的字段，而不是像 WPF 中的依赖属性。这意味着你不能将资源绑定或分配给一个单独的厚度参数。</td>
 </tr>
 <tr>
  <td>Size / Rect / Point</td>
  <td>✔</td>
  <td>✔</td>
  <td>在 WPF 和 UWP 中都完全支持 Size、Rect 和 Point。然而，UWP 使用单精度浮点类型的属性，而不是 WPF 的双精度。这在移植代码时产生了不兼容的问题。 
</td>
 </tr>
</table>

**未实现的类**

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>Adorner</td>
  <td>✔</td>
  <td>❌</td>
  <td>https://docs.microsoft.com/en-us/dotnet/framework/wpf/controls/adorners-overview</td>
 </tr>
 <tr>
  <td>补充图形：Arrow, Callout, Star 等等</td>
  <td>✔</td>
  <td>❌</td>
  <td>在 WPF 中存在的几个形状在 UWP 中缺失。</td>
 </tr>
 <tr>
  <td>VisualBrush / DrawingBrush</td>
  <td>✔</td>
  <td>❌</td>
  <td>VisualBrush 在 UWP 中不是一个 XAML 画笔。相反，必须退回到不是等价的组合画笔。在 UWP 中完全不支持 DrawingBrush。</td>
 </tr>
 <tr>
  <td>Window</td>
  <td>✔</td>
  <td>❌</td>
  <td>由于一些很好的原因，UWP 没有窗口的概念。这对移动设备来说很好，但对纯粹的桌面应用程序来说可能是个问题。没有窗口，就没有办法控制一个应用程序的大小和位置。目前有建议在过渡到 WinUI 3.0 时增加这个功能。</td>
 </tr>
</table>

---

### 其他

<table>
 <tr>
   <th>项目</th>
   <th>WPF</th>
   <th>UWP</th>
   <th>备注</th>
 </tr>
 <tr>
  <td>运行时自定义光标</td>
  <td>✔</td>
  <td>❌</td>
  <td></td>
 </tr>
 <tr>
  <td>亚像素抗锯齿</td>
  <td>✔</td>
  <td>❌</td>
  <td>与 WPF 相比，UWP 中的抗锯齿以及一般的渲染都很差。我们认为这是在移动设备和网页（Silverlight）上的性能原因。</td>
 </tr>
 <tr>
  <td>XAML 中的嵌套类型</td>
  <td>✔</td>
  <td>❌</td>
  <td>在 UWP 中，在 XAML 中嵌套不同的类型一般是不可能的。诸如 `&lt;ListBox.ItemsSource&gt;&lt;x:Array&gt;&lt;s:string&gt;foo&lt;s/:string&gt;&lt;x/:Array&gt;` 这样的代码在 WPF 中可行，但在 UWP 中不行。</td>
 </tr>
 <tr>
  <td>隧道事件/冒泡事件/路由事件</td>
  <td>✔</td>
  <td>⚡</td>
  <td>更多的事件在 UWP 中是直接的。在 UWP 中不支持一些事件冒泡的情况，如 ButtonBase.Click to parent。隧道事件，一个在 WPF 中完全支持的概念，在 UWP 中根本就不支持。</td>
 </tr>
</table>

## 怪异的地方

 * 几个 UWP 控件有重入问题。例如，在 ComboBox SelectionChanged 事件中改变所选项目是不可能的，会导致崩溃。这使得直接在事件处理程序中进行验证几乎不可能。
 * UWP 控件通常不像 WPF 控件那样强大。例如，几年来，UWP 的 ComboBox 是不可编辑的。UWP 的 DatePicker 也不允许输入一个特定的日期。
 * UWP 没有对数据（输入）验证的支持。对于从 WPF 迁移到 UWP 的业务线应用程序来说，这是一个很大的问题，这些应用程序在 ViewModel 或绑定中大量使用这一功能。
 * UWP 的样式系统与 WPF 有很大的不同，在移植过程中需要额外的努力。UWP 使用 VistualStateManger 而不是 WPF 中的 DataTriggers 或 EventTriggers 等概念。样式/模板是主要的区别之一。
 * UWP 中的 ResourceDictionary XAML 标记支持的功能比 WPF 少得多。
 * UWP 似乎只遵循 XAML/2006 规范，而不是 WPF 所支持的 [XAML/2009](https://docs.microsoft.com/en-us/dotnet/desktop-wpf/xaml-services/xaml-2009-language-features)
 * 一些 UWP 控件是密封的（sealed），新的控件不能从它们继承出来。
 * 对于高级渲染，UWP 内置的功能较少。这就需要更经常地使用 Win2D 或 composition。
 * 在 UWP 和 WPF 中有几个命名空间的差异。例如，WPF有 System.Windows.Media.Colors，而 UWP 将其移至 Windows.UI.Colors。
 * 例如，TextBlock 和 TextBox，不允许字符串类型的 `Text` 属性的 `null` 值。为 `Text` 设置 `null` 将在运行时使应用程序崩溃。这是从 WPF 移植过来的最大问题之一，因为 WPF 接受 null 没有问题；但同样的代码在 UWP 可能会崩溃。解决办法是对所有控件使用 `.Text = stringValue ?? string.Empty;`，而不是直接设置一个字符串。
 * 在 WPF 中，可以使用 [FrameworkElementFactory Class](https://docs.microsoft.com/en-us/dotnet/api/system.windows.frameworkelementfactory?view=netcore-3.1) 建立模板而不使用 XAML。这允许在没有标记的情况下创建整个 UI（因为在 C# 中已经可以直接实例化控件）。然而，维护两种不同方式的负担变得太重了，微软在 UWP 中放弃了这种能力，并在 WPF 中弃用了它。相反，有必要在代码中把模板 XAML 写成一个字符串，然后把它传递给 XamlReader.Load()。
 * 在WPF中，可以使用 [`Control.Template.FindName("controlName")`](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/controls/how-to-find-controltemplate-generated-elements?view=netframeworkdesktop-4.8)来获取由模板生成的控件的引用。当你需要获得一个控件实例时，这与数据绑定相结合是非常有用的。在 UWP 中，`Template.FindName` 并不存在。这意味着要获得由模板生成的控件，你必须使用 `VisualTreeHelper.GetChild()` 在视觉树上行走。在实践中，这引入了一个时间因素，并使其比 WPF 中更困难（你必须确保模板是完全生成的）。

## 控件

关于支持的控件的列表和它们之间的差异比较，请参考单独的 [XAML 框架控件一览](https://github.com/1357310795/XAML-UI-Docs/blob/master/XAMLFrameworkControls.md)文档。该文档最初包含在这里，但被分离出来，以便于扩展和包含其他框架。

## 引用

 1. http://dansuleski.com/so-what-else-could-be-missing-in-uwp/
 2. https://github.com/microsoft/microsoft-ui-xaml/issues/719

## 附加资料

 * https://github.com/jbe2277/waf/wiki/UWP-vs.-WPF

## License

This document is licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
