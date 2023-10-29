Last Updated 29 October 2023 | License CC BY-SA 4.0

# XAML Framework Comparison

XAML-based UI frameworks have evolved considerably over the years. This is best illustrated in the below graphic. The bulk of these frameworks: Avalonia UI, the Uno Platform and .NET MAUI support cross-platform applications. In fact, except for Avalonia UI, the need for cross-platform XAML is the main driving force behind their development. If Microsoft stepped in earlier and created a true Flutter-like cross-platform UI framework years ago we likely never would have ended up with all of these options. This is both good and bad: Good that we now have lots of options to choose from and bad that all have a different object model and dialect of XAML.

While following the various .NET UI frameworks, the same question was being asked: Which XAML UI framework should be used to write apps? This is a valid and important question. For there to be so many options today indicates there is no clear solution. That said, on a per-app basis, the answer to the question is easier as each of the frameworks have clear strengths and weaknesses which can be compared with a specific application's needs. By outlining the strengths and weaknesses in the main XAML-based UI frameworks, this document aims to help companies and developers answer the question:

 > Which XAML framework should I use for my cross-platform app?

<p align="center">
<img src="https://github.com/robloo/PublicDocs/blob/master/XAMLFrameworkEvolution.png?raw=true" width="800px">
</p>

At a very high level the difference in the three cross-platform XAML frameworks can be described in terms of architecture. All frameworks are based on the same .NET (formerly Mono) tooling. Xamarin's contributions to .NET allowing all of these frameworks to exist must not be overlooked. Additionally, with .NET 6+ all of these frameworks are using the same runtime and core libraries on every platform.

 * [**Avalonia UI**](https://github.com/AvaloniaUI/Avalonia) : Fully renders controls and user-interface elements itself. This is the same approach that Flutter uses.
 * [**.NET MAUI**](https://github.com/dotnet/maui) : Standardizes a set of names, properties and events and applies/links them to platform-specific native controls. Mapping to native controls is a least-common-denominator approach. If a single platform doesn't support a feature it likely won't be in MAUI for all platforms (without dropping into platform-specific code).
 * [**Uno Platform**](https://github.com/unoplatform/uno) : Uses a select few platform-specific primitives to build and render controls. For high level controls this gives nearly pixel-perfect results. This means the Uno Platform behaves like Avalonia UI or Flutter which fully render their controls; however, it also supports direct embedding of platform-specific native controls. It is a hybrid architecture.

Other Microsoft XAML-based frameworks such as WPF and UWP/WinUI are skipped because they were historically not cross-platform. However, WPF can now run cross-platform using [Wine Mono](https://github.com/madewokherd/wine-mono) or [Avalonia XPF](https://avaloniaui.net/XPF). WinUI/UWP itself is already supported cross-platform using the Uno Platform discussed below.

**Project links**

| Project | Website | GitHub | Docs |
|---------|---------|--------|------|
| Avalonia UI | [avaloniaui.net](https://avaloniaui.net/) | [github.com/AvaloniaUI/Avalonia](https://github.com/AvaloniaUI/Avalonia) | [docs.avaloniaui.net](https://docs.avaloniaui.net/) |
| .NET MAUI | [maui](https://dotnet.microsoft.com/en-us/apps/maui) | [github.com/dotnet/maui](https://github.com/dotnet/maui) | [docs.microsoft.com/en-us/dotnet/maui/](https://docs.microsoft.com/en-us/dotnet/maui/) |
| Uno Platform | [platform.uno](https://platform.uno/) | [github.com/unoplatform/uno](https://github.com/unoplatform/uno) | [platform.uno/docs/](https://platform.uno/docs/articles/intro.html) |

**Additional Frameworks**

Additional options are available for .NET cross-platform UI development not featured in this document. These other frameworks or methodologies deserve a mention even though they aren't included in the full comparison.

  1. [WPF](https://github.com/dotnet/wpf) : As mentioned, WPF can now run cross-platform using [Wine Mono](https://github.com/madewokherd/wine-mono) or [Avalonia XPF](https://avaloniaui.net/XPF). This possibility should not be overlooked for existing applications with large WPF codebases.
  1. [Eto.Forms](https://github.com/picoe/Eto) : A UI framework that, similar to .NET MAUI, constructs UI using platform-native controls. A version of XAML can also be used to serialize and construct the UI.
  1. [Noesis GUI](https://www.noesisengine.com/) : Intended for game development, Noesis GUI recreates WPF for usage in game engines (like Unity) to construct user-interfaces. XAML support is so extensive it even works with Microsoft Blend. If it worked outside of game engines and had better licensing for smaller applications this is a very interesting tech that pre-dates some other cross-platform XAML implementations.
  1. [OpenSilver](https://github.com/OpenSilver/OpenSilver) A cross-platform re-implementation of the Silverlight framework that transpiles C#/XAML/.NET into WebAssembly (or JavaScript) and HTML/CSS. This project only supports the Silverlight dialect of XAML which is a less-powerful derivitive of WPF and the basis for later UWP and WinUI dialects. Like the original Silverlight, applications written with OpenSilver are only designed to run in a web browser.
  1. [.NET MAUI + Blazor Hybrid](https://learn.microsoft.com/en-us/aspnet/core/blazor/hybrid/tutorials/maui?view=aspnetcore-7.0) : .NET MAUI can host Blazor web apps (within a BlazorWebView control) making it function as more of an application plus services container. This is a very attractive option for those that wish to repackage and distribute existing web apps as mobile applications.
  1. [.NET MAUI + Avalonia UI Hybrid](https://github.com/AvaloniaUI/AvaloniaMauiHybrid) : .NET MAUI can also host Avalonia UI views (within an AvaloniaView control) again making it function as more of an application plus services container. Since Avalonia is only a UI framework this is an attractive option to easily get all of .NET MAUI's additional platform-abstracted functionality (Essentials) as well as easier mobile packaging and deployment.

Making .NET MAUI into more of an application plus services container and then hosting other UI frameworks like Blazor or Avalonia UI is an attractive option. It's possible this architecture will pick up more traction going forward and is definitely an area to watch closely.

## Comparison Table

Each framework performs differently – significantly in some places. The table below highlights these differences focusing on high-impact areas or features. Where all platforms behave the same an entry may be excluded (focusing on only the differences).

The comparison is based on a lot of research and experience with the various frameworks; however, it is subjective. Also note that experience with .NET MAUI is least of the three which may bias rankings.

 * ✔️ means the feature is supported, ❌ means it is not
 * ⭐⭐⭐ is the highest/best rating, ⭐ is the lowest/worst

|                               | Avalonia | .NET MAUI| Uno Platform |
|-------------------------------|----------|----------|----------|
| ▶ **Features**                |
| MVVM pattern                  | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐ |
| MVU pattern                   | ❌          | ✔️｜⭐⭐   | ✔️｜⭐      |
| Pixel-perfect rendering       | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐   |
| Lookless controls             | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐⭐ |
| Styling and themes            | ✔️｜⭐⭐⭐ | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| Supports uniform look and feel| ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐⭐ |
| Platform native look and feel | ❌          | ✔️｜⭐⭐⭐ | ✔️｜⭐      |
| Platform consistency          | ✔️｜⭐⭐⭐ | ✔️｜⭐      | ✔️｜⭐⭐   |
| Native control integration    | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐⭐ |
| XAML syntax & code sharing    | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| C# code-behind sharing        | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| Hot-reloading                 | ❌          | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐⭐ |
| 3rd party support             | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| Advanced text formatting      | ✔️｜⭐⭐⭐ | ❌          | ❌          |
| Non-UI features               | ❌          | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐  |
| ▶ **Strategy & Development**  |
| Performance (theoretical)     | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐   |
| Mobile app stability          | ⭐      | ⭐⭐   | ⭐⭐   |
| Desktop app stability         | ⭐⭐⭐ | ⭐⭐   | ⭐      |
| Available controls            | ⭐      | ⭐⭐   | ⭐⭐⭐ |
| Code license                  | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐   |
| Free support                  | ⭐      | ⭐⭐   | ⭐⭐⭐ |
| Paid support                  | ⭐⭐⭐ | ⭐⭐   | ⭐⭐⭐ |
| Project speed                 | ⭐⭐   | ⭐⭐   | ⭐⭐   |
| Ease of contribution          | ⭐⭐⭐ | ⭐⭐   | ⭐⭐   |
| Code-base readability         | ⭐⭐⭐ | ⭐      | ⭐     |
| Developer experience          | ⭐⭐⭐ | ⭐⭐   | ⭐      |
| Corporate backing             | ⭐⭐    | ⭐⭐   | ⭐⭐⭐ |
| ▶ **IDE & Tooling Integration** |
| Visual Studio                 | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| Visual Studio Code            | ✔️｜TBD     | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐ |
| Rider                         | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐⭐   |
| Design tool integration       | ❌          | ❌          | ✔️｜⭐⭐  |
| ▶ **Platform Support**        |
| iOS Mobile                    | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| Android Mobile                | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐       |
| Windows Desktop               | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| macOS Desktop                 | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐       |
| Linux Desktop                 | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐      |
| Web Browser (WASM)            | ✔️｜⭐      | ❌          | ✔️｜⭐⭐⭐ |
| ▶ **Overall Platform Support** |
| Mobile                        | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| Desktop                       | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐       |
| Web                           | ✔️｜⭐      | ❌          | ✔️｜⭐⭐⭐ |

Comparisons were last updated in early 2023.

## Comparison Remarks

<dl>
  <dt>MVU Pattern</dt>
  <dd>

.NET MAUI has the most complete support for what is traditionally thought of as the MVU pattern with [C# Markup](https://learn.microsoft.com/en-us/dotnet/communitytoolkit/maui/markup/markup) and [Comet](https://github.com/dotnet/Comet). This is an active area of experimentation and development and it's expected to be supported at the same level of MVVM going forward.
<br/><br/>
The Uno Platform has developed their own variation of MVU known as [MVU-X](https://platform.uno/docs/articles/external/uno.extensions/doc/Overview/Reactive/overview.html). This is quite a bit different than other offerings and has a higher learning curve but does integrate better with XAML data binding. The long-term viability of a brand-new approach to the MVU pattern will have to be seen. It might be best to approach with caution until experimentation in this area settles down.
<br/><br/>
Avalonia has no first party offering to support the MVU pattern. However, there are two libraries that provide support for writing UI using a declarative syntax instead of XAML. [Avalonia.Markup.Declarative](https://github.com/AvaloniaUI/Avalonia.Markup.Declarative) supports a lot of the C# markup concepts by providing helper methods and extensions on top of Avalonia. This provides a good way of writing UI in C# that can follow the MVU pattern with no XAML. Another option for F# developers is [Avalonia.FuncUI](https://github.com/fsprojects/Avalonia.FuncUI) which provides similar support specifically for the F# language. It's useful to note that of all the frameworks Avalonia has the best support for F# (provided by the community).
  </dd>

  <dt>Pixel-Perfect Rendering</dt>
  <dd>

Of the three frameworks, only Avalonia supports true "pixel-perfect" rendering. This is due to the architectures and only Avalonia fully draws its own user-interface and controls. The Uno Platform, while attempting to achieve "pixel-perfect", often has differences between platforms as a result of using native control primitives. The Uno Platform (except on Skia) never fully draws itself and therefore is never "pixel-perfect" being just a close approximation.
  </dd>

  <dt>Lookless Controls, Styling & Themes</dt>
  <dd>

When a developer thinks of XAML they usually think of lookless controls. The ability to completely change the style and default template of a control to turn it into something completely different was a major feature of WPF. Both Avalonia and the Uno Platform fully support their own versions of lookless controls and re-templating. However, MAUI does not have this ability and instead only supports changing some common properties.
<br/><br/>
Think of MAUI like older interface toolkits like Windows Forms in this regard. As an example, this means placing an icon or graphic inside of a button is not supported in MAUI while it is trivial in other XAML frameworks.
  </dd>

  <dt>Platform Consistency</dt>
  <dd>

Consistency of the application and code is very import during development with a cross-platform framework. You don't want to develop and validate a feature on one platform then find it doesn't work the same on another. In this area .NET MAUI is very poor as it forwards to native controls on each platform. It's necessary to not only validate everywhere, but write custom controls multiple times while spending a lot of time tweaking things to look uniform (similar to getting a web page to render correctly on all browsers).
<br/><br/>
Uno Platform is better than MAUI in most cases; however, it too has some serious issues where features simply don't exist on all platforms. Those features that do exist everywhere usually behave consistently but there are subtle difference that may be very difficult to fix.
<br/><br/>
Avalonia UI easily rises above the other frameworks here because of the architecture differences. Avalonia fully renders itself so it's always going to look exactly the same on every platform (except for fonts, input differences, popups etc.).
  </dd>

  <dt>Native Control Integration</dt>
  <dd>

Both .NET MAUI and the Uno Platform are built on top of, and fully integrated with, Xamarin Native. This means both frameworks have access to the platform-specific native controls through C# bindings. This is extremely powerful for accessing native platform features and controls with almost no compromises. It is possible to add a native control directly in both XAML and code-behind as any other control built into the framework itself.
<br/><br/>
Avalonia UI in contrast is its own UI layer that does not integrate directly with Xamarin Native (and its platform-specific controls). Instead, Avalonia does provide a NativeControlHost that allows embedding native controls within an Avalonia application. However, this is not as streamlined as what is available with MAUI or the Uno Platform. Avalonia UI, unlike WPF, also solves the "airspace problem" with 3D elements and can draw UI directly on various surfaces. This actually allows Avalonia to run inside game engines or on top of DirectX surfaces which isn't possible in the other frameworks.
  </dd>

  <dt>XAML Syntax & Code Sharing</dt>
  <dd>

The Uno Platform has the highest rating for code sharing. It uses the same dialect of XAML and object model as UWP/WinUI which makes it 100% compatible in both XAML and C#. Both Avalonia and MAUI deviate from past XAML versions and are not compatible with either WPF or UWP/WinUI. That said, Avalonia makes an effort to be similar to WPF in object models where MAUI otherwise deviates for little reason (Height/Width, TextBlock, etc.). Avalonia also succeeds in several cases of being a more powerful next-generation of the WPF syntax and object model. Several things are much easier to do in Avalonia due to the XAML changes (styling, IsVisible as a bool, simplified Grid rows/columns syntax, etc.). Since Avalonia compatibility and code sharing with existing WPF code is better the overall rating is also higher.
  </dd>

  <dt>Advanced Text Formatting</dt>
  <dd>

The original XAML framework WPF has an extremely advanced text formatting API (FlowDocument). This is still more advanced than what is found today in WinUI 3 or UWP before it. In fact, until Avalonia UI version 11.0, no other XAML framework supported advanced text features. Now Avalonia UI has nearly the same API as WPF and can do things with text formatting and measurement simply impossible in .NET MAUI and Uno Platform. Due to architecture differences it's likely Avalonia UI will continue to be the only framework supporting advanced text (outside 3rd party controls) for the foreseeable future. This includes controls such as RichTextBox which is possible to implement in Avalonia but very difficult in the Uno Platform and nearly impossible in .NET MAUI.
  </dd>

  <dt>Non-UI Features</dt>
  <dd>

The major downside to Avalonia UI is that is it only a UI framework. .NET MAUI has the essentials package and the Uno Platform is an entire app development platform following UWP. Both .NET MAUI and Uno Platform can be thought of as much more than simply a UI framework. This means things such as persistent settings, file handling, authentication, localization and device permissions are available right away in MAUI or Uno Platform but not in Avalonia. Uno Platform even has advanced audio-related APIs found only in UWP that work cross-platform.
<br/><br/>
Uno Platform, however, attempts to cover the entire UWP API-surface area which is huge. The entire API is auto-generated with unimplemented stubs for a lot of functionality. This means the majority of non-UI API's are unavailable and will throw exceptions if they are used in apps. This does create some problems during development but compilation will show which unimplemented APIs are being used. Even so, Uno Platform still has more non-UI functionality than other frameworks.
  </dd>

  <dt>Performance</dt>
  <dd>

XAML comes from desktop origins and as such is fairly resource intensive. WPF (the original XAML framework) usually builds the entire view from XAML markup at runtime which can be a serious performance hit at first load. Additionally, using MVVM, controls are bound to view models using reflection bindings which are inherently slow compared to compiled code. Bottom-line XAML controls traditionally have higher performance and system requirements which may be a concern for mobile or cloud platforms.
<br/><br/>
UWP, and therefore the Uno Platform, improves on this by allowing lazy loading through x:Load. They also both support compiled bindings using x:Bind. MAUI's architecture sidesteps the first issue completely by using native controls. Avalonia UI has largely switched to pre-compiled XAML and compiled bindings which solves both problems as well. All three of these platforms have better theoretical performance than WPF.
<br/><br/>
The MVU pattern as it relates to performance should not be overlooked. The UI isn't constructed from XAML markup – it is constructed in-code along with the logic and what normally would be code-behind. This by default means controls and user interface elements are only constructed when they are referenced by code and needed for display. In this way performance using the MVU pattern is expected to exceed the performance of MVVM pattern applications. Both MAUI and Uno Platform support the MVU pattern. Avalonia also supports creating UI entirely in code with no XAML which achieves the same performance benefits.
<br/><br/>
Performance in .NET MAUI is somewhat unintuitively rated two stars which is below Avalonia at three. The reason for this, even though MAUI uses native controls, is interop. This is mitigated by native compilation for the most part but any C# integrating with Android controls has a performance penalty. Avalonia, however, fully renders itself and does not interact with Androids native control elements (unless hosting native views). This means Avalonia can essentially have the performance of a video game.
<br/><br/>
Uno Platform performance is generally adequate on most platforms. However, there are serious interop performance issues on Android between the .NET runtime and the Java runtime. This is a problem with .NET Android itself. However, due to the architecture of the Uno Platform (integrating with native controls) this interop is always required. That means, on Android, Uno Platform has fundamentally inferior performance to the other frameworks and high-performance Uno Platform apps on Android are not currently possible.
  </dd>

  <dt>App Stability</dt>
  <dd>

Mobile app stability of MAUI is ranked the same as the Uno Platform; however, it is very common to encounter per-platform layout bugs that require a lot of special-case code and markup. The Uno Platform also has a number of unhandled cases and several bugs that will appear throughout development. This is largely a result of the strategy where rapid development pace is prioritized over correctness and completeness. Avalonia UI in contrast is developed with stability in mind from the start: the features it has are fully functional. In practice Avalonia UI may be the most stable and easiest to develop for.
  </dd>

  <dt>Code License</dt>
  <dd>

The Uno Platform is not MIT license, it is Apache 2.0. The Apache license is not as permissive as MIT and, among other things, this prevents code sharing back into other MIT licensed frameworks. The Uno Platform can use source code from MIT licensed projects such as WinUI, WPF and Avalonia but these projects largely can't use Uno Platform code. This is why Uno Platform ranks lower here.

Avalonia UI is entirely MIT licensed and can freely share code between most .NET foundation and WinUI projects. Avalonia UI is ideal for companies that need full control over their UI framework to push fixes faster than upstream, ensure app-specific compatiblity, or even swap out custom internals.
  </dd>

  <dt>Support</dt>
  <dd>

Avalonia and the Uno Platform both rank higher than MAUI in terms of paid support even though MAUI is developed by Microsoft. This is primarily due to the agility of the smaller companies. Microsoft is highly bureaucratic now and any feedback or changes, even minor, require extensive discussion before there is movement. This is in contrast to Avalonia which can adopt new features very quickly and Uno Platform which has extremely fast communication. In terms of free support, the Uno Platform has great community response times on par with the larger MAUI community. However, the Uno Platform can generally address bugs and implement features faster.
  </dd>

  <dt>Code-base Readability & Ease of Contribution</dt>
  <dd>

Avalonia UI has the cleanest codebase which significantly lowers the barrier of entry for public contributions. The Uno Platform and .NET MAUI are considerably more complex and the code shows it. Increased complexity in the long term is usually prohibitive in terms of maintenance and stability. In the case of the Uno Platform, this complexity was necessary to meet the architectural objectives and support native control integration.
  </dd>

  <dt>Developer Experience</dt>
  <dd>

Avalonia UI has the best overall developer experience. The code base is easy to read and the IDE and debugging experience is top notch using Rider (less on other IDEs). .NET MAUI is a very close second as it now has first-party integration with Visual Studio that exceeds all others. However, .NET MAUI falls short in overall developer experience due to the need to validate/tweak each feature/view on each platform separately. The Uno Platform has a poor developer experience with little integration in Visual Studio, very long compile times, and difficult debugging. More details about developer experience are available in the IDE integration sections.
  </dd>

  <dt>Corporate Backing</dt>
  <dd>

At first glance .NET MAUI seems to have the strongest corporate backing considering it is developed by Microsoft. However, Microsoft is not putting a lot of resources on the project and the long history of abandoning UI frameworks at Microsoft creates uncertainty.
<br/><br/>
Avalonia, while originally fully open-source, is now backed by a company setup by some of the core team members. This provides a good measure of stability and income to sustain the project. However, there is caution here due to the increasing corporate reach and closed-source progress of the code base. For example, the composition rendering engine is now not a free-license to modify (while the rest of the code is MIT licensed). This should change once v11 is released.
<br/><br/>
The Uno Platform; however, remains in a class of its own with its corporate sponsorship by *nventive* and incredible communication and response times. Their partnership and close communication with Microsoft should also be noted.
  </dd>

  <dt>Visual Studio Integration</dt>
  <dd>

None of the frameworks have three stars for Visual Studio integration. This is because Visual Studio historically focused on Windows-first frameworks like WinForms, WPF, UWP and WinUI and hard-coded support for these in a non-extensible way. However, .NET MAUI support is improving quite a bit (from being almost unusable at launch). Uno Platform's Visual Studio integration leaves a lot to be desired and is clearly the worse of the three which contributes to the poor developer experience. This isn't their fault as Microsoft does not reasonably support any other project types using .xaml files. Avalonia support in Visual Studio is provided with solid previewer support and most things work - by using a special .axaml extension - but XAML isn't nearly as smooth to work with as on other IDE's like Rider.
  </dd>

  <dt>Visual Studio Code Integration</dt>
  <dd>

The Uno Platform team has developed an [extension for Visual Studio Code](https://platform.uno/blog/announcing-net-mobile-debugging-in-vs-code-mobile-development-in-vs-code-with-uno-platform-or-net-maui/) that enables development and, more importantly, debugging of both mobile and web applications. This is a big step forward for VS Code tooling which historically has not been developer friendly as an IDE for C#/.NET applications. Amazingly, the extension also supports .NET MAUI applications. The Uno Platform team really stepped up here and filled a long-standing gap in VS Code support that results in a full three stars for this IDE. Uno Platform apps are now best supported in Visual Studio Code (unless developing as WinUI on Windows where Visual Studio is still best). Note that this extension is not open sourced.

Avalonia UI [announced](https://avaloniaui.net/Blog/avalonia-for-visual-studio-code-early-access,e2464208-4482-4dd1-bd60-fd11c98983dc) (as of July, 2023) a [preview Visual Studio Code extension](https://github.com/AvaloniaUI/Avalonia-VSCode-Extension) that supports XAML code completion as well as previewing. This makes Avalonia UI much more usable in Visual Studio Code and should make it a viable IDE going forward. This section and the above comparison table will be updated when the extension is publicly released and tested.
  </dd>

  <dt>Design Tool Integration</dt>
  <dd>

Right now only the Uno Platform supports a design tool (Figma) to build UI. This support is provided by a closed-source XAML generator. In the past Microsoft Blend was available for WPF to support the same role. The quality and efficiency of generated XAML may be lacking; however, it helps in the designer to developer transition for companies that have a clear separation between these teams.
<br/><br/>
.NET MAUI does not support any design tool and due to its architecture likely never will. However, it has out-of-the-box support for live editing of XAML which gives designers the option of tweaking and adding some UI elements directly in the app before code is added. Uno Platform also supports live editing of XAML.
  </dd>

  <dt>Platform Support</dt>
  <dd>

The Uno Platform has support for the most platforms and can run on almost any device with varying levels of success (its strongest areas being mobile and the web). The Uno Platform supports Windows desktop directly through WinUI/UWP so receives the highest ranking on Windows desktop for being native. It's important to note that in Uno Platform, certain backends and platforms lack features that others have. This can cause issues where you can do things on iOS/Android that you can't in Linux. So platform support is not consistent and should be carefully reviewed. This is especially true on macOS where the Uno Platform runs extremely poorly when last tested (2021). Today it is usually better to build macOS apps using macCatalyst as Uno Platform's iOS support is significantly better and more complete. The Skia backend is also an option across all the desktop platforms (even older versions of Windows). Keep in mind (as noted in the *Performance* section) Uno Platform has inferior performance on Android compared to iOS.
<br/><br/>
Avalonia UI is well ahead of the other frameworks for macOS and Linux desktops platforms. Avalonia has very high marks for Windows desktop as well but isn't using the native UI toolkit so is scored a bit lower than the Uno Platform. Mobile and Web support is newly released in version 11.0 and may take time to stabilize so is scored lower for now. Avalonia's Web implementation renders to an HTML5 canvas. This will never be quite as good as Uno Platforms architecture where it fully integrates as HTML elements.
<br/><br/>
.NET MAUI does not support Linux or the Web at all. It is clearly inferior to the other two in platform coverage.
  </dd>
</dl>

## Per-Platform Framework Recommendation

On a per-platform basis there are frameworks that perform the best. This is also subjective; however, overall the assessment should be directionally correct and factor in all considerations.

<table>
  <tr>
    <th>Platform</th>
    <th colspan="2">Best Framework</th>
  </tr>
  <tr>
    <td>Windows</td>
    <td colspan="2">WPF/WinUI</td>
  </tr>
  <tr>
    <td>macOS</td>
    <td rowspan="3">
      <img src="https://avaloniaui.net/img/logo/avalonia-white-purple.svg" width="40"/>
    </td>
    <td rowspan="3">Avalonia UI</td>
  </tr>
  <tr>
    <td>Linux</td>
  </tr>
  <tr>
    <td>Android</td>
  </tr>
  <tr>
    <td>iOS</td>
	<td colspan="2" rowspan="2">
      <img src="https://uno-website-assets.s3.amazonaws.com/wp-content/uploads/2021/03/24151905/uno-logo-tm.svg" height="40"/>
    </td>
  </tr>
  <tr>
    <td>Web/Wasm</td>
  </tr>
</table>

If an application is needed for desktop platforms only, Avalonia is a very strong choice. Its Windows support is top notch and only ranks below WinUI or WPF because it isn’t the native UI. However, in an application there are no significant limitations and many desktop apps use it already today. In fact, Avalonia even supports things that cannot be done in WPF such as overlay XAML controls over a DirectX surface.

If an application is needed for cross-platform, it may be written in either WinUI or WPF first. Using a WPF code base for Windows will translate well to Avalonia but will still require three different variants of XAML, it also isn’t the latest tech. For this reason it is generally best to use WinUI which can be shared 100% with the Uno Platform. This means only two variants of XAML will be needed.

Also note that:
 * Web/Wasm is a clear advantage of the Uno Platform. Avalonia will have difficulty competing here due to architecture differences (fully rendered with Skia).
 * Avalonia UI is the closest competition to Flutter. It fully renders itself on each platform using Skia (or, optionally, Direct2D on Windows). This has major performance benefits over the Uno Platform especially visible on macOS and Android. In this way, Avalonia has the cleanest architecture of all frameworks and lowest barrier of entry for community engagement.
 * Avalonia UI is positioned as the next generation of WPF and it reimplements most features and then some. Avalonia takes ideas and code from WPF (Grid, text formatting) and WinUI (ItemsRepeater, touch input APIs) while still having several unique ideas not found in other XAML frameworks (advanced styling system closer to CSS in some areas). It is ready today for desktop app developers - especially those with existing WPF code. For UWP/WinUI developers it is a rougher transition but more recent features from UWP/WinUI were added in version 11 to improve the transition. For corporate WPF apps that don't want to change existing code, Avalonia also offers Avalonia XPF which implements the open-sourced WPF code base on top of the Avalonia rendering engine.
 * .NET MAUI is not listed as best for any platform intentionally. It is most useful for small applications without complex UIs. Its usefulness - and ability to share code between platforms - quickly falls behind other frameworks for even moderate app complexity. However, there are certain line-of-business or simpler apps where MAUI may be the better choice. MAUI also, more recently, has the ability to host both Blazor and Avalonia UI which offers an interesting option for certain scenarios.
 * Avalonia is best for versions of Windows before Windows 10. While the Uno Platform also has a solution with its Skia backend, it falls behind considerably in features, stability and completeness.
 * As the table above shows, all platforms can be supported very well using two dialects of XAML: the WinUI/UWP dialect for Windows and mobile with Uno Platform and the Avalonia dialect for others.

Links & References

 1. [Question: XAML Flavor, Architecture & Roadmap](https://github.com/dotnet/maui/issues/43)
 1. [The New .NET Multi-platform App UI](https://devblogs.microsoft.com/xamarin/the-new-net-multi-platform-app-ui-maui)
 1. [Goodbye Xamarin.Forms](https://itnext.io/goodbye-xamarin-forms-f41723fb9fe1)
 1. [Putting “Universal” back into UWP](https://medium.com/@Arlodottxt/putting-universal-back-into-uwp-d2e5a8099bc1)
 1. [Evolution of Client Development: Richard Campbell](https://youtu.be/nbqe9uHWT_c?t=232)
 1. [[Spec] Slim Renderer Architecture](https://github.com/dotnet/maui/issues/28)
 1. [Discussion: Compatibility with WPF, UWP and WinUI](https://github.com/AvaloniaUI/Avalonia/discussions/5596)
 1. [Project Reunion: An End to Microsoft’s UI Madness?](https://medium.com/young-coder/project-reunion-an-end-to-microsofts-ui-madness-1af662e36386)

## Conclusions

It took years to get here but we are finally in a good place with robust UI frameworks covering all uses for .NET. Interestingly, all have evolved to serve a very unique and almost complimentary function. Everything you might want to try is covered by one of the approaches. Today we can write cross-platform XAML/C# applications that work quite well. Most of this technology (aside from the UI layer) is based on Mono so a lot of credit goes to Xamarin for this.

What each framework has accomplished is remarkable. However, none is yet dominant on all platforms and each has their strengths and weaknesses. The Uno Platform comes from an Android/iOS heritage and those mobile platforms are the strongest along with Web. Avalonia comes from a desktop heritage and works best on Windows/Linux/macOS but mobile is advancing rapidly. As of 2023, the macOS support of the Uno Platform is experimental at best and is unusable for more than simple applications. Avalonia, as of 2023, only has initial support for mobile but in practice is more stable on all platforms. Nevertheless, right now it may be necessary to utilize two different UI frameworks to enable cross-platform XAML-based UI.

---

This document is licensed CC BY-SA 4.0. For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
