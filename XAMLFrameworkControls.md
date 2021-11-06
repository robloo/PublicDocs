Last Updated 06 November 2021 | License CC BY-SA 4.0

# XAML Framework Controls

This document lists supported controls for each XAML framework excluding some primitives and shapes (Ellipse, Rect, etc.). It also describes some of the differences in implemenation or usage where appropriate. 

The following frameworks are included so far:

 * Avalonia
 * UWP (with the WinUI 2.x library), also implicitly includes the Uno Platform
 * WPF

## Controls

As WPF is the first XAML framework, it occurs first and all others are listed alphabetically in their own column. The Uno Platform generally supports all controls in UWP/WinUI3 and therefore does not need its own column. 

| WPF |	UWP |	Comments |
|-----|-----|----------|
|🔲                          |✅ AppBarButton	         | |
|🔲                          |✅ AppBarSeparator	       | |
|🔲                          |✅ AppBarToggleButton	   | |
|🔲                          |✅ AnimatedVisualPlayer <br/> *(WinUI 2.1)* | |
|🔲                          |✅ AutoSuggestBox	       | |
|✅ Border                   |✅ Border	                | |
|🔲                          |✅ BreadcrumbBar <br/> *(WinUI 2.6)* | |
|✅ BulletDecorator	        |🔲                        | |
|✅ Button                   |✅ Button	                | |
|✅ DatePicker               |✅ CalendarDatePicker	    | See differences |
|✅ Calendar	                |✅ CalendarView	          | |
|✅ Canvas	                  |✅ Canvas                 | |	
|🔲                          |✅ CaptureElement	       | |
|✅ CheckBox                 |✅ CheckBox	              | |
|🔲                          |✅ ColorPicker	           | |
|✅ ComboBox	                |✅ ComboBox               | |	
|✅ ToolBar                  |✅ CommandBar	            | |
|🔲                          |✅ CommandBarFlyout <br/> *(WinUI 2.0)* | |	
|✅ ContentControl           |✅ ContentControl	        | |
|✅ ContentPresenter         |✅ ContentPresenter	      | |
|✅ DataGrid	                |🔲 *(WCT Version)*        | See differences |
|🔲                          |✅ DatePicker	           | |
|🔲                          |✅ DatePickerFlyout	     | |
|✅ DockPanel		            |🔲 *WCT Version*          | |
|✅ DocumentViewer		        |🔲                        | |
|🔲                          |✅ DropDownButton <br/> *(WinUI 2.0)* | |
|✅ Expander	                |✅ Expander <br/> *(WinUI 2.6)* | *WCT Version* as well |
|🔲                          |✅ FlipView	             | |
|✅ FlowDocumentPageViewer		|🔲                        | |
|✅ FlowDocumentReader		    |🔲                        | |
|✅ FlowDocumentScrollViewer |🔲                        | |
|🔲                          |✅ Flyout	               | |
|✅ Frame                    |✅ Frame	                | |
|✅ Grid                     |✅ Grid                   | |	
|✅ GridSplitter	            |🔲 *(WCT Version)*        | |
|🔲                          |✅ GridView	             | |
|✅ GroupBox		              |🔲                        | |
|🔲                          |✅ Hub	                   | |
|🔲                          |✅ HubSection	           | |
|🔲                          |✅ HyperlinkButton	       | |
|✅ Image                    |✅ Image	                | |
|🔲                          |✅ InfoBar <br/> *(WinUI 2.5)* | |
|🔲                          |✅ InkCanvas	             | |
|🔲                          |✅ InkToolbar             | |
|✅ ItemsControl             |✅ ItemsControl	          | |
|🔲                          |✅ ItemsPresenter	       | |
|🔲                          |✅ ItemsRepeater <br/> *(WinUI 2.1)* | |
|✅ Label		                |🔲                        | |
|✅ ListBox                  |✅ ListBox	              | |
|✅ ListView	                |✅ ListView	              | |
|🔲                          |✅ MapControl             | |
|🔲                          |✅ MediaElement	         | |
|🔲                          |✅ MediaTransportControls | |
|✅ Menu                     |✅ MenuBar <br/> *(WinUI 2.0)* | |
|✅ MenuItem                 |✅ MenuBarItem <br/> *(WinUI 2.0)* | |
|✅ ContextMenu	            |✅ MenuFlyout	            | |
|🔲                          |✅ NavigationView	       | |
|🔲                          |✅ NumberBox <br/> *(WinUI 2.3)* | |
|✅ Panel		                |🔲                        | |
|🔲                          |✅ ParallaxView	         | |
|✅ PasswordBox              |✅ PasswordBox	          | |
|🔲                          |✅ PersonPicture		       | |
|🔲                          |✅ PipsPager <br/> *(WinUI 2.6)* | |
|🔲                          |✅ Pivot		               | |
|🔲                          |✅ PivotItem		           | |
|✅ Popup                    |✅ Popup		              | |
|✅ PrintDialog		          |🔲                        | |
|✅ ProgressBar              |✅ ProgressBar		        | |
|🔲                          |✅ ProgressRing		       | |
|🔲                          |✅ PullToRefresh		       | |
|✅ RadioButton	            |✅ RadioButton		        | |
|🔲   	                     |✅ RadioButtons <br/> *(WinUI 2.3)* | |
|🔲                          |✅ RatingControl		       | |
|✅ Rectangle                |✅ Rectangle		          | |
|🔲                          |✅ RefreshContainer <br/> *(WinUI 2.0)* | |
|🔲                          |✅ RelativePanel		       | |
|✅ RepeatButton             |✅ RepeatButton	          | |
|✅ RichTextBox              |✅ RichEditBox	          | |
|🔲                          |✅ RichTextBlock	         | |
|🔲                          |✅ RichTextBlockOverflow	 | |
|✅ ScrollBar	              |✅ ScrollBar	            | |
|✅ ScrollContentPresenter   |✅ ScrollContentPresenter	| |
|✅ ScrollViewer	            |✅ ScrollViewer	          | |
|🔲                          |✅ SearchBox              | |
|🔲                          |✅ SemanticZoom	         | |
|✅ Separator		            |🔲                        | |
|✅ Slider	                  |✅ Slider                 | |
|🔲                          |✅ SplitButton <br/> *(WinUI 2.0)* | |
|🔲                          |✅ SplitView	             | |
|✅ StackPanel	              |✅ StackPanel	            | |
|✅ StatusBar		            |🔲                        | |
|🔲                          |✅ SwipeControl <br/> *(WinUI 2.0)* | |
|✅ TabControl	              |✅ TabView <br/> *(WinUI 2.2)* | |
|🔲                          |✅ TeachingTip <br/> *(WinUI 2.1)* | |
|✅ TextBlock                |✅ TextBlock	            | |
|✅ TextBox                  |✅ TextBox	              | |
|🔲                          |✅ TimePicker	           | |
|🔲                          |✅ TimePickerFlyout	     | |
|✅ ToggleButton             |✅ ToggleButton	          | |
|🔲                          |✅ ToggleSplitButton <br/> *(WinUI 2.0)* | |
|🔲                          |✅ ToggleSwitch	         | |
|✅ ToolTip	                |✅ ToolTip	              | |
|✅ TreeView                 |✅ TreeView	              | |
|🔲                          |✅ TwoPaneView	           | |
|🔲                          |✅ VariableSizedWrapGrid	 | |
|✅ Viewbox	                |✅ Viewbox	              | |
|🔲                          |✅ WebView	               | |
|✅ WrapPanel		            |🔲 *(WCT Version)*        | |
|✅ Window	                  |🔲                        | |
| **Icons** |
|🔲                          |✅ AnimatedIcon <br/> *(WinUI 2.6)* | |
|🔲                          |✅ BitmapIcon             | |
|🔲                          |✅ FontIcon               | |
|🔲                          |✅ ImageIcon <br/> *(WinUI 2.6)* | |
|🔲                          |✅ PathIcon               | |

Note that *(WCT Version)* indicates a version of the control exists for UWP in the [Windows Community Toolkit](https://docs.microsoft.com/en-us/windows/communitytoolkit/).

## Control Differences

 1. The UWP `DatePicker` is different from WPF's `DatePicker`. The WPF `DatePicker` is closer to the UWP `CalendarDatePicker` in functionality as they both have a drop-down calendar. A picker to select a date without a calendar view does not exist in WPF.
 1. The `DataGrid` in both Avalonia and UWP's Windows Community Toolkit is based on the Silverlight version of the control -- not the full-featured WPF version. As such, WPF's `DataGrid` is more powerful in certain areas. In addition, the Windows Community Toolkit version of the control has many bugs that Microsoft announced they will not fix. Avalonia, however, makes an attempt to fix these issues.
 1. UWP's `TabView` is designed for top-level document navigation only. It is not always a good replacement for `TabControl` in WPF. Instead, UWP's `Pivot` control is sometimes used for tab functionality.
 1. `RadioButtons` is a container to easily create groups of individual `RadioButton` controls (with accessiblity improvements, etc.)
 1. `ProgressRing` was updated to use Lottie animations in WinUI Library v2.5-v2.6

## License

This document is licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
