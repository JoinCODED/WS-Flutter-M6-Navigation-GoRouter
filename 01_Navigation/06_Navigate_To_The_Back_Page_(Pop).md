We learned how to move to a new screen using the `GoRouter.push` method, but what about moving back to a previous screen?

When the user clicks one of the movie tiles, the app will push to a new page, and because there is an **AppBar** inside the **MoviePage** widget, Flutter adds the back button automatically. When the back button is clicked, the app will return to the previous page.

![image](https://lh6.googleusercontent.com/8DhgjyGFDGdrT1QbvaXbonlf7UF8fddcgQjnk_uKI-QyLJ8SbyKUir7x6YNgIQLNj6RPlAW6d29iePurGUr9xftDrEPOFnDrJxZ8NOpVE7PfnfRnGPGH_5TMtTb44d9ilkys6vmU)

What if we do not have an app bar and we want to go back to a previous page?

We first add a `Button` widget somewhere in the file, and to make this button take us back to the previous screen, we use `GoRouter.pop()`

22. Add the `ElevatedButton` widget on the top inside the children named argument in the `Column` widget.

```dart
       ElevatedButton(
            onPressed: () {},
            child: Text('Back'),
          ),
```

![back_button](https://lh4.googleusercontent.com/iBqjFINtkOlHAmFBySpRFPEkrZPREwS5bcZpUIzMkQhYX8b5IHVPIGgvjmw5oDWQeyYPa8uxo88dr6zepr7pUZ1Mj14ah1nynKmII38KYxUd0B1clLCU8yKQxxl9Vr2DgI_KaNui)

23. Use the **GoRouter.pop()** function inside the **onPressed** named argument in the **ElevatedButton** widget.

```dart
 ElevatedButton(
            onPressed: () => GoRouter.of(context).pop(),
            child: Text('Back'),
          ),
```

![back](https://lh5.googleusercontent.com/-vreHJxhDkJBXM6gxRQPJqw4pV7rlVL4Pp_n2_6pelNbcDqVyrg80mwBUxswO0-cPeYYNWbqR9REp4cT8hMhF6BQbx-hziSuzgtURx_1hcIi0jFMYGUM5bW-S6zMzGOEDeV-UpYU)

**Note:** You can remove the back button, it was for practicing only.
