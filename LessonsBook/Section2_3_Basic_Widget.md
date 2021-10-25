# 3 - Basic Widgets

#### Written by Vincent Ngo

As you know, everything in Flutter is a widget. But how do you know which widget to use when? In this chapter, you’ll explore three categories of basic widgets, which you can use for:

° Structure and navigation

° Displaying information

° Positioning widgets

By the end of this chapter, you’ll use those different types of widgets to build the foundation of an app called *Fooderlich*, a social recipe app. You’ll build out the app’s structure and learn how to create three different recipe cards: the main recipe card, an author card and an explore card.

![img37](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img37.png)

Ready? Dive in by taking a look at the starter project.

# Getting started

Start by downloading this chapter’s project from the book materials repo https://github.com/raywenderlich/flta-materials.

Locate the projects folder and open starter. If your IDE has a banner that reads ‘Pub get’ has not been run, click Get dependencies to resolve the issue.

![img38](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img38.png)

Run the app from Android Studio and you’ll see an app bar and some simple text:

![img39](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img39.png)

*main.dart* is the starting point for any Flutter app. Open it and you’ll see the following:

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
   
3. The `Fooderlich` widget starts by composing a `MaterialApp` widget to give it a *Material Design* system look and feel. See https://material.io for more details about it.

4. The `MaterialApp` widget contains a `Scaffold` widget, which defines the layout and structure of the app. The scaffold has two properties: an `appBar` and a `body`. An `Appbar`’s `title` contains a `Text` widget. The `body` has a `Center` widget, whose `child` property is a `Text` widget.
