# 3 - Basic Widgets

#### Written by Vincent Ngo

As you know, everything in Flutter is a widget. But how do you know which widget to use when? In this chapter, you’ll explore three categories of basic widgets, which you can use for:

° Structure and navigation

° Displaying information

° Positioning widgets

By the end of this chapter, you’ll use those different types of widgets to build the foundation of an app called _Fooderlich_, a social recipe app. You’ll build out the app’s structure and learn how to create three different recipe cards: the main recipe card, an author card and an explore card.

![img37](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img37.png)

Ready? Dive in by taking a look at the starter project.

# Getting started

Start by downloading this chapter’s project from the book materials repo https://github.com/raywenderlich/flta-materials.

Locate the projects folder and open starter. If your IDE has a banner that reads ‘Pub get’ has not been run, click Get dependencies to resolve the issue.

![img38](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img38.png)

Run the app from Android Studio and you’ll see an app bar and some simple text:

![img39](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img39.png)

_main.dart_ is the starting point for any Flutter app. Open it and you’ll see the following:

```dart
import 'package:flutter/material.dart';

void main() {
  // 1
  runApp(const Fooderlich());
}

class Fooderlich extends StatelessWidget {
  // 2
  const Fooderlich({Key? key}) : super(key: key);
  @override
  Widget build(BuildContext context) {
    // TODO: Create theme
    // TODO: Apply Home widget
    // 3
    return MaterialApp(
      // TODO: Add theme
      title: 'Fooderlich',
      // 4
      home: Scaffold(
        // TODO: Style the title
        appBar: AppBar(title: const Text('Fooderlich')),
        // TODO: Style the body text
        body: const Center(child: Text('Let\'s get cooking 👩‍🍳')),
      ),
    );
  }
}
```

Take a moment to explore what the code does:

1. Everything in Flutter starts with a widget. `runApp()` takes in the root widget `Fooderlich`.
2. Every stateless widget must override the `build()` method.
3. The `Fooderlich` widget starts by composing a `MaterialApp` widget to give it a _Material Design_ system look and feel. See https://material.io for more details about it.

4. The `MaterialApp` widget contains a `Scaffold` widget, which defines the layout and structure of the app. The scaffold has two properties: an `appBar` and a `body`. An `Appbar`’s `title` contains a `Text` widget. The `body` has a `Center` widget, whose `child` property is a `Text` widget.

# Styling your app

Since Flutter is cross-platform, it’s only natural for Google’s UI Toolkit to support the visual design systems of both Android and iOS.

![img40](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img40.png)

Android uses the _Material Design_ system, which you’d import like this:

```dart
import 'package:flutter/material.dart';
```

iOS uses the _Cupertino_ system. Here’s how you’d import it:

```dart
import 'package:flutter/cupertino.dart';
```

To keep things simple, a rule of thumb is to pick only one design system for your UI. Imagine having to create _if-else_ statements just to manage the two designs, let alone support different transitions and OS version compatibility.

Throughout this book, you’ll learn to use the _Material Design_ system. You’ll find the look and feel of Material Design is quite customizable!

```
NOTE: Switching between Material and Cupertino is beyond the scope of this book. For more information about what these packages offer in terms of UI components, check out:

  ° Material UI Components: https://flutter.dev/docs/development/ui/widgets/material
  ° Cupertino UI Components: https://flutter.dev/docs/development/ui/widgets/cupertino
```

Now that you have settled on a design, you’ll set a theme for your app in the next section.

# Setting a theme

You might notice the current app looks a little boring with the default blue, so you’ll spice it up with a custom theme! Your first step is to select the font for your app to use.

# Using Google fonts

The `google_fonts` package supports over 900 fonts to help you style your text. It’s already included _pubspec.yaml_ and you have already added it to the app when clicking _Pub Get_ before. You’ll use this package to apply a custom font to your theme class.

# Defining a theme class

To share colors and font styles throughout your app, you’ll provide a `ThemeData` object to `MaterialApp`. In the _lib_ directory, open _fooderlich_theme.dart_, which contains a predefined theme for your app.

Take a look at the code:

```dart
import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';

class FooderlichTheme {
  // 1
  static TextTheme lightTextTheme = TextTheme(
    bodyText1: GoogleFonts.openSans(
      fontSize: 14.0,
      fontWeight: FontWeight.w700,
      color: Colors.black,
    ),
    headline1: GoogleFonts.openSans(
      fontSize: 32.0,
      fontWeight: FontWeight.bold,
      color: Colors.black,
    ),
    headline2: GoogleFonts.openSans(
      fontSize: 21.0,
      fontWeight: FontWeight.w700,
      color: Colors.black,
    ),
    headline3: GoogleFonts.openSans(
      fontSize: 16.0,
      fontWeight: FontWeight.w600,
      color: Colors.black,
    ),
    headline6: GoogleFonts.openSans(
      fontSize: 20.0,
      fontWeight: FontWeight.w600,
      color: Colors.black,
    ),
  );

  // 2
  static TextTheme darkTextTheme = TextTheme(
    bodyText1: GoogleFonts.openSans(
      fontSize: 14.0,
      fontWeight: FontWeight.w700,
      color: Colors.white,
    ),
    headline1: GoogleFonts.openSans(
      fontSize: 32.0,
      fontWeight: FontWeight.bold,
      color: Colors.white,
    ),
    headline2: GoogleFonts.openSans(
      fontSize: 21.0,
      fontWeight: FontWeight.w700,
      color: Colors.white,
    ),
    headline3: GoogleFonts.openSans(
      fontSize: 16.0,
      fontWeight: FontWeight.w600,
      color: Colors.white,
    ),
    headline6: GoogleFonts.openSans(
      fontSize: 20.0,
      fontWeight: FontWeight.w600,
      color: Colors.white,
    ),
  );

  // 3
  static ThemeData light() {
    return ThemeData(
      brightness: Brightness.light,
      checkboxTheme: CheckboxThemeData(
        fillColor: MaterialStateColor.resolveWith(
          (states) {
            return Colors.black;
          },
        ),
      ),
      appBarTheme: const AppBarTheme(
        foregroundColor: Colors.black,
        backgroundColor: Colors.white,
      ),
      floatingActionButtonTheme: const FloatingActionButtonThemeData(
        foregroundColor: Colors.white,
        backgroundColor: Colors.black,
      ),
      bottomNavigationBarTheme: const BottomNavigationBarThemeData(
        selectedItemColor: Colors.green,
      ),
      textTheme: lightTextTheme,
    );
  }

  // 4
  static ThemeData dark() {
    return ThemeData(
      brightness: Brightness.dark,
      appBarTheme: AppBarTheme(
        foregroundColor: Colors.white,
        backgroundColor: Colors.grey[900],
      ),
      floatingActionButtonTheme: const FloatingActionButtonThemeData(
        foregroundColor: Colors.white,
        backgroundColor: Colors.green,
      ),
      bottomNavigationBarTheme: const BottomNavigationBarThemeData(
        selectedItemColor: Colors.green,
      ),
      textTheme: darkTextTheme,
    );
  }
}
```

This code does the following:

1. Declares a `TextTheme` called `lightTextTheme`, which uses the Google font _Open Sans_ and has a predefined font size and weight. Most importantly, the color of the text is black.

2. Then it defines `darkTextTheme`. In this case, the text is white.

3. Next, it defines a static method, `light`, which returns the color tones for a light theme using the `lightTextTheme` you created in step 1.

4. Finally, it declares a static method, `dark`, which returns the color tones for a dark theme using the `darkTextTheme` you created in step 2.

Your next step is to utilize the theme.

# Using the theme

In _main.dart_, import your theme by adding the following beneath the existing import statement:

```dart
import 'fooderlich_theme.dart';
```

Then replace the comment `//TODO: Create theme` with the following:

```dart
final theme = FooderlichTheme.dark();
```

To apply the new theme replace the comment `// TODO: Add theme` with the following:

```dart
theme: theme,
```

Next replace the comment `// TODO: Style the title` and the line below it with the following:

```dart
appBar: AppBar(
          title: Text(
            'Fooderlich',
            style: theme.textTheme.headline6,
          ),
        ),
```

Finally, locate the comment `// TODO: Style the body text` and replace it and the code below it with the following:

```dart
body: Center(
  child: Text('Let\'s get cooking 👩‍🍳',
      style: theme.textTheme.headline1),
),
```

After all your updates, your code should look like this:

```dart
// 1
import 'fooderlich_theme.dart';

void main() {
  runApp(const Fooderlich());
}

class Fooderlich extends StatelessWidget {
  const Fooderlich({Key? key}) : super(key: key);
  @override
  Widget build(BuildContext context) {
    // 2
    final theme = FooderlichTheme.dark();
    // TODO: Apply Home widget
    return MaterialApp(
      // 3
      theme: theme,
      title: 'Fooderlich',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Fooderlich',
                      // 4
                      style: theme.textTheme.headline6,
                     ),
        ),
        body: Center(
          child: Text('Let\'s get cooking 👩‍🍳',
                      // 5
                      style: theme.textTheme.headline1,
                     ),
        ),
      ),
    );
  }
}
```

To recap, your updates:

1. Imported the `FooderlichTheme`.

2. Defined a variable that holds the theme.

3. Added the `MaterialApp` widget’s `theme` property.

4. Added `AppBar` text styling.

5. Finally, added `body` text styling.

Save your changes. Thanks to hot reload, you’ll see the updated theme nearly immediately.

![img41](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img41.png)

To see the difference between light and dark mode, change the theme between `FooderlichTheme.dark()` and `FooderlichTheme.light`(). The two themes look like this:

```
NOTE: It’s generally a good idea to establish a common theme object for your app — especially when you work with designers. That gives you a single source of truth to access your theme across all your widgets.
```

Next, you’ll learn about an important aspect of building an app — understanding which app structure to use.

# App structure and navigation

Establishing your app’s structure from the beginning is important for the user experience. Applying the right navigation structure makes it easy for your users to navigate the information in your app.

Fooderlich uses the `Scaffold` widget for its starting app structure. `Scaffold` is one of the most commonly-used Material widgets in Flutter. Next, you’ll learn how to implement it in your app.

# Using Scaffold

The Scaffold widget implements all your basic visual layout structure needs. It’s composed of the following parts:

° AppBar
° BottomSheet
° BottomNavigationBar
° Drawer
° FloatingActionButton
° SnackBar

`Scaffold` has a lot of functionality out of the box!

The following diagram represents some of the aforementioned items as well as showing left and right nav options:

![img42](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img42.png)

For more information, check out Flutter’s documentation on *Material Components widgets*, including app structure and navigation: https://flutter.dev/docs/development/ui/widgets/material

Now, it’s time to add more functionality.