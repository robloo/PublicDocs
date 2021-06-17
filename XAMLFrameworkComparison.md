Last Updated 17 June 2021 | License CC BY-SA 4.0

# XAML Framework Comparison

XAML-based UI frameworks have evolved considerably over the years. This is best illustrated in the below graphic. The bulk of these frameworks: Avalonia UI, the Uno Platform and MAUI support cross-platform applications. In fact, except for Avalonia UI, the need for cross-platform XAML is the main driving force behind their development. If Microsoft stepped in earlier and created a true Flutter-like cross-platform UI framework years ago we likely never would have ended up with all of these options. This is both good and bad: Good that we now have lots of options to choose from and bad that all have a different dialect of XAML and object model.

This document aims to help companies and developers answer the question:

 > Which XAML framework should I use for my cross-platform app?

<p align="center">
<img src="https://github.com/robloo/PublicDocs/blob/master/XAMLFrameworkEvolution.png?raw=true" width="800px">
</p>

At a very high level the difference in the three cross-platform XAML frameworks can be described in terms of architecture:

 * **Avalonia UI** : Fully renders controls and user-interface elements itself. This is the same approach that Flutter uses.
 * **Maui** : Standardizes a set of properties and applies them to platform-specific native controls. Mapping to native controls is a least-common-denominator approach. If a single platform doesn't support a feature it likely won't be in MAUI for all platforms (without dropping into platform-specific code).
 * **Uno Platform** : Uses a select few platform-specific primitives to build and render controls. For high level controls this gives nearly pixel-perfect results. This means the Uno Platform behaves like Avalonia UI or Flutter which fully render their controls; however, it also supports direct embedding of platform-specific native controls. It is a hybrid architecture.

## Comparison Table

Each framework performs a differently-signifiantly in some places. The below table highlights these differences focusing on high-impact areas or features. Where all platforms behave the same, an entry is commonly excluded (focuses on only the differences).

 * ✔️ means the feature is supported, ❌ means it is not
 * ⭐⭐⭐ is the highest/best rating, ⭐ is the lowest/worst

|                            | Avalonia | MAUI     | Uno      |
|----------------------------|----------|----------|----------|
| MVVM Pattern               | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   | ✔️｜⭐⭐⭐ |
| MVU Pattern                | ❌          | ✔️｜⭐      | ❌          |
| Pixel-perfect rendering    | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐⭐ |
| Lookless controls          | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐⭐⭐ |
| Styling and Themes         | ✔️｜⭐⭐⭐ | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| Native control integration | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐⭐ |
| XAML Sharing               | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| C# Code-behind Sharing     | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| Hot-reloading              | ❌          | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| 3rd Party Support          | ✔️｜⭐      | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐   |
| **Strategy & Development** |
| Performance (theoretical)  | ⭐⭐⭐ | ⭐⭐   | ⭐⭐   |
| Mobile app stability       | -       | ⭐⭐⭐ | ⭐⭐   |
| Desktop app stability      | ⭐⭐⭐ | ⭐⭐   | ⭐      |
| Available Controls         | ⭐      | ⭐⭐   | ⭐⭐⭐ |
| Code License               | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐   |
| Free support               | ⭐      | ⭐⭐   | ⭐⭐⭐ |
| Paid support               | ⭐⭐⭐ | ⭐⭐   | ⭐⭐⭐ |
| Project speed              | ⭐      | ⭐⭐   | ⭐⭐⭐ |
| **Platform Support** |
| iOS/Android Mobile         | ❌          | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐⭐ |
| Windows Desktop            | ✔️｜⭐⭐   | ✔️｜⭐      | ✔️｜⭐⭐⭐ |
| macOS Desktop              | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐       |
| Linux Desktop              | ✔️｜⭐⭐⭐ | ❌          | ✔️｜⭐      |
| Web Browser (WASM)         | ❌          | ❌          | ✔️｜⭐⭐⭐ |
| **Overall Platform Support** |
| Mobile                     | ❌          | ✔️｜⭐⭐⭐ | ✔️｜⭐⭐⭐ |
| Desktop                    | ✔️｜⭐⭐⭐ | ✔️｜⭐     | ✔️｜⭐       |
| Web                        | ❌          | ❌          | ✔️｜⭐⭐⭐ |

Note the following:
 * The comparison is based on a lot of research and experience with the various frameworks; however, it is subjective in some areas. Also note that experience with Maui is least of the three which may bias rankings.
 * XAML/C# sharing for Uno Platform is compared with WinUI/UWP which is 100% compatible. XAML/C# sharing for Avalonia is primarily compared with WPF.
 * Stability of Maui is ranked lower than the Uno Platform due to the fundamental architecture. It is very common to encounter per-platform layout bugs that require a lot of special-case code and markup.
 * Avalonia mobile platform support is experimental therefore is currently excluded
 * The Uno Platform supports Windows desktop directly through WinUI/UWP so receives the highest ranking as it is native. Avalonia has very high marks as well but isn't using the native UI toolkit so is scored a bit lower.

## Per-Platform Framework Recommendation

On a per-platform basis there are frameworks that perform the best. This is also subjective; however, overall the assessment should be directionally correct and factors in all considerations.

| Platform | Best Framework |
|----------|----------------|
| Windows  | WinUI or WPF   |
| macOS    | Avalonia       |
| Linux    | Avalonia       |
| Android  | Uno Platform   |
| iOS      | Uno Platform   |
| Web/Wasm | Uno Platform   |

Note that:
 * Web/Wasm is a clear advantage of the Uno Platform. Avalonia can likely never compete here due to architecture differences (fully rendered with Skia).
 * Avalonia UI is the closest competition to Flutter. It fully renders itself on each platform using Skia. This has major performance benefits over the Uno Platform especially visible on macOS. In this way, Avalonia has the cleanest architecture of all frameworks and perhaps the brightest future.
 * Maui is not listed as best for any platform intentionally. Maui is most useful for small applications without complex UIs. Its usefulness - and ability to share code between platforms - quickly falls behind other frameworks for even moderate app complexity. However, there are certain line-of-business or simpler apps where Maui may be the better choice.
 * Avalonia is best for versions of Windows before Windows 10. While the Uno Platform also has a solution with its Skia backend, it falls behind considerably in features, stability and completeness.
 * As the table above shows, all platforms can be supported very well using two dialects of XAML: the WinUI dialect (formerly UWP) (for Windows and mobile with Uno Platform) and the Avalonia dialect for others. A technique for managing two versions of XAML in the same project and source code will be shared in a future article.

---

This document is licensed CC BY-SA 4.0. For full text see: https://creativecommons.org/licenses/by-sa/4.0/legalcode
