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
| &#10006;                 |	AppBarButton	          | |
| &#10006;                 |	AppBarSeparator	       | |
| &#10006;                 | AppBarToggleButton	    | |
| &#10006;                 | AnimatedVisualPlayer <br/> *(WinUI v2.1)* |  |	
| &#10006;                 |	AutoSuggestBox	        | |
| Border                   |	Border	                | |
| &#10006;                 |	BreadcrumbBar <br/> *(WinUI v2.6)*	        | |
| BulletDecorator	         |	&#10006;               | |
| Button                   |	Button	                | |
| DatePicker               |	CalendarDatePicker	    | See below section |
| Calendar	                | CalendarView	          | |
| Canvas	                  | Canvas                 | |	
| &#10006;                 |	CaptureElement	        | |
| CheckBox                 |	CheckBox	              | |
| &#10006;                 |	ColorPicker	           | |
| ComboBox	                | ComboBox               | |	
| ToolBar                  |	CommandBar	            | |
| &#10006;                 |	CommandBarFlyout <br/> *(WinUI v2.0)*	      | |	
| ContentControl           | ContentControl	        | |
| ContentPresenter         |	ContentPresenter	      | |
| DataGrid	               | &#10006;               | Available for UWP in the Windows Community Toolkit (albeit with many bugs) |
| &#10006;                 |	DatePicker	            | A picker to select a date without a calendar view does not exist in WPF. |
| &#10006;                 |	DatePickerFlyout	      | |
| DockPanel		              |	&#10006;               | Available for UWP in the Windows Community Toolkit |
| DocumentViewer		         |	&#10006;               | |
| &#10006;                 |	DropDownButton	        | First introduced in WinUI Library v2.0 |
| Expander	                | Expander               |	First introduced in WinUI Library v2.6. Also available for UWP in the Windows Community Toolkit |
| &#10006;                 |	FlipView	              | |
| FlowDocumentPageViewer		 |	&#10006;               | |
| FlowDocumentReader		     |	&#10006;               | |
| FlowDocumentScrollViewer |	&#10006;               | |
| &#10006;                 |	Flyout	                | |
| Frame                    |	Frame	                 | |
| Grid                     |	Grid                   | |	
| GridSplitter	            | &#10006;               |	Available for UWP in the Windows Community Toolkit |
| &#10006;                 |	GridView	              | |
| GroupBox		               | &#10006;               | |
| &#10006;                 |	Hub	                   | |
| &#10006;                 |	HubSection	            | |
| &#10006;                 |	HyperlinkButton	       | |
| Image                    |	Image	                 | |
| &#10006;                 | InfoBar                | Provides interactive status and message information to the user. First introduced in WinUI Library v2.5 |
| &#10006;                 |	InkCanvas	             | |
| &#10006;                 |	InkToolbar	            | |
| ItemsControl             |	ItemsControl	          | |
| &#10006;                 |	ItemsPresenter	        | |
| &#10006;                 |	ItemsRepeater	         | First introduced in WinUI Library v2.1 |
| Label		                  | &#10006;               | Exists in WPF to align with Windows Forms |
| ListBox                  |	ListBox	               | |
| ListView	                | ListView	              | |
| &#10006;                 | MapControl	            | |
| &#10006;                 |	MediaElement	          | |
| &#10006;                 |	MediaTransportControls	| |
| Menu                     |	MenuBar	               | First introduced in the Windows Community Toolkit then WinUI Library v2.0 |
| MenuItem                 | MenuBarItem            | First introduced in WinUI Library v2.0 |
| ContextMenu	             | MenuFlyout	            | |
| &#10006;                 |	NavigationView	        | |
| &#10006;                 |	NumberBox     	        | First introduced in WinUI Library v2.3 |
| Panel		                  | &#10006;               | |
| &#10006;                 |	ParallaxView	          | |
| PasswordBox              |	PasswordBox	           | |
| &#10006;                 |	PersonPicture		        | |
| &#10006;                 |	PipsPager     	        | First introduced in WinUI Library v2.6 |
| &#10006;                 |	Pivot		                | |
| &#10006;                 |	PivotItem		            | |
| Popup                    |	Popup		                | |
| PrintDialog		            |	&#10006;               | |
| ProgressBar              |	ProgressBar		          | |
| &#10006;                 |	ProgressRing		         | Updated to use Lottie animations in WinUI Library v2.5-v2.6 |
| &#10006;                 |	PullToRefresh		        | |
| RadioButton	             | RadioButton		          | |
| &#10006;   	             | RadioButtons		         | Container to easily create groups for RadioButtons (with accessiblity improvements, etc.) First introduced in WinUI Library v2.3 |
| &#10006;                 |	RatingControl		        | |
| Rectangle                |	Rectangle		            | |
| &#10006;                 |	RefreshContainer	      | First introduced in WinUI Library v2.0 |
| &#10006;                 |	RelativePanel		        | |
| RepeatButton             |	RepeatButton	          | |
| RichTextBox              |	RichEditBox	           | |
| &#10006;                 |	RichTextBlock	         | |
| &#10006;                 |	RichTextBlockOverflow	 | |
| ScrollBar	               | ScrollBar	             | |
| ScrollContentPresenter   |	ScrollContentPresenter	| |
| ScrollViewer	            | ScrollViewer	          | |
| &#10006;                 | SearchBox              | |
| &#10006;                 |	SemanticZoom	          | |
| Separator		              | &#10006;               | |
| Slider	                  | Slider                 | |
| &#10006;                 |	SplitButton	           | First introduced in WinUI Library v2.0 |
| &#10006;                 |	SplitView	             | |
| StackPanel	              | StackPanel	            | |
| StatusBar		              | &#10006;               | No longer a UI convention |
| &#10006;                 | SwipeControl	          | First introduced in WinUI Library v2.0 |
| TabControl	              | TabView	               | First introduced in WinUI Library v2.2. Originally, Pivot was used to replace tabs. |
| &#10006;                 |	TeachingTip            |	First introduced in WinUI Library v2.1 |
| TextBlock                |	TextBlock	             | |
| TextBox                  |	TextBox	               | |
| &#10006;                 |	TimePicker	            | |
| &#10006;                 |	TimePickerFlyout	      | |
| ToggleButton             |	ToggleButton	          | |
| &#10006;                 |	ToggleSplitButton	     | First introduced in WinUI Library v2.0 |
| &#10006;                 |	ToggleSwitch	          | |
| ToolTip	                 | ToolTip	               | |
| TreeView                 |	TreeView	              | |
| &#10006;                 |	TwoPaneView	           | |
| &#10006;                 |	VariableSizedWrapGrid	 | |
| Viewbox	                 | Viewbox	               | |
| &#10006;                 | WebView	               | |
| WrapPanel		              | &#10006;               | Available for UWP in the Windows Community Toolkit |
| Window	                  | &#10006;               |	There is no top-level window concept in UWP |
| **Icons** |
| &#10006;                 |	AnimatedIcon           | First introduced in WinUI Library v2.6 |
| &#10006;                 |	BitmapIcon             | |
| &#10006;                 |	FontIcon               | |
| &#10006;                 |	ImageIcon              | First introduced in WinUI Library v2.6 |
| &#10006;                 |	PathIcon               | |

## Control Differences

 * The UWP DatePicker is different from WPF's DatePicker. The WPF DatePicker is closer to the UWP CalendarDatePicker in functionality.
