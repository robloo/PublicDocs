最后更新时间 2022年4月11日  | 使用 CC BY-SA 4.0 协议分发

# XAML 框架控件

本文档列出了每个 XAML 框架支持的控件，不包括一些基元和形状（Ellipse、Rect 等）。它还适当地描述了一些实现或使用上的差异。

到目前为止，包括以下框架：

 * Avalonia
 * UWP（使用 WinUI 2.x 库），也隐含了 Uno 平台的内容
 * WPF

## 控件

由于 WPF 是第一个 XAML 框架，它出现在第一位，所有其他的都按字母顺序列在他们自己的栏目中。Uno 平台通常支持 UWP/WinUI3 的所有控件，因此不需要自己的栏目。

支持的 Avalonia 控件的初始列表取自 [Avalonia 与 WPF 和 UWP 的比较](https://github.com/AvaloniaUI/Avalonia/wiki/Comparison-of-Avalonia-with-WPF-and-UWP#controls)，也是 CC BY-SA 4.0 许可的（本身最初基于[UWPvsWPF.md](https://github.com/robloo/PublicDocs/blob/master/UWPvsWPF.md)）。

请注意，*（WCT Version）* 表示该控件在 [Windows Community Toolkit](https://docs.microsoft.com/en-us/windows/communitytoolkit/) 中可用。

| WPF                        | Avalonia                |	UWP / Uno Platform       |
|----------------------------|-------------------------|--------------------------|
|🔲                          |🔲                        |✅ AppBarButton	          |
|🔲                          |🔲                        |✅ AppBarSeparator	       |
|🔲                          |🔲                        |✅ AppBarToggleButton	    |
|🔲                          |🔲                        |✅ AnimatedVisualPlayer <br/> *(WinUI 2.1)* |
|🔲                          |✅ AutoCompleteBox        |✅ AutoSuggestBox	        |
|✅ Border                   |✅ Border                 |✅ Border	                |
|🔲                          |🔲                        |✅ BreadcrumbBar <br/> *(WinUI 2.6)* |
|✅ BulletDecorator	         |✅ BulletDecorator        |🔲                        |
|✅ Button                   |✅ Button                 |✅ Button	                |
|✅ DatePicker               |✅ CalendarDatePicker     |✅ CalendarDatePicker	    |
|✅ Calendar	                |✅ Calendar               |✅ CalendarView	          |
|✅ Canvas	                  |✅ Canvas                 |✅ Canvas                 |
|🔲                          |🔲                        |✅ CaptureElement	        |
|✅ CheckBox                 |✅ CheckBox               |✅ CheckBox	              |
|🔲                          |🔲                        |✅ ColorPicker	           |
|✅ ComboBox	                |✅ ComboBox               |✅ ComboBox               |
|✅ ToolBar                  |🔲                        |✅ CommandBar	            |
|🔲                          |🔲                        |✅ CommandBarFlyout <br/> *(WinUI 2.0)* |
|✅ ContentControl           |✅ ContentControl         |✅ ContentControl	        |
|✅ ContentPresenter         |✅ ContentPresenter       |✅ ContentPresenter	      |
|✅ DataGrid	                |✅ DataGrid               |🔲 *(WCT Version)*        |
|🔲                          |✅ DatePicker             |✅ DatePicker	            |
|🔲                          |✅ DatePickerFlyout       |✅ DatePickerFlyout	      |
|✅ DockPanel                |✅ DockPanel              |🔲 *WCT Version*          |
|✅ DocumentViewer		         |🔲                        |🔲                        |
|🔲                          |✅ DropDownButton         |✅ DropDownButton <br/> *(WinUI 2.0)* |
|✅ Expander	                |✅ Expander               |✅ Expander <br/> *(WinUI 2.6)*       |
|🔲                          |✅ Carousel               |✅ FlipView	              |
|✅ FlowDocumentPageViewer		 |🔲                        |🔲                        |
|✅ FlowDocumentReader		     |🔲                        |🔲                        |
|✅ FlowDocumentScrollViewer |🔲                        |🔲                        |
|🔲                          |✅ Flyout                 |✅ Flyout	                |
|✅ Frame                    |🔲                        |✅ Frame	                 |
|✅ Grid                     |✅ Grid                   |✅ Grid                   |
|✅ GridSplitter	            |✅ GridSplitter           |🔲 *(WCT Version)*        |
|🔲                          |🔲                        |✅ GridView	              |
|✅ GroupBox		               |🔲                        |🔲                        |
|🔲                          |🔲                        |✅ Hub	                   |
|🔲                          |🔲                        |✅ HubSection	            |
|🔲                          |🔲                        |✅ HyperlinkButton	       |
|✅ Image                    |✅ Image                  |✅ Image	                 |
|🔲                          |🔲                        |✅ InfoBar <br/> *(WinUI 2.5)* |
|🔲                          |🔲                        |✅ InkCanvas	<br/> *(N/A in Uno)* |
|🔲                          |🔲                        |✅ InkToolbar	<br/> *(N/A in Uno)* |
|✅ ItemsControl             |✅ ItemsControl           |✅ ItemsControl	          |
|🔲                          |✅ ItemsPresenter         |✅ ItemsPresenter	        |
|🔲                          |✅ ItemsRepeater          |✅ ItemsRepeater <br/> *(WinUI 2.1)* |
|✅ Label		                  |✅ Label                  |🔲                        |
|✅ ListBox                  |✅ ListBox                |✅ ListBox	               |
|✅ ListView	                |🔲                        |✅ ListView	<br/> *(N/A in Uno)* |
|🔲                          |🔲                        |✅ MapControl             |
|🔲                          |🔲                        |✅ MediaElement	          |
|🔲                          |🔲                        |✅ MediaTransportControls |
|✅ Menu                     |✅ Menu                   |✅ MenuBar <br/> *(WinUI 2.0)*     |
|✅ MenuItem                 |✅ MenuItem               |✅ MenuBarItem <br/> *(WinUI 2.0)* |
|🔲 	                        |✅ MenuFlyout             |✅ MenuFlyout	            |
|✅ ContextMenu	             |✅ ContextMenu            |🔲          	             |
|🔲                          |🔲                        |✅ NavigationView	        |
|🔲                          |✅ NumericUpDown          |✅ NumberBox <br/> *(WinUI 2.3)* |
|✅ Panel		                  |✅ Panel                  |🔲                        |
|🔲                          |🔲                        |✅ ParallaxView	          |
|✅ PasswordBox              |✅ TextBox *(PasswordChar)* |✅ PasswordBox	         |
|🔲                          |🔲                        |✅ PersonPicture          |
|🔲                          |🔲                        |✅ PipsPager <br/> *(WinUI 2.6)* |
|🔲                          |🔲                        |✅ Pivot		                |
|🔲                          |🔲                        |✅ PivotItem		            |
|✅ Popup                    |✅ Popup                  |✅ Popup		                |
|✅ PrintDialog		            |🔲                        |🔲                        |
|✅ ProgressBar              |✅ ProgressBar            |✅ ProgressBar		          |
|🔲                          |🔲                        |✅ ProgressRing		         |
|🔲                          |🔲                        |✅ PullToRefresh		        |
|✅ RadioButton	             |✅ RadioButton            |✅ RadioButton		          |
|🔲   	                      |🔲                        |✅ RadioButtons <br/> *(WinUI 2.3)* |
|🔲                          |🔲                        |✅ RatingControl		        |
|✅ Rectangle                |✅ Rectangle              |✅ Rectangle		            |
|🔲                          |🔲                        |✅ RefreshContainer <br/> *(WinUI 2.0)* |
|🔲                          |✅ RelativePanel          |✅ RelativePanel		        |
|✅ RepeatButton             |✅ RepeatButton           |✅ RepeatButton	          |
|✅ RichTextBox              |🔲                        |✅ RichEditBox	           |
|🔲                          |🔲                        |✅ RichTextBlock	         |
|🔲                          |🔲                        |✅ RichTextBlockOverflow	 |
|✅ ScrollBar	               |✅ ScrollBar              |✅ ScrollBar	             |
|✅ ScrollContentPresenter   |✅ ScrollContentPresenter |✅ ScrollContentPresenter	|
|✅ ScrollViewer	            |✅ ScrollViewer           |✅ ScrollViewer	          |
|🔲                          |🔲                        |✅ SearchBox              |
|🔲                          |🔲                        |✅ SemanticZoom	          |
|✅ Separator		              |✅ Separator              |🔲                        |
|✅ Slider	                  |✅ Slider                 |✅ Slider                 |
|🔲                          |✅ SplitButton            |✅ SplitButton <br/> *(WinUI 2.0)* |
|🔲                          |✅ SplitView              |✅ SplitView	             |
|✅ StackPanel	              |✅ StackPanel             |✅ StackPanel	            |
|✅ StatusBar		              |🔲                        |🔲                        |
|🔲                          |🔲                        |✅ SwipeControl <br/> *(WinUI 2.0)* |
|✅ TabControl	              |✅ TabControl             |✅ TabView <br/> *(WinUI 2.2)*      |
|✅ TabItem                  |✅ TabItem                |✅ TabViewItem <br/> *(WinUI 2.2)*  |         
|🔲                          |🔲                        |✅ TeachingTip <br/> *(WinUI 2.1)*  |
|✅ TextBlock                |✅ TextBlock              |✅ TextBlock	             |
|✅ TextBox                  |✅ TextBox                |✅ TextBox	               |
|🔲                          |✅ TimePicker             |✅ TimePicker	            |
|🔲                          |✅ TimePickerFlyout       |✅ TimePickerFlyout	      |
|✅ ToggleButton             |✅ ToggleButton           |✅ ToggleButton	          |
|🔲                          |✅ ToggleSplitButton      |✅ ToggleSplitButton <br/> *(WinUI 2.0)* |
|🔲                          |✅ ToggleSwitch           |✅ ToggleSwitch	          |
|✅ ToolTip	                 |✅ ToolTip                |✅ ToolTip	               |
|✅ TreeView                 |✅ TreeView               |✅ TreeView	              |
|🔲                          |🔲                        |✅ TwoPaneView	           |
|🔲                          |🔲                        |✅ VariableSizedWrapGrid	 |
|✅ Viewbox	                 |✅ Viewbox                |✅ Viewbox	               |
|🔲                          |🔲                        |✅ WebView	               |
|✅ WrapPanel		              |✅ WrapPanel              |🔲 *(WCT Version)*        |
|✅ Window	                  |✅ Window                 |🔲                        |
| **Icons** |
|🔲                          |🔲                        |✅ AnimatedIcon <br/> *(WinUI 2.6)* |
|🔲                          |🔲                        |✅ BitmapIcon             |
|🔲                          |🔲                        |✅ FontIcon               |
|🔲                          |🔲                        |✅ ImageIcon <br/> *(WinUI 2.6)* |
|🔲                          |✅ PathIcon               |✅ PathIcon               |

## 控件的差异

 1. UWP的 `DatePicker` 与 WPF 的 `DatePicker` 不同。WPF 的 `DatePicker` 在功能上更接近于 UWP 的 `CalendarDatePicker`，因为它们都有一个下拉日历。在 WPF 中不存在一个没有日历视图的日期选择器。
 1. Avalonia 和 UWP 的 Windows Community Toolkit中 的 `DataGrid` 是基于 Silverlight 版本的控件——而不是全功能的 WPF 版本。因此，WPF 的 `DataGrid` 在某些方面更加强大。此外，Windows Community Toolkit 版本的控件有许多错误，微软宣布他们不会修复。然而，Avalonia 试图修复这些问题。
 1. UWP 的 `TabView` 只为顶层文档导航而设计。它并不总是 WPF 中`TabControl`的良好替代品。相反，UWP 的 `Pivot` 控件有时被用于标签功能。
 1. `RadioButtons` 是一个容器，可以轻松地创建单独的 `RadioButton` 控件组（具有可访问性的改进，等等）
 1. `ProgressRing` 在 WinUI Library v2.5-v2.6中被更新以使用 Lottie 动画。
 1. WPF 的 `ContextMenu` 在 UWP 中被通用化并被 `MenuFlyout` 取代。但是 Avalonia 同时支持这两者。
 
***

This document is licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
