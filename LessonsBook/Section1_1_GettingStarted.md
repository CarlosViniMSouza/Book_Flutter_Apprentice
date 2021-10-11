# 1 Getting Started
#### Written by Michael Katz

Congratulations. By opening “The Flutter Apprentice”, you’ve taken your first step toward becoming a Flutter master. This book will be your guide to learning the Flutter UI Toolkit, Google’s platform for building apps for mobile, desktop and web from a single codebase.

The five sections of this book will progressively teach you how to create an app using Flutter. You’ll learn all about widgets, which are components that you compose to build your apps. You’ll also learn about navigation and transitions, handling state and network management. Finally, you’ll learn how to deploy the app to testers and users.

This book assumes you’re familiar with development for a native mobile platform, such as iOS with Swift or Android with Kotlin… but you don’t need to be an expert by any means. These chapters will show you how to build a Flutter app from scratch, so if you’re completely new, you’ll catch up just fine.

![img1](E:\RepositoriosFlutter\flutter-apprentice\LessonsBook\Images\img1.png)

# What is Flutter?

In the simplest terms, Flutter is a software development toolkit from Google for building cross-platform apps. Flutter apps consist of a series of packages, plugins and widgets — but that’s not all. Flutter is a process, a philosophy and a community as well.

It’s also the easiest way to get an app up and running on any one platform, let alone multiple. You can be more productive than you thought possible thanks to Flutter’s declarative, widget-based UI structure, first-class support for reactive programming, cross platform abstractions and its virtual machine that allows for hot reloading of code changes.

![img1.5](E:\RepositoriosFlutter\flutter-apprentice\LessonsBook\Images\img1_2.png)

One thing Flutter is not is a language. Flutter uses Dart as its programming language. If you know Kotlin, Swift, Java or Typescript, you’ll find Dart familiar, since it’s an object-oriented C-style language.

You can compile Dart to native code, which makes it fast. It also uses a virtual machine (VM) with a special feature: hot reload. This lets you update your code and see the changes live without redeploying it.

For years, programmers have been promised the ability to write once and run anywhere; Flutter may well be the best attempt yet at achieving that goal.

# Seriously?

Yes, Flutter is that awesome. You can build a high-quality app that’s performant and looks great, very quickly. This book will show you how.

In the first few chapters, you’ll get your feet under you with the basic UI. By the end of the book, you’ll be able to build apps that look great and perform well.

And it truly does work well with both desktop and web.

Other cross-platform toolkits have tried to abstract the underlying OS by adding a layer on top of the native UI layer. This leaves the developer with the lowest common set of features available — not to mention, degraded performance.

In contrast, Flutter’s widgets exist parallel to native widgets due to its custom user interface rendering engine, Skia. That means that the toolkit controls how the UI looks and behaves, which allows for consistent behavior between platforms. From a performance perspective, there’s no penalty from additional layers of abstraction.

# Who’s Flutter for?

![img2](E:\RepositoriosFlutter\flutter-apprentice\LessonsBook\Images\img2.png)

Flutter is for both the new or experienced developer who wants to start a mobile app with minimal overhead. Flutter is for someone looking to make an app that runs on multiple devices, either right away or in the future. It’s for someone who prefers to build declarative UIs with the support of a large, open-source community.

Additionally, Flutter is for developers with experience on one platform who want to develop an app that works across many. This is doubly true if you’re a web developer with deep Javascript or Typescript knowledge, but haven’t gotten started on mobile yet. You can learn both major mobile platforms at once!

If you don’t have an existing app, Flutter is a great way to develop something quickly to validate an idea or to build a full, multi-platform production app.

On the other hand, if you already have a great app on one platform with the native toolkits, then you should evaluate your ongoing maintenance costs to see if it makes sense to build out for the other platforms by using Flutter or the native toolkits.

# Great things about Flutter

Here’s just a sample of some great things about using Flutter:

° Flutter is open-source. That means you can watch its evolution and know what’s coming — and even try out new features in development. You can also create your own patches and packages or contribute code. And you can be involved in the community to help others or contribute to its future direction.

° Flutter uses the Dart programming language. Dart (https://dart.dev) is a modern, UI-focused language that’s compiled to native ARM or x86 code or cross-compiled to Javascript. It supports all the great language features people have come to like and expect, such as `async/await` for concurrency management and type inference for clean, type-safe code.

° One of the best features of Flutter is hot reload. Hot reload allows you to make updates to the code and the UI that rebuild the widget tree, then deliver them live to emulators and devices — without having to reload state or recompile your app.

° Sometimes, you make changes that affect too much of the widget tree or app state to hot reload easily. In those cases, you can use hot restart. Hot restart takes a little longer than hot reload because it loads the changes, restarts the app and resets the state, but it’s still faster than a full restart, which recompiles and redeploys. You need to use a full restart when you make certain significant changes to the code, including anything changing state management.

° These restart features leverage Dart’s VM to inject the updated code, so they’re only available in debug mode and not in a production app.

° Other cross-platform toolkits produce apps with a stock look and feel — boring! Flutter is purposely attractive, using Google’s **Material Design** out of the box. It’s also easy to apply Cupertino widgets to get an iOS-like appearance. The UI is fully customizable, allowing you to make an app that looks right for your brand.

° Flutter comes with great animations and transitions, and you can build custom widgets as well. Because widgets are **composable**, you can be creative and flexible with the UI. For example, you can put videos behind a scroll view or put a toolbar on top of a canvas.

° The sheer number of widgets and the declarative syntax for building UIs lets you be extremely productive, building a rich app quickly with minimal overhead and boilerplate. Stateful widgets are bound to data and automatically update as the data model changes.

° If you’ve used SwiftUI or Jetpack Compose recently, you’re already familiar with many of Flutter’s concepts. But Flutter is even better — it has fewer limitations on the tools and you can build for multiple platforms at once.

° Flutter was designed with **accessibility** in mind, with out-of-the-box support for dynamic font sizes and screen readers and a ton of best practices around language, contrast and interaction methods.

° Platform integration is important for accessing libraries written in other languages or using platform-specific features that don’t have a Flutter support package yet. Flutter supports C and C++ interoperability as well as **platform channels** for connecting to Kotlin and Java on Android and Swift or Objective-C on iOS.

# Are you convinced yet?

If you’re not yet convinced that there’s a place for Flutter, check out the showcase: https://flutter.dev/showcase.

There, you see the top companies using Flutter and how diverse the apps you can make with it are. These aren’t limited to “JSON-in-a-table” apps, but also include media-rich dynamic and interactive apps.

These apps help you be more productive, better informed, communicate more easily and have more fun. Flutter’s native performance and system integrations make it a better choice than a web or hybrid app for most mobile applications.

Popular apps from some of the world’s biggest companies are built with Flutter. These include:

    -> Very Good Ventures
    -> Tencent
    -> Realtor.com
    -> Google Assistant
    -> New York Times
    -> Policygenius
    -> Google Stadia
    -> Take a look at some recent examples:

![img3](E:\RepositoriosFlutter\flutter-apprentice\LessonsBook\Images\img3.png)

# When not to use Flutter

Flutter isn’t the best tool for every application. Here are some areas where Flutter is an evolving platform.

### Games and audio

While you can create simple 2D games using Flutter, for complex 2D and 3D games, you’d probably prefer to base your app on a cross-platform game engine technology like Unity or Unreal. They have more domain-specific features like physics, sprite and asset management, game state management, multiplayer support and so on.

Flutter doesn’t have a sophisticated audio engine yet, so audio editing or mixing apps are at a disadvantage over those that are purpose-built for a specific platform.

### Apps with specific native SDK needs

Flutter supports many, but not all, native features. Fortunately, you can usually create bridges to platform-specific code. However, if the app is highly integrated with a device’s features and platform SDKs, it might be worth writing the app using the platform-specific tools. Flutter also produces app binaries that are bigger in size than those built with platform frameworks.

Flutter might not be a practical choice if you are only interested in a single platform app and you have deep knowledge of that platform’s tools and languages. For example, if you’re working with a highly-customized iOS app based on CloudKit that uses all the native hardware, MLKit, StoreKit, extensions and so on, maintaining and taking advantage of those features will be easier using SwiftUI. Of course, the same goes for a heavily-biased Android app using Jetpack Compose.

### Certain platforms

Flutter doesn’t run everywhere. It doesn’t support Apple Bitcode yet, which means that it doesn’t support watchOS, tvOS or certain iOS app extensions. Its support for the web is still in its early days, which means that Flutter has many features and performance improvements ahead of it — but they’re coming.

Since Flutter doesn’t run on watches or TVs yet, you’ll have to build those components natively and attach them to a Flutter-based mobile app. Depending on how sophisticated those other apps are, it might not be worth the hassle to write both native and Flutter code.

# Flutter’s history

Flutter comes from a tradition of trying to improve web performance. It’s built on top of several open-source technologies developed at Google to bring native performance and modern programming to the web through Chrome.

The Flutter team chose the Dart language, which Google also developed, for its productivity enhancements. Its object-oriented type system and support for reactive and asynchronous programming give it clear advantages over Javascript. Most importantly, Google built the Dart VM into the Chrome browser, allowing web apps written in Dart to run at native speeds.

Another piece of the puzzle is the inclusion of Skia as the graphics rendering layer. Skia is another Google-based open source project that powers the graphics on Android, Chrome browsers, Chrome OS and Firefox. It runs directly on the GPU using Vulcan on Android and Metal on iOS, making the graphics layer fast on mobile devices. Its API allows Flutter widgets to render quickly and consistently, regardless of the host platform.

# The Flutter architecture

Flutter has a modular, layered architecture. This allows you to write your application logic once and have consistent behavior across platforms, even though the underlying engine code differs depending on the platform. The layered architecture also exposes different points for customization and overriding, as necessary.

![img4](E:\RepositoriosFlutter\flutter-apprentice\LessonsBook\Images\img4.png)

The Flutter architecture consists of three main layers:

1 - The Framework layer is written in Dart and contains the high-level libraries that you’ll use directly to build apps. This includes the UI theme, widgets, layout and animations, gestures and foundational building blocks. Alongside the main Flutter framework are plugins: high-level features like JSON serialization, geolocation, camera access, in-app payments and so on. This plugin-based architecture lets you include only the features your app needs.

2 - The Engine layer contains the core C++ libraries that make up the primitives that support Flutter apps. The engine implements the low-level primitives of the Flutter API, such as I/O, graphics, text layout, accessibility, the plugin architecture and the Dart runtime. The engine is also responsible for rasterizing Flutter scenes for fast rendering onscreen.

3 - The Embedder is different for each target platform and handles packaging the code as a stand-alone app or embedded module.

Each of the architecture layers is made up of other sublayers and modules, making them almost fractal. Of particular import to general app development is the makeup of the framework layer:

![img5](E:\RepositoriosFlutter\flutter-apprentice\LessonsBook\Images\img5.png)

The Flutter framework consists of several sublayers:

° At the top is the UI theme, which uses either the Material (Android) or Cupertino (iOS) design language. This affects how the controls appear, allowing you to make your app look just like a native one.

° The widget layer is where you’ll spend the bulk of your UI programming time. This is where you compose design and interactive elements to make up the app.

° Beneath the widgets layer is the rendering layer, which is the abstraction for building a layout.

° The foundation layer provides basic building blocks, like animations and gestures, that build up the higher layers.

# What’s ahead

This book is divided into five sections:

° Section 1 is the introduction. You’re here! In this section, you’ll get an overview of Flutter, learn how to get started and make sure you have everything set up to develop great apps. You’ll build a simple app to get a taste of the Dart language and Flutter SDKs.

° Section 2 is all about widgets, the building blocks you use to make your app.

° Section 3 covers navigation and deep links. If you think about widgets as making up screens, navigation ties them together to let the user accomplish various tasks within the app.

° Section 4 goes over state and data. You’ll learn how to save data and work with local persistence and networking.

° Section 5 shows you how to make the app work with native platforms as well as how to deploy your app.

° By the end of the book, you’ll be able to take an idea, turn it into a great-looking multi-platform app and submit it for publication.

# Getting started
Now that you’ve decided Flutter is right for you, your next step is to get the tools necessary to build Flutter apps: the Flutter SDK and Dart compiler. You’ll also need an IDE with a Flutter plugin along with the tools to build and deploy for the various platforms. The latter means Xcode for iOS and Android Studio for Android.

To start, visit https://flutter.dev/. This portal is the source of truth for any installation instructions or API changes that occur between this book’s publication and the time you read it. If there are any contradictions, the information at **flutter.dev** supersedes.

# What you need

1 - A computer. You can develop Flutter apps on Windows, macOS, Linux or ChromeOS. However, Xcode only runs on macOS, making a Mac necessary to build and deploy apps for iOS.

`Note: Because of the Xcode limitation for macOS, this book uses the Flutter toolchain on Mac. You can follow along on any platform of your choice — just skip any iOS- or Mac-specific steps.`

2 - The Flutter SDK.

3 - An editor, such as Android Studio or Visual Studio Code.

4 - At least one device. You can run in an iOS Simulator or Android emulator, but running Flutter apps on a physical device will give you the true user experience.

5 - Developer accounts (optional). To deploy to the Apple App Store or Google Play Store, you’ll need a valid account on each.

