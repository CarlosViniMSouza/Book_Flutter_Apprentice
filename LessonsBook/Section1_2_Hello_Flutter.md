# Hello, Flutter

#### Written by Michael Katz

Now that you’ve had a short introduction, you’re ready to start your Flutter apprenticeship. Your first task is to build a basic app from scratch, giving you the chance to get the hang of the tools and the basic Flutter app structure. You’ll customize the app and find out how to use a few popular widgets like `ListView` and `Slider` to update its UI in response to changes.

Creating a simple app will let you see just how quick and easy it is to build cross-platform apps with Flutter — and it will give you a quick win.

By the end of the chapter, you’ll have built a lightweight recipe app. Since you’re just starting to learn Flutter, your app will offer a hard-coded list of recipes and let you use a `Slider` to recalculate quantities based on the number of servings.

Here’s what your finished app will look like:

![img17](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img17.png)

All you need to start this chapter is to have Flutter set up. If the `flutter doctor` results show no errors, you’re ready to get started. Otherwise, go back to Chapter 1, “Getting Started”, to set up your environment.

# Creating a new app

There are two simple ways to start a new Flutter app. In the last chapter, you created a new app project through the IDE. Alternatively, you can create an app with the `flutter` command. You’ll use the second option here.

Open a terminal window, then navigate to the location where you want to create a new folder for the project. For example, you can use this book’s materials and go to **flta-materials/02-hello-flutter/projects/starter/**.

Creating a new project is straightforward. In the terminal, run:

```shell
flutter create recipes
```

This command creates a new app in a new folder, both named `recipes`. It has the demo app code, as you saw in the previous chapter, with support for running on iOS and Android.

Using your IDE, open the recipes folder as an existing project.

![img18](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img18.png)

Build and run and you’ll see the same demo app as in Chapter 1, "Getting Started".

![img19](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img19.png)

Tapping the + button increments the counter.

# Making the app yours

The ready-made app is a good place to start because the `flutter create` command puts all the boilerplate together for you to get up and running. But this is not your app. It’s literally **MyApp**, as you can see near the top of **main.dart**:

```dart
class MyApp extends StatelessWidget {
```

This defines a new Dart `class` named `MyApp` which **extends** — or inherits from — `StatelessWidget`. In Flutter, almost everything that makes up the user interface is a **Widget**. A `StatelessWidget` doesn’t change after you build it. You’ll learn a lot more about widgets and state in the next section. For now, just think of `MyApp` as the container for the app.

Since you’re building a recipe app, you don’t want your main `class` to be named `MyApp` — you want it to be `RecipeApp`.

While you could change it manually in multiple places, you’ll reduce the chance of a copy-and-paste error or typo by using the IDE’s **rename** action instead. This lets you rename a symbol at its definition and all its callers at the same time.

In Android Studio, you’ll find this either under the **Refactor ▸ Rename menu** item or by right-clicking on `MyApp` in `class MyApp...` and navigating to **Refactor ▸ Rename**. Rename **MyApp** to be **RecipeApp**. The result will look like this:

```dart
void main() {
  runApp(RecipeApp());
}
class RecipeApp extends StatelessWidget {
```

`main()` is the entry point for the code when the app launches. `runApp()` tells Flutter which is the top-level widget for the app.

A hot reload won’t include the code changes you just made. To run the new code you need to perform a hot restart. In this specific case you won’d notice any change in the UI.

```
Note: As mentioned in Chapter 1, “Getting Started”, when you save your changes, hot reload automatically runs and updates the UI. If this doesn’t happen, check your IDE settings for Flutter to make sure it’s enabled. If you don’t want it to trigger it when you save changes you can run it manually. The shortcut for Android Studio is Command-\.

With hot reload you can quickly see the effect of code changes and the app state is preserved. For example, if the user was in a “logged in” state before the code changed, a hot reload will preserve such a state and you won’t need to log in again to test your changes.

If you’ve made significant changes, like adding a new property to a state or changed main() like in the case above, then you need to hot restart, so that the new change is detected and included in the new build.

For even bigger changes, like adding dependencies or assets, you need to a full build and run.
```

![img20](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img20.png)

# Styling your app

To continue making this into a new app, you’ll customize the appearance of your widgets next. Replace `RecipeApp`’s `build()` with:

```dart
// 1
@override
Widget build(BuildContext context) {
  // 2
  final ThemeData theme = ThemeData();
  // 3
  return MaterialApp(
    // 4
    title: 'Recipe Calculator',
    // 5
    theme: theme.copyWith(
        colorScheme: theme.colorScheme.copyWith(
            primary: Colors.grey,
            secondary: Colors.black,
        ),
    ),
    // 6
    home: const MyHomePage(title: 'Recipe Calculator'),
  );
}
```

This code changes the appearance of the app:

1 - A widget’s build() method is the entry point for composing together other widgets to make a new widget.

2 - A theme determines visual aspects like color. The default ThemeData will show the standard Material defaults.

3 - MaterialApp uses Material Design and is the widget that will be included in RecipeApp.

4 - The title of the app is a description that the device uses to identify the app. The UI won’t display this.

5 - By copying the theme and replacing the color scheme with an updated copy lets you change the app’s colors. Here, the primary color is Colors.grey and the secondary color is Colors.black.

6 - This still uses the same MyHomePage widget as before, but now, you’ve updated the title and displayed it on the device.

When you relaunch the app now, you’ll see the same widgets, but they have a more sophisticated style.

![img21](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img21.png)

You’ve taken the first step towards making the app your own by customizing the `MaterialApp` body. You’ll finish cleaning up the app in the next section.
