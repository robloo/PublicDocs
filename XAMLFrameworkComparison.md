最后更新时间 2023年7月27日  | 使用 CC BY-SA 4.0 许可分发

# XAML 框架横向对比

多年来，基于 XAML 的 UI 框架有了很大的发展。下面的图表很好地证明了这个观点。XAML UI 框架的三大巨头：Avalonia UI、Uno Platform 和 .NET MAUI 都支持跨平台的应用。事实上，除了 Avalonia UI，对跨平台 XAML 的需求是它们发展的主要动力。如果微软早一点介入，在几年前就创建一个真正的类似 Flutter 的跨平台 UI 框架，我们很可能永远不会有所有这些选择。这既是好事也是坏事：好的是我们现在有很多选择，坏的是这些选择都有不同的对象模型和 XAML 的“方言”（或者叫“变体”）。

在关注各种 .NET UI 框架的同时，有一个问题是老生常谈的：我应该用哪个 XAML UI 框架来编写应用程序？这是一个有意义且重要的问题。今天我们有这么多的选择，说明没有绝对正确的解决方案。也就是说，在开发某个具体应用的语境下，这个问题比较容易，因为每个框架都有明确的优势和劣势，可以与具体的应用需求进行比较。本文通过对比主流的基于 XAML 的 UI 框架的优势和劣势，旨在帮助公司和开发者回答这个问题：

 > 我应该用哪个 XAML 框架来开发我的跨平台应用程序？
 
<p align="center">
<img src="https://s2.loli.net/2023/06/18/lJ7VjNPuZOSHhqB.png" width="800px">
</p>

高屋建瓴地来看，三个跨平台的 XAML 框架的区别可以用架构来描述。所有的框架都是基于相同的 .NET（以前的 Mono）工具。Xamarin 对 .NET 的贡献使所有这些框架得以存在，这一点不容忽视。此外，通过 .NET 6+，所有这些框架都在每个平台上使用相同的运行时和核心库。

 * [**Avalonia UI**](https://github.com/AvaloniaUI/Avalonia) : 完全自渲染控件和用户界面元素本身。这也是 Flutter 使用的方法。
 * [**.NET MAUI**](https://github.com/dotnet/maui) : 将一组名称、属性和事件标准化，并将它们应用/链接到特定平台的本地控件。与本地控件的映射相当于是一种“取最大公因数”的方法。如果一个平台不支持某项功能，那么它很可能不会出现在 MAUI 的标准库中（即 MAUI 标准库的功能都可以被完美映射到平台本地功能，而不需要用户编写平台特定代码）。
 * [**Uno Platform**](https://github.com/unoplatform/uno) : 使用一些特定的平台基础设施来构建和渲染控件。对于高层级的控件来说，这可以提供几乎完美的像素结果。这意味着 Uno Platform 的行为像 Avalonia UI 或 Flutter 一样，完全渲染界面控件；但是，它也支持直接嵌入平台特定的本地控件。这是一个混合架构。

其他基于微软 XAML 的框架，如 WPF 和 UWP/WinUI 在此处不讨论，因为它们在历史上不是跨平台的。然而，WPF 现在可以使用 [Wine Mono](https://github.com/madewokherd/wine-mono) 或 [Avalonia XPF](https://avaloniaui.net/XPF) 跨平台运行。WinUI/UWP 本身已经可以使用下面讨论的 Uno Platform 支持跨平台。

**相关项目链接**

| 项目 | 网站 | GitHub | 文档 |
|---------|---------|--------|------|
| Avalonia UI | [avaloniaui.net](https://avaloniaui.net/) | [github.com/AvaloniaUI/Avalonia](https://github.com/AvaloniaUI/Avalonia) | [docs.avaloniaui.net](https://docs.avaloniaui.net/) |
| .NET MAUI | [maui](https://dotnet.microsoft.com/en-us/apps/maui) | [github.com/dotnet/maui](https://github.com/dotnet/maui) | [docs.microsoft.com/en-us/dotnet/maui/](https://docs.microsoft.com/en-us/dotnet/maui/) |
| Uno Platform | [platform.uno](https://platform.uno/) | [github.com/unoplatform/uno](https://github.com/unoplatform/uno) | [platform.uno/docs/](https://platform.uno/docs/articles/intro.html) |

**其他框架**

在本文中没有介绍的其他的 .NET 跨平台 UI 开发选项。这些其他的框架或方法值得一提，尽管它们没有被包括在完整的比较中。

  1. [WPF](https://github.com/dotnet/wpf) ：如前所述，WPF 现在可以使用 [Wine Mono](https://github.com/madewokherd/wine-mono) 或 [Avalonia XPF](https://avaloniaui.net/XPF) 跨平台运行。对于拥有大型 WPF 代码库的现有应用程序来说，这种可能性不应该被忽视。
  1. [Eto.Forms](https://github.com/picoe/Eto) ：一个 UI 框架，类似于 .NET MAUI，使用平台原生控件构建 UI。XAML 的一个版本也可以用来序列化和构建 UI。
  1. [Noesis GUI](https://www.noesisengine.com/) ：用于游戏开发，Noesis GUI 重新创建了 WPF，以便在游戏引擎（如 Unity）中使用，构建用户界面。Noesis GUI 对 XAML 的支持非常完善，它甚至可以与 Microsoft Blend 一起工作。如果它能在游戏引擎之外工作，并且对小型应用有更好的许可，这是一个非常有趣的技术，比其他一些跨平台的 XAML 实现要早。
 1. [.NET MAUI + Blazor Hybrid](https://learn.microsoft.com/en-us/aspnet/core/blazor/hybrid/tutorials/maui?view=aspnetcore-7.0)：.NET MAUI 可以承载 Blazor 网络应用（在 BlazorWebView 控件中），使其更像是一个“应用+服务”的容器。对于那些希望将现有网络应用重新打包并作为移动应用发布的人来说，这是一个非常有吸引力的选择。
  1. [.NET MAUI + Avalonia UI Hybrid](https://github.com/AvaloniaUI/AvaloniaMauiHybrid) : .NET MAUI 也可以承载 Avalonia UI 视图（在 AvaloniaView 控件中），这使得它更像是一个“应用+服务”的容器。由于 Avalonia 只是一个 UI 框架，这是一个有吸引力的选择，可以轻松获得 .NET MAUI 的所有额外的平台抽象功能（Essentials），以及更容易的移动打包和部署。

更多地将 .NET MAUI 用作“应用+服务”的容器，然后托管其他 UI 框架，如 Blazor 或 Avalonia UI，是一个有吸引力的选择。这种架构有可能在未来获得更多的吸引力，而且绝对是一个需要密切关注的领域。

## 对比表格

每个框架的表现都不一样——尤其是在某些特定的地方。下面的表格强调了这些差异，重点是影响大的领域或特征。在所有框架都表现相同的情况下，该项条目可能被忽略（即我们只关注差异）。

这种比较是基于大量的研究和对各种框架的经验；但是，它是主观的。还要注意的是，作者对 .NET MAUI 的经验是三者中最少的，这可能会使排名出现偏差。

 * ✔️ 表示支持该功能，❌ 表示不支持。
 * ⭐⭐⭐ 是最高/最好的评价，⭐是最低/最差的评价。

|                               | Avalonia | .NET MAUI| Uno Platform |
|-------------------------------|----------|----------|----------|
| ▶ **特点**                |
| MVVM 模式                  | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐ |
| MVU 模式                   | ❌          | ✔️｜⭐⭐   | ✔️｜⭐      |
| 像素级精确的渲染       | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐   |
| 无外观控件             | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐⭐ |
| 样式和主题            | ✔️｜⭐⭐⭐ | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| 统一的观感和体验 | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐⭐ |
| 平台特色的观感和体验 | ❌          | ✔️｜⭐⭐⭐ | ✔️｜⭐      |
| 平台一致性          | ✔️｜⭐⭐⭐ | ✔️｜⭐      | ✔️｜⭐⭐   |
| 原生控件整合    | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐⭐ |
| XAML 语法和代码共用    | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| C# 代码共用        | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| 热重载                 | ❌          | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐⭐ |
| 第三方支持             | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| 富文本支持      | ✔️｜⭐⭐⭐ | ❌          | ❌          |
| 非 UI 的功能               | ❌          | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐  |
| ▶ **策略与开发**  |
| 理论性能     | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐   |
| 移动端 APP 稳定性         | ⭐      | ⭐⭐   | ⭐⭐   |
| 桌面端 APP 稳定性         | ⭐⭐⭐ | ⭐⭐   | ⭐      |
| 可用控件            | ⭐      | ⭐⭐   | ⭐⭐⭐ |
| 代码许可                  | ⭐⭐⭐  | ⭐⭐⭐ | ⭐⭐   |
| 免费支持                  | ⭐      | ⭐⭐   | ⭐⭐⭐ |
| 付费支持                  | ⭐⭐⭐ | ⭐⭐   | ⭐⭐⭐ |
| 项目活跃度                 | ⭐⭐   | ⭐⭐   | ⭐⭐   |
| 贡献的容易程度          | ⭐⭐⭐ | ⭐⭐   | ⭐⭐   |
| 源代码的可读性        | ⭐⭐⭐ | ⭐      | ⭐     |
| 开发体验          | ⭐⭐⭐ | ⭐⭐   | ⭐      |
| 背后公司          | ⭐⭐    | ⭐⭐   | ⭐⭐⭐ |
| ▶ **IDE 与工具整合** |
| Visual Studio                 | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| Visual Studio Code            | ✔️｜待定   | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐ |
| Rider                         | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐⭐   |
| 设计工具整合       | ❌          | ❌          | ✔️｜⭐⭐  |
| ▶ **平台支持情况**        |
| iOS 移动端                    | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| Android 移动端                | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐       |
| Windows 桌面端               | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| macOS 桌面端                 | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐       |
| Linux 桌面端                 | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐      |
| 浏览器网页端 (WASM)            | ✔️｜⭐      | ❌          | ✔️｜⭐⭐⭐ |
| ▶ **总体平台支持情况** |
| 移动端                        | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| 桌面端                       | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐       |
| 网页端                           | ✔️｜⭐      | ❌          | ✔️｜⭐⭐⭐ |

上述比较的最后一次更新是在2023年初。

## 关于比较的一些说明

<dl>
  <dt>MVU 模式</dt>
  <dd>

.NET MAUI 对传统上被认为是MVU模式的 [C# Markup](https://learn.microsoft.com/en-us/dotnet/communitytoolkit/maui/markup/markup) 和 [Comet](https://github.com/dotnet/Comet) 有最完整的支持。这是一个活跃的实验和开发领域，预计今后会得到与 MVVM 相同水平的支持。
<br/><br/>
Uno Platform 已经开发了他们自己的 MVU 变体，称为 [MVU-X](https://platform.uno/docs/articles/external/uno.extensions/doc/Overview/Reactive/overview.html)。这与其他的产品有很大的不同，有一个更高的学习曲线，但确实与 XAML 数据绑定整合得更好。一个全新的 MVU 模式的方法的长期可行性将不得不看。在这个领域的实验稳定下来之前，最好还是谨慎行事。
<br/><br/>
Avalonia 没有提供第一方产品来支持 MVU 模式。然而，有两个库为使用声明式语法而不是 XAML 编写 UI 提供了支持。[Avalonia.Markup.Declarative](https://github.com/AvaloniaUI/Avalonia.Markup.Declarative) 通过在 Avalonia 之上提供帮助方法和扩展，支持大量的 C# 标记概念。这为用 C# 编写 UI 提供了一个很好的方法，可以遵循 MVU 模式，不需要 XAML。F# 开发者的另一个选择是 [Avalonia.FuncUI]（https://github.com/fsprojects/Avalonia.FuncUI），它专门为 F# 语言提供了类似的支持。值得一提的是，在所有的框架中，Avalonia 对 F# 的支持是最好的（由社区提供）。
  </dd>

  <dt>像素级精确的渲染</dt>
  <dd>
在这三个框架中，只有 Avalonia 支持真正的“像素完美”的渲染。这是由于架构的原因，只有 Avalonia 完全绘制了自己的用户界面和控件。Uno Platform 虽然试图实现“像素完美”，但由于使用了本地控件基础设施，所以平台之间经常会有差异。Uno Platform（除了在 Skia 上）从未完全画出自己，因此从来没有“像素完美”，只是一个近似值。
  </dd>

  <dt>无外观控件、样式和主题</dt>
  <dd>

当一个开发者想到 XAML时 ，他们通常会想到无外观的控件。能够完全改变一个控件的风格和默认模板，将其变成完全不同的东西是 WPF 的一个主要特征。Avalonia 和 Uno Platform 都完全支持他们自己版本的无外观控件和重新模板化。然而，MAUI 不具备这种能力，而只支持改变一些常见的属性。
<br/><br/>
在这方面，可以把 MAUI 想象成像 Windows Forms 这样的老式界面工具箱。举个例子，在 MAUI 中不支持在按钮中放置图标或图形，而在其他 XAML 框架中这是非常容易的。
  </dd>

  <dt>统一的观感和体验</dt>
  <dd>

在跨平台框架的开发过程中，应用程序和代码的一致性是非常重要的。你不希望在一个平台上开发和验证一个功能，然后发现它在另一个平台上的工作方式不一样。在这个领域，.NET MAUI 是非常差的，因为它在每个平台上都会映射到本地控件。它不仅需要到处验证，还需要多次编写自定义控件，同时花费大量的时间来调整事情，使其看起来统一（类似于让一个网页在所有的浏览器上正确呈现）。
<br/><br/>
Uno Platform 在大多数情况下都比 MAUI 好；然而，它也有一些严重的问题，如果某个功能不是在所有平台上都存在。那些在所有平台上都存在的功能通常表现一致，但有一些细微的差别，可能非常难以修复。
<br/><br/>
Avalonia UI 在这里很容易超越其他框架，因为它的架构不同。Avalonia 完全渲染自己，所以它在每个平台上看起来都是一模一样的（除了字体、输入差异、弹出窗口等）。
  </dd>

  <dt>原生控件整合</dt>
  <dd>

.NET MAUI 和 Uno Platform 都是建立在 Xamarin Native 之上，并与之完全集成。这意味着这两个框架都可以通过 C# 绑定来访问特定平台的本地控件。这对于访问本地平台的功能和控件来说是非常强大的，几乎没有任何妥协。在 XAML 和代码后台都可以直接添加一个本地控件，就像框架本身内置的任何其他控件一样。
<br/><br/>
相比之下，Avalonia UI 是它自己的 UI 层，不直接与 Xamarin Native（及其平台特定控件）集成。相反，Avalonia 确实提供了一个 NativeControlHost，允许在 Avalonia 应用程序中嵌入本地控件。然而，这并不像 MAUI 或 Uno Platform 所提供的那样简单。Avalonia UI 与 WPF 不同，也解决了 3D 元素的“空域问题”，可以直接在各种表面上绘制 UI。这实际上允许 Avalonia 在游戏引擎内或在 DirectX 表面上运行，这在其他框架中是不可能的。
  </dd>

  <dt>XAML 语法和代码共用</dt>
  <dd>

Uno Platform 在代码共享方面有最高的评价。它使用与 UWP/WinUI 相同的 XAML 变体和对象模型，这使得它在 XAML 和 C# 中 100% 兼容。Avalonia 和 MAUI 都偏离了过去的 XAML 版本，与 WPF 或 UWP/WinUI 都不兼容。也就是说，Avalonia 努力在对象模型中与 WPF 相似，而 MAUI 在其他方面的偏离没有什么理由（Height/Width，TextBlock，等等）。Avalonia 在几个案例中也成功地成为 WPF 语法和对象模型的更强大的下一代。由于 XAML 的变化，有几件事在 Avalonia 中更容易做到（样式，IsVisible 为 bool，简化的网格行/列语法，等等）。由于 Avalonia 与现有 WPF 代码的兼容性和代码共享性更好，所以总体评价也更高。
  </dd>

  <dt>富文本支持</dt>
  <dd>

最初的 XAML 框架 WPF 有一个极其先进的文本格式化 API（FlowDocument）。这仍然比今天的 WinUI 3 或之前的 UWP 中的内容更先进。事实上，直到 Avalonia UI 11.0 版本，没有其他 XAML 框架支持高级文本功能。现在，Avalonia UI 几乎拥有与 WPF 相同的 API，并且可以做一些在 .NET MAUI 和 Uno Platform 中根本不可能做到的文字格式和测量。由于架构上的差异，在可预见的未来，Avalonia UI 可能将继续成为唯一支持高级文本的框架（在第三方控件之外）。这包括像 RichTextBox 这样的控件，在 Avalonia 中可以实现，但在 Uno Platform 中非常困难，在 .NET MAUI 中几乎不可能。
  </dd>

  <dt>非 UI 的功能</dt>
  <dd>

Avalonia UI 的主要缺点是，它只是一个UI框架。.NET MAUI 有 Essentials 包，而 Uno Platform 是继 UWP 之后的整个应用开发平台。.NET MAUI 和 Uno Platform 都可以被认为不仅仅是一个 UI 框架。这意味着诸如持久性设置、文件处理、认证、本地化和设备权限等东西在 MAUI 或 Uno Platform 中可以立即使用，但在 Avalonia 中却不能。Uno Platform 甚至拥有 UWP 中才有的先进的音频相关 API，可以跨平台使用。
<br/><br/>
然而，Uno Platform 试图覆盖整个 UWP API 体系，这是很庞大的。整个 API 是自动生成的，很多功能都是未实现的空函数。这意味着大多数非用户接口的 API 是不可用的，如果在应用程序中使用它们，会出现异常。这确实在开发过程中产生了一些问题，但编译会显示哪些未实现的 API 正在被使用。即便如此，Uno Platform 仍然比其他框架拥有更多的非 UI 功能。
  </dd>

  <dt>性能</dt>
  <dd>

XAML 来自于桌面，因此资源是相当密集的。WPF（最初的 XAML 框架）通常在运行时从 XAML 标记中构建整个视图，这在第一次加载时可能是一个严重的性能打击。此外，使用 MVVM 模式将控件绑定到视图模型上，这使用了反射绑定，与编译的代码相比，反射本身就很慢。基础 XAML 控件传统上有更高的性能和系统要求，这可能是移动或云平台的一个问题。
<br/><br/>
UWP，也就是 Uno Platform，通过 x:Load 允许懒惰加载来改进这一点。它们也都支持使用 x:Bind 的编译绑定。MAUI 的架构通过使用本地控件完全避开了第一个问题。Avalonia UI 已经在很大程度上转向了预编译的 XAML 和编译的绑定，这也解决了这两个问题。这三个平台都有比 WPF 更好的理论性能。
<br/><br/>
与性能有关的 MVU 模式不应该被忽视。用户界面不是由 XAML 标记构建的——它是在代码中与逻辑和通常是代码后置的东西一起构建的。默认情况下，这意味着控件和用户界面元素只有在它们被代码引用并需要显示时才被构建。这样一来，使用 MVU 模式的性能有望超过 MVVM 模式应用的性能。MAUI 和 Uno Platform 都支持 MVU 模式。Avalonia 也支持完全在代码中创建 UI，没有 XAML，这也实现了同样的性能优势。
<br/><br/>
.NET MAUI 的性能被评为两颗星，低于 Avalonia 的三颗星，这有点不符合常理。尽管 MAUI 使用了本地控件，但其原因是互操作。这在很大程度上被本地编译所缓解，但任何 C# 与 Android 控件的整合都会带来性能上的损失。然而，Avalonia 完全渲染自己，不与安卓的本地控件元素互动（除非托管本地控件）。这意味着 Avalonia 本质上可以拥有视频游戏的性能。
<br/><br/>
Uno Platform 的性能在大多数平台上一般都是足够的。然而，在 Android 上，.NET 运行时和 Java 运行时之间存在严重的互操作性能问题。这是 .NET Android 本身的问题。然而，由于 Uno Platform 的架构（与本地控件集成），这种互操作总是需要的。这意味着，在安卓上，Uno Platform 的性能从根本上不如其他框架，安卓上的高性能 Uno Platform 应用目前还无法实现。
  </dd>

  <dt>APP 稳定性</dt>
  <dd>

MAUI 的移动应用稳定性与 Uno Platform 排名相同；但是，遇到每个平台的布局 bug 是很常见的，需要大量的特殊情况下的代码和标记。Uno Platform 也有一些未处理的案例和一些在整个开发过程中会出现的 bug。这主要是由于快速开发速度优先于正确性和完整性的策略造成的。相比之下，Avalonia UI 的开发从一开始就考虑到了稳定性：它所具有的功能是完全可以实现的。在实践中，Avalonia UI 可能是最稳定和最容易开发的。
  </dd>

  <dt>代码许可</dt>
  <dd>

Uno Platform 不是 MIT 许可，是 Apache 2.0。Apache 许可证不像 MIT 那样宽松，除此之外，它也阻止了代码共享回到其他 MIT 许可的框架中。Uno Platform 可以使用 MIT 许可项目的源代码，如 WinUI、WPF 和 Avalonia，但这些项目基本上不能使用 Uno Platform 的代码。这就是为什么 Uno Platform 在这里排名较低。

Avalonia UI 完全采用 MIT 许可，可以在大多数 .NET 基础和 WinUI 项目之间自由共享代码。Avalonia UI 是那些需要完全控制其 UI 框架的公司的理想选择，这些公司可以比上游更快地推送修复程序，确保应用程序的兼容性，甚至更换自定义的内部结构。
  </dd>

  <dt>反馈与支持</dt>
  <dd>

Avalonia 和 Uno Platform 在付费支持方面都比 MAUI 排名高，尽管 MAUI 是由微软开发的。这主要是由于小公司的敏捷性。微软现在高度官僚化，任何反馈或变化，即使是微小的，也需要广泛的讨论才能有动作。这与 Avalonia 和 Uno Platform 形成鲜明对比，Avalonia 可以非常迅速地采用新功能，而 Uno Platform 则有极快的沟通。在免费支持方面，Uno Platform 有很好的社区响应时间，与较大的 MAUI 社区相当。然而，Uno Platform 一般能更快地解决 bug 和实现功能。
  </dd>

  <dt>源代码的可读性与贡献的难易</dt>
  <dd>

Avalonia UI 拥有最简洁的代码库，大大降低了公众贡献的门槛。Uno Platform 和 .NET MAUI 要复杂得多，代码也显示了这一点。从长远来看，复杂性的增加通常会在维护和稳定性方面造成障碍。在 Uno Platform 的情况下，这种复杂性对于满足架构目标和支持本地控制集成是必要的。
  </dd>

  <dt>开发体验</dt>
  <dd>

Avalonia UI 拥有最好的整体开发者体验。代码库易于阅读，使用 Rider 的 IDE 和调试体验是一流的（在其他 IDE 上较差）。.NET MAUI 是非常接近的第二名，因为它现在与 Visual Studio 的第一方集成超过了所有其他的。然而，由于需要在每个平台上分别验证/调整每个功能/视图，.NET MAUI 在整体开发者体验方面有所欠缺。Uno Platform 的开发者体验很差，在 Visual Studio 中的集成度很低，编译时间非常长，而且调试困难。关于开发者体验的更多细节可在 IDE 整合部分找到。
  </dd>

  <dt>背后公司</dt>
  <dd>

乍一看，.NET MAUI 似乎有最强大的企业支持，因为它是由微软开发的。然而，微软并没有在该项目上投入大量的资源，而且微软放弃 UI 框架的长期历史也造成了不确定性。
<br/><br/>
Avalonia，虽然最初是完全开源的，但现在是由一些核心团队成员成立的公司支持的。这提供了一个很好的稳定性和收入来维持这个项目。然而，由于公司的影响力越来越大和代码库的闭源进展，这里需要谨慎对待。例如，组成渲染引擎现在不是自由许可的修改（而其余的代码是 MIT 许可的）。随着 v11 发布，这种情况应该会改变。
<br/><br/>
然而，由于有 *nventive* 的企业赞助，以及令人难以置信的沟通和响应时间，Uno Platform 仍然处于一个独立的级别。他们与微软的合作关系和密切沟通也值得注意。
  </dd>

  <dt>Visual Studio 整合</dt>
  <dd>

没有一个框架在 Visual Studio 集成方面有三颗星。这是因为 Visual Studio 在历史上专注于 Windows 优先的框架，如 WinForms、WPF、UWP 和 WinUI，并以非扩展的方式对这些框架进行硬编码支持。然而，.NET MAUI 的支持正在得到相当大的改善（从推出时几乎无法使用）。Uno Platform 的 Visual Studio 集成还有很多需要改进的地方，显然是三者中最差的，这也是导致开发者体验不佳的原因。这不是他们的错，因为微软并没有合理地支持任何其他使用 .xaml 文件的项目类型。Visual Studio 中的 Avalonia 支持提供了坚实的预览器支持，大多数东西都能工作——通过使用特殊的 .axaml 扩展名--但 XAML 的工作并不像在 Rider 等其他 IDE 上那么顺利。
  </dd>

  <dt>Visual Studio Code 整合</dt>
  <dd>

Uno Platform 团队开发了一个 [Visual Studio Code的扩展](https://platform.uno/blog/announcing-net-mobile-debugging-in-vs-code-mobile-development-in-vs-code-with-uno-platform-or-net-maui/)，可以实现移动和网络应用的开发，更重要的是可以进行调试。这是 VS Code 工具的一大进步，因为作为 C#/.NET 应用程序的 IDE，VS Code 工具在历史上对开发者并不友好。令人惊讶的是，该扩展还支持 .NET MAUI 应用程序。Uno Platform 团队在这里真正站了出来，填补了 VS Code 支持方面的一个长期空白，从而使这个 IDE 获得了满分三颗星。Uno Platform 应用程序现在在 Visual Studio Code 中得到了最好的支持（除非在 Windows 上作为 WinUI 开发，否则 Visual Studio 仍然是最好的）。请注意，这个扩展不是开源的。

Avalonia UI [发布了](https://avaloniaui.net/Blog/avalonia-for-visual-studio-code-early-access,e2464208-4482-4dd1-bd60-fd11c98983dc)（截至 2023 年 7 月）[预览版 Visual Studio Code 扩展](https://github.com/AvaloniaUI/Avalonia-VSCode-Extension)，支持 XAML 代码补全以及预览。这使得 Avalonia UI 在 Visual Studio Code 中的可用性大大提高，并应使其成为未来可行的集成开发环境。本节和上述比较表将在该扩展公开发布并经过测试后进行更新。
  </dd>

  <dt>设计工具整合</dt>
  <dd>

现在只有 Uno Platform 支持一个设计工具（Figma）来构建用户界面。这种支持是由一个闭源的 XAML 生成器提供的。在过去，Microsoft Blend 可用于 WPF 以支持同样的作用。生成的 XAML 的质量和效率可能有所欠缺；但是，对于那些在这些团队之间有明确分工的公司来说，它有助于设计者向开发者过渡。
<br/><br/>
.NET MAUI 不支持任何设计工具，而且由于它的结构，可能永远不会支持。然而，它有开箱即用的对 XAML 的实时编辑的支持，这使设计者可以在代码添加之前直接在应用程序中调整和添加一些 UI 元素。Uno Platform 也支持 XAML 的实时编辑。
  </dd>

  <dt>平台支持</dt>
  <dd>

Uno Platform 支持最多的平台，几乎可以在任何设备上运行，并取得不同程度的成功（其最强的领域是移动和网络）。Uno Platform 通过 WinUI/UWP 直接支持 Windows 桌面，所以在 Windows 桌面上获得了原生的最高排名。值得注意的是，在 Uno Platform 中，某些后端和平台缺乏其他平台所具有的功能。这可能导致的问题是，你可以在 iOS/Android 上做一些你在 Linux 上做不到的事情。所以平台支持并不一致，应该仔细审查。这在 macOS 上尤其如此，在上次测试时（2021年），Uno Platform 的运行情况极差。今天，通常使用 macCatalyst 构建 macOS 应用程序会更好，因为 Uno Platform 的 iOS 支持明显更好、更完整。Skia 后端也是所有桌面平台（甚至是旧版本的 Windows）的一个选择。请记住（如*性能*部分所述），与 iOS 相比，Uno Platform 在 Android 上的性能较差。
<br/><br/>
Avalonia UI 在 macOS 和 Linux 桌面平台上远远领先于其他框架。Avalonia 在 Windows 桌面端也有很高的分数，但没有使用原生 UI 工具包，所以得分比 Uno Platform 低一些。移动端和网页端支持是在 11.0 版本中新发布的，可能需要时间来稳定，所以目前得分较低。Avalonia 的网页端实现渲染到一个 HTML5 画布。这永远不会像 Uno Platform 的架构那样好，Uno Platform 将界面整合为 HTML 元素。
<br/><br/>
.NET MAUI 完全不支持 Linux 或网页端。在平台覆盖方面，它显然不如另外两个。
  </dd>
</dl>

## 每个平台下的框架推荐

在每个平台的上，有一些框架的表现是最好的。这也是主观的；但是，总的来说，评估应该是有方向性的，并考虑到所有的因素。

<table>
  <tr>
    <th>平台</th>
    <th colspan="2">最好的框架</th>
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

如果一个应用程序只需要在桌面平台上使用，Avalonia 是一个非常有力的选择。它对 Windows 的支持是一流的，只是因为它不是原生 UI，所以排名低于 WinUI 或 WPF。然而，在一个应用程序中，没有明显的限制，许多桌面应用程序今天已经使用它。事实上，Avalonia 甚至支持在 WPF 中无法做到的事情，如在 DirectX 表面覆盖 XAML 控件。

如果一个应用程序需要跨平台，可以先用 WinUI 或 WPF 编写。使用 Windows 的 WPF 代码库可以很好地转换到 Avalonia，但仍然需要三种不同的 XAML 变体，它也不是最新的技术。出于这个原因，一般来说，最好使用 WinUI，它可以 100% 与 Uno Platform 共享。这意味着只需要两种 XAML 的变体。

还要注意的是：
 * Web/Wasm是 Uno Platform 的一个明显优势。由于架构差异，Avalonia 在这里很难竞争（用 Skia 完全渲染）。
 * Avalonia UI 是最接近 Flutter 的竞争者。它在每个平台上都使用 Skia（或在 Windows 上可选择使用 Direct2D）完全渲染自己。这比 Uno Platform 有很大的性能优势，特别是在 macOS 和 Android 上可见。这样一来，Avalonia 在所有框架中拥有最简洁的架构，而且社区参与的门槛最低。
 * Avalonia UI 被定位为下一代的 WPF，它重新实现了大多数功能。Avalonia 从 WPF（Grid，文本格式化）和 WinUI（ItemsRepeater，触摸输入 API）中获得了一些想法和代码，同时还有其他 XAML 框架中没有的独特想法（在某些方面更接近 CSS 的高级样式系统）。今天，它已经为桌面应用程序开发者准备好了——特别是那些已有 WPF 代码的开发者。对于 UWP/WinUI 开发者来说，这是一个比较粗糙的过渡，但在第11版中加入了更多来自 UWP/WinUI 的最新功能，以改善过渡情况。对于不想改变现有代码的企业 WPF 应用，Avalonia 还提供了Avalonia XPF，它在Avalonia 渲染引擎之上实现了开源的 WPF 代码库。
 * .NET MAUI 并没有被列为任何平台的最佳选择。它对没有复杂 UI 的小型应用程序最有用。它的有用性，以及在平台之间共享代码的能力，对于甚至是中等复杂的应用程序来说，很快就会落后于其他框架。然而，在某些业务线或更简单的应用程序中，MAUI 可能是更好的选择。最近，MAUI 还能够同时托管 Blazor 和 Avalonia UI，这为某些场景提供了一个有趣的选择。
 * Avalonia 最适用于 Windows 10 之前的 Windows 版本。虽然 Uno Platform 也有其 Skia 后台的解决方案，但它在功能、稳定性和完整性方面大大落后。
 * 如上表所示，使用 XAML 的两种变体可以很好地支持所有平台：WinUI/UWP 变体用于 Windows 和 Uno Platform 的手机，Avalonia 变体用于其他平台。

链接与引用

 1. [Question: XAML Flavor, Architecture & Roadmap](https://github.com/dotnet/maui/issues/43)
 1. [The New .NET Multi-platform App UI](https://devblogs.microsoft.com/xamarin/the-new-net-multi-platform-app-ui-maui)
 1. [Goodbye Xamarin.Forms](https://itnext.io/goodbye-xamarin-forms-f41723fb9fe1)
 1. [Putting “Universal” back into UWP](https://medium.com/@Arlodottxt/putting-universal-back-into-uwp-d2e5a8099bc1)
 1. [Evolution of Client Development: Richard Campbell](https://youtu.be/nbqe9uHWT_c?t=232)
 1. [[Spec] Slim Renderer Architecture](https://github.com/dotnet/maui/issues/28)
 1. [Discussion: Compatibility with WPF, UWP and WinUI](https://github.com/AvaloniaUI/Avalonia/discussions/5596)
 1. [Project Reunion: An End to Microsoft’s UI Madness?](https://medium.com/young-coder/project-reunion-an-end-to-microsofts-ui-madness-1af662e36386)

## 结论

我们花了很多年才走到这一步，但我们终于有了一个好地方，有了强大的 UI 框架，涵盖了 .NET 的所有用途。有趣的是，所有的框架都发展到了一个非常独特且功能几乎是互补的状态。可能你想尝试的一切都被其中一个或几个框架所涵盖。今天，我们可以编写跨平台的 XAML/C# 应用程序，而且运行得相当好。大部分技术（除了 UI 层）都是基于 Mono 的，所以这要归功于 Xamarin。

每个框架所取得的成就都很了不起。然而，没有一个框架在所有平台上都占主导地位，每个平台都有自己的优势和劣势。Uno Platform 来自 Android/iOS 的遗产，这些移动平台和 Web 平台是最强大的。Avalonia 来自桌面端遗产，在 Windows/Linux/MacOS 上效果最好，但移动平台正在迅速发展。截至 2023 年，Uno Platform 对 macOS 的支持充其量只是试验性的，对于简单的应用程序来说是无法使用的。Avalonia，截至 2023 年，只对移动端有初步支持，但实际上在所有平台上都更稳定。尽管如此，现在可能需要利用两个不同的 UI 框架来实现基于 XAML 的跨平台 UI。

---

This document is licensed CC BY-SA 4.0. For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
