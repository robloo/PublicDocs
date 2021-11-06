Last Updated 06 November 2021 | License CC BY-SA 4.0

# XAML Framework Controls

This document lists supported controls for each XAML framework excluding some primitives and shapes (Ellipse, Rect, etc.). It also describes some of the differences in implemenation or usage where appropriate. 

The following frameworks are included so far:

 * Avalonia
 * UWP (with the WinUI 2.x library), also implicitly includes the Uno Platform
 * WPF

## Controls

As WPF is the first XAML framework, it occurs first and all others are listed alphabetically in their own column. The Uno Platform generally supports all controls in UWP/WinUI3 and therefore does not need its own column. 

The initial list of supported Avalonia controls was taken from [Comparison of Avalonia with WPF and UWP](https://github.com/AvaloniaUI/Avalonia/wiki/Comparison-of-Avalonia-with-WPF-and-UWP#controls) also Licensed CC BY-SA 4.0 (itself originally based on [UWPvsWPF.md](https://github.com/robloo/PublicDocs/blob/master/UWPvsWPF.md)).

Note that *(WCT Version)* indicates a version of the control exists for UWP in the [Windows Community Toolkit](https://docs.microsoft.com/en-us/windows/communitytoolkit/).

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
|🔲                          |🔲                        |✅ DropDownButton <br/> *(WinUI 2.0)* |
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
|🔲                          |🔲                        |✅ InkCanvas	             |
|🔲                          |🔲                        |✅ InkToolbar             |
|✅ ItemsControl             |✅ ItemsControl           |✅ ItemsControl	          |
|🔲                          |✅ ItemsPresenter         |✅ ItemsPresenter	        |
|🔲                          |✅ ItemsRepeater          |✅ ItemsRepeater <br/> *(WinUI 2.1)* |
|✅ Label		                  |✅ Label                  |🔲                        |
|✅ ListBox                  |✅ ListBox                |✅ ListBox	               |
|✅ ListView	                |🔲                        |✅ ListView	              |
|🔲                          |🔲                        |✅ MapControl             |
|🔲                          |🔲                        |✅ MediaElement	          |
|🔲                          |🔲                        |✅ MediaTransportControls |
|✅ Menu                     |✅ Menu                   |✅ MenuBar <br/> *(WinUI 2.0)*     |
|✅ MenuItem                 |✅ MenuItem               |✅ MenuBarItem <br/> *(WinUI 2.0)* |
|🔲 	                        |✅ MenuFlyout             |✅ MenuFlyout	            |
|✅ ContextMenu	             |✅ ContextMenu            |🔲          	             |
|🔲                          |🔲                        |✅ NavigationView	        |
|🔲                          |🔲                        |✅ NumberBox <br/> *(WinUI 2.3)* |
|✅ Panel		                  |✅ Panel                  |🔲                        |
|🔲                          |🔲                        |✅ ParallaxView	          |
|✅ PasswordBox              |✅ TextBox *(PasswordChar)* |✅ PasswordBox	         |
|🔲                          |🔲                        |✅ PersonPicture.         |
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
|🔲                          |🔲                        |✅ SplitButton <br/> *(WinUI 2.0)* |
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
|🔲                          |🔲                        |✅ ToggleSplitButton <br/> *(WinUI 2.0)* |
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

## Control Differences

 1. The UWP `DatePicker` is different from WPF's `DatePicker`. The WPF `DatePicker` is closer to the UWP `CalendarDatePicker` in functionality as they both have a drop-down calendar. A picker to select a date without a calendar view does not exist in WPF.
 1. The `DataGrid` in both Avalonia and UWP's Windows Community Toolkit is based on the Silverlight version of the control -- not the full-featured WPF version. As such, WPF's `DataGrid` is more powerful in certain areas. In addition, the Windows Community Toolkit version of the control has many bugs that Microsoft announced they will not fix. Avalonia, however, makes an attempt to fix these issues.
 1. UWP's `TabView` is designed for top-level document navigation only. It is not always a good replacement for `TabControl` in WPF. Instead, UWP's `Pivot` control is sometimes used for tab functionality.
 1. `RadioButtons` is a container to easily create groups of individual `RadioButton` controls (with accessiblity improvements, etc.)
 1. `ProgressRing` was updated to use Lottie animations in WinUI Library v2.5-v2.6
 1. WPF's `ContextMenu` was generalized and replaced by `MenuFlyout` in UWP. Avalonia; however, still supports both.
 
## License

This document is licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
