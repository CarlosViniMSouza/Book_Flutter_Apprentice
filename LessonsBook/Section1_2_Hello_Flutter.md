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

In Android Studio, you’ll find this either under the **Refactor ▸ Rename** menu item or by right-clicking on `MyApp` in `class MyApp...` and navigating to **Refactor ▸ Rename**. Rename **MyApp** to be **RecipeApp**. The result will look like this:

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

# Clearing the app

You’ve themed the app, but it’s still displaying the counter demo. Clearing the screen is your next step. To start, replace the `_MyHomePageState` class with:

```dart
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    // 1
    return Scaffold(
      // 2
      appBar: AppBar(
        title: Text(widget.title),
      ),
      // 3
      body: SafeArea(
        // TODO: Replace child: Container()
        // 4
        child: Container(),
        ),
    );
  }

  // TODO: Add buildRecipeCard() here
}
```

A quick look at what this shows:

1 - A `Scaffold` provides the high-level structure for a screen. In this case, you’re using two properties.

2 - `AppBar` gets a title property by using a `Text` widget that has a `title` passed in `from home: MyHomePage(title: 'Recipe Calculator')` in the previous step.

3 - `body` has `SafeArea`, which keeps the app from getting too close to the operating system interfaces such as the notch or interactive areas like the Home Indicator at the bottom of some iOS screens.

4 - `SafeArea` has a `child` widget, which is an empty `Container` widget.

One hot reload later, and you’re left with a clean app:

![img22](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img22.png)

# Building a recipe list

An empty recipe app isn’t very useful. The app should have a nice list of recipes for the user to scroll through. Before you can display these, however, you need the data to fill out the UI.

# Adding a data model

You’ll use `Recipe` as the main data structure for recipes in this app.

Create a new **Dart file** in the **lib** folder, named **recipe.dart**.

Add the following class to the file:

```dart
class Recipe {
  String label;
  String imageUrl;
  // TODO: Add servings and ingredients here

  Recipe(
    this.label,
    this.imageUrl,
  );
  // TODO; Add List<Recipe> here
}

// TODO: Add Ingredient() here
```

This is the start of a `Recipe` model with a label and an image.

You’ll also need to supply some data for the app to display. In a full-featured app, you’d load this data either from a local database or a JSON-based API. For the sake of simplicity as you get started with Flutter, however, you’ll use hard-coded data in this chapter.

Add the following method to `Recipe` by replacing `// TODO: Add List<Recipe> here` with:

```dart
static List<Recipe> samples = [
  Recipe(
    'Spaghetti and Meatballs',
    'assets/2126711929_ef763de2b3_w.jpg',
  ),
  Recipe(
    'Tomato Soup',
    'assets/27729023535_a57606c1be.jpg',
  ),
  Recipe(
    'Grilled Cheese',
    'assets/3187380632_5056654a19_b.jpg',
  ),
  Recipe(
    'Chocolate Chip Cookies',
    'assets/15992102771_b92f4cc00a_b.jpg',
  ),
  Recipe(
    'Taco Salad',
    'assets/8533381643_a31a99e8a6_c.jpg',
  ),
  Recipe(
    'Hawaiian Pizza',
    'assets/15452035777_294cefced5_c.jpg',
  ),
];
```

This is a hard-coded list of recipes. You’ll add more detail later, but right now, it’s just a list of names and images.

```
Note: A `List` is an ordered collection of items; in some programming languages, it’s called an array. List indexes start with 0.
```

You’ve created a List with images, but you don’t have any images in your project yet. To add them, go to **Finder** and copy the **assets** folder from the top level of **02-hello-flutter** in the book materials of your project’s folder structure. When you’re done, it should live at the same level as the **lib** folder. That way, the app will be able to find the images when you run it.

You’ll notice that by copy-pasting in Finder, the folder and images automatically display in the Android Studio project list.

![img23](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img23.png)

But just adding assets to the project doesn’t display them in the app. To tell the app to include those assets, open **pubspec.yaml** in the **recipes** project root folder.

Under `# To add assets to your application...` add the following lines:

```
assets:
  - assets/
```

These lines specify that assets/ is an assets folder and must be included with the app. Make sure that the first line here is aligned with the `uses-material-design: true` line above it.

# Displaying the list

With the data ready to go, your next step is to create a place for the data to go to.

Back in _main.dart_, you need to import the data file so the code in _main.dart_ can find it. Add the following to the top of the file, under the other import lines:

```dart
import 'recipe.dart';
```

Next, in `_MyHomePageState` `SafeArea’s` `child`, find and replace `// TODO: Replace child: Container()` and the two lines beneath it with:

This code does the following:

4 - Builds a list using `ListView`.

5 - `itemCount` determines the number of rows the list has. In this case, `length` is the number of objects in the `Recipe.samples` list.

6 - `itemBuilder` builds the widget tree for each row.

7 - A `Text` widget displays the name of the recipe.

Perform a hot reload now and you’ll see the following list:

![img24](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img24.png)

# Putting the list into a card

It’s great that you’re displaying real data now, but this is barely an app. To spice things up a notch, you need to add images to go along with the titles.

To do this, you’ll use a `Card`. In Material Design, `Cards` define an area of the UI where you’ve laid out related information about a specific entity. For example, a `Card` in a music app might have labels for an album’s title, artist and release date along with an image for the album cover and maybe a control for rating it with stars.

Your recipe `Card` will show the recipe’s label and image. Its widget tree will have the following structure:

![img25](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img25.png)

In _main.dart_, at the bottom of `_MyHomePageState` create a _ custom widget_ by replacing `// TODO: Add buildRecipeCard()` here with:

```dart
Widget buildRecipeCard(Recipe recipe) {
  // 1
  return Card(
    // 2
      child: Column(
        // 3
        children: <Widget>[
          // 4
          Image(image: AssetImage(recipe.imageUrl)),
          // 5
          Text(recipe.label),
        ],
      ),
  );
}
```

Here’s how you define your new custom `Card` widget:

1 - You return a `Card` from `buildRecipeCard()`.
2 - The `Card’s` child property is a `Column`. A `Column` is a widget that defines a vertical layout.
3 - The `Column` has two `children`.
4 - The first child is an `Image widget`. `AssetImage` states that the image is fetched from the local asset bundle defined in _pubspec.yaml_.
5 - A `Text` widget is the second child. It will contain the `recipe.label` value.

To use the card, go to `_MyHomePageState` and replace `// TODO: Update to return Recipe card` and the `return` line below it with this:

```dart
// TODO: Add GestureDetector
return buildRecipeCard(Recipe.samples[index]);
```

That instructs the `itemBuilder` to use the custom `Card` widget for each recipe in the `samples` list.

Hot restart the app to see the image and text cards.

# Looking at the widget tree

Now’s a good time to think about the widget tree of the overall app. Do you remember that it started with `RecipeApp` from `main()`?

![img26](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img26.png)

`RecipeApp` built a `MaterialApp`, which in turn used `MyHomePage` as its home. That builds a `Scaffold` with an `AppBar` and a `ListView`. You then updated the `ListView` builder to make a `Card` for each item.

Thinking about the widget tree helps explain the app as the layout gets more complicated and as you add interactivity. Fortunately, you don’t have to hand-draw a diagram each time.

In Android Studio, open the _Flutter Inspector_ from the _View ▸ Tool Windows ▸ Flutter Inspector_ menu while your app is running. This opens a powerful UI debugging tool.

![img27](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img27.png)

This view shows you all the widgets onscreen and how they are composed. As you scroll, you can refresh the tree. You might notice the number of cards change. That’s because the `List` doesn’t keep every item in memory at once to improve performance. You’ll cover more about how that works in a later chapter.

# Making it look nice

The default cards look okay, but they’re not as nice as they could be. With a few added extras, you can spiffy the card up. These include wrapping widgets in layout widgets like `Padding` or specifying additional styling parameters.

Get started by replacing `buildRecipeCard()` with:

```dart
Widget buildRecipeCard(Recipe recipe) {
  return Card(
    // 1
    elevation: 2.0,
    // 2
    shape: RoundedRectangleBorder(
      borderRadius: BorderRadius.circular(10.0)),
    // 3
    child: Padding(
      padding: const EdgeInsets.all(16.0),
      // 4
      child: Column(
        children: <Widget>[
          Image(image: AssetImage(recipe.imageUrl)),
          // 5
          const SizedBox(
            height: 14.0,
          ),
          // 6
          Text(
            recipe.label,
            style: const TextStyle(
              fontSize: 20.0,
              fontWeight: FontWeight.w700,
              fontFamily: 'Palatino',
            ),
          )
        ],
      ),
    ),
  );
}
```

This has a few updates to look at:

1 - A card’s `elevation` determines _how high off the screen_ the card is, affecting its shadow.

2 - `shape` handles the shape of the card. This code defines a rounded rectangle with a `10.0` corner radius.

3 - `Padding` insets its child’s contents by the specified `padding` value.

4 - The padding child is still the same vertical `Column` with the image and text.

5 - Between the image and text is a `SizedBox`. This is a blank view with a fixed size.

6 - You can customize `Text` widgets with a `style` object. In this case, you’ve specified a `Palatino` font with a size of `20.0` and a bold weight of `w700`.

Hot reload and you’ll see a more styled list.

![img28](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img28.png)

You can play around with these values to get the list to look “just right” for you. With hot reload, it’s easy to make changes and instantly see their effect on the running app.

Using the Widget inspector, you’ll see the added `Padding` and `SizedBox` widgets. When you select a widget, such as the `SizedBox`, it shows you all its real-time properties in a separate pane, which includes the ones you set explicitly and those that were inherited or set by default.

Selecting a widget also highlights where it was defined in the source.

![img29](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img29.png)

```
Note: You may need to click the Refresh Tree button to reload the widget structure in the inspector. See Chapter 4, “Understanding Widgets” for more details.
```

# Adding a recipe detail page

You now have a pretty list, but the app isn’t interactive yet. What would make it great is to show the user details about a recipe when they tap the card. You’ll start implementing this by making the card react to a tap.

# Making a tap response

Inside `_MyHomePageState`, locate `// TODO: Add GestureDetector` and replace the `return` statement beneath it with the following:

```dart
// 7
return GestureDetector(
  // 8
  onTap: () {
    // 9
    Navigator.push(
      context,
      MaterialPageRoute(
        builder: (context) {
        // 10
        // TODO: Replace return with return RecipeDetail()
        return Text('Detail page');
      },
    ),
   );
  },
  // 11
  child: buildRecipeCard(Recipe.samples[index]),
);

```

This introduces a few new widgets and concepts. Looking at the lines one at a time:

7 - Introduces a `GestureDetector` widget, which, as the name implies, detects gestures.

8 - Implements an `onTap` function, which is the callback called when the widget is tapped.

9 - The `Navigator` widget manages a stack of pages. Calling `push()` with a `MaterialPageRoute` will push a new Material page onto the stack. Section III, “Navigating Between Screens”, will cover navigation in a lot more detail.

10 - `builder` creates the destination page widget.

11 - `GestureDetector’s` child widget defines the area where the gesture is active.

Hot reload the app and now each card is tappable. _Tap_ a recipe and you’ll see a black _Detail page_:

![img30](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img30.png)

# Creating an actual target page

The resulting page is obviously just a placeholder. Not only is it ugly, but because it doesn’t have all the normal page trappings, the user is now stuck here, at least on iOS devices without a back button. But don’t worry, you can fix that!

In _lib_, create a new _Dart file_ named _recipe_detail.dart_.

Now, add this code to the file, ignore the red squiggles:

```dart
import 'package:flutter/material.dart';
import 'recipe.dart';

class RecipeDetail extends StatefulWidget {
  final Recipe recipe;

  const RecipeDetail({
    Key? key,
    required this.recipe,
  }) : super(key: key);

  @override
  _RecipeDetailState createState() {
    return _RecipeDetailState();
  }
}

// TODO: Add _RecipeDetailState here
```

This creates a new `StatefulWidget` which has an initializer that takes the `Recipe` details to display. This is a `StatefulWidget` because you’ll add some interactive state to this page later.

You need `_RecipeDetailState` to build the widget, replace `// TODO: Add _RecipeDetailState here` with:

```dart
class _RecipeDetailState extends State<RecipeDetail> {
  // TODO: Add _sliderVal here

  @override
  Widget build(BuildContext context) {
    // 1
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.recipe.label),
      ),
      // 2
      body: SafeArea(
        // 3
        child: Column(
          children: <Widget>[
            // 4
            SizedBox(
              height: 300,
              width: double.infinity,
              child: Image(
                image: AssetImage(widget.recipe.imageUrl),
              ),
            ),
            // 5
            const SizedBox(
              height: 4,
            ),
            // 6
            Text(
              widget.recipe.label,
              style: const TextStyle(fontSize: 18),
            ),
            // TODO: Add Expanded

            // TODO: Add Slider() here
          ],
        ),
      ),
    );
  }
}
```

The body of the widget is the same as you’ve already seen. Here are a few things to notice:

1 - `Scaffold` defines the page’s general structure.
2 - In the `body`, there’s a `SafeArea`, a `Column` with a `Container`, a `SizedBox` and `Text` children.
3 - `SafeArea` keeps the app from getting too close to the operating system interfaces, such as the notch or the interactive area of most iPhones.
4 - One new thing is the `SizedBox` around the `Image`, which defines resizable bounds for the image. Here, the `height` is fixed at 300 but the `width` will adjust to fit the aspect ratio. The unit of measurement in Flutter is *logical pixels*.
5 - There is a spacer `SizedBox`.
6 - The `Text` for the `label` has a `style` that’s a little different than the main `Card`, to show you how much customizability is available.

Next, go back to *main.dart* and add the following line to the top of the file:

```dart
import 'recipe_detail.dart';
```

Then find `// TODO: Replace return with return RecipeDetail()` replace it and the existing `return` statement with:

```dart
return RecipeDetail(recipe: Recipe.samples[index]);
```

Perform a hot restart by choosing *Run ▸ Flutter Hot Restart* from the menu to set the app state back to the original list. Tapping a recipe card will now show the `RecipeDetail` page.

```
Note: You need to use hot restart here because hot reload won’t update the UI after you update the state.
```

![img31](https://github.com/CarlosViniMSouza/Book_Flutter_Apprentice/blob/master/LessonsBook/Images/img31.png)

Because you now have a `Scaffold` with an `appBar`, Flutter will automatically include a back button to return the user to the main list.

# Adding ingredients