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
