We learned how to push to a new screen, but what about the back to the old screen.

24. When you click one of the movie tiles, your app will push to a new page. Note that since we added an **AppBar** widget inside the **MoviePage** widget, the Flutter will add the back button automatically. When you click this back button, you will return back to the old page.

![image](https://lh6.googleusercontent.com/8DhgjyGFDGdrT1QbvaXbonlf7UF8fddcgQjnk_uKI-QyLJ8SbyKUir7x6YNgIQLNj6RPlAW6d29iePurGUr9xftDrEPOFnDrJxZ8NOpVE7PfnfRnGPGH_5TMtTb44d9ilkys6vmU)

25. But what if you add a button widget, and when you click on this button it will return back to the old page. For example, let’s add a button on the top of the **MoviePage** widget.

Add the **ElevatedButton** widget, on the top inside the children named argument that is inside the **Column** widget.

```dart
       ElevatedButton(
            onPressed: () {},
            child: Text('Back'),
          ),
```

![back_button](https://lh4.googleusercontent.com/iBqjFINtkOlHAmFBySpRFPEkrZPREwS5bcZpUIzMkQhYX8b5IHVPIGgvjmw5oDWQeyYPa8uxo88dr6zepr7pUZ1Mj14ah1nynKmII38KYxUd0B1clLCU8yKQxxl9Vr2DgI_KaNui)

26. Now, we have the back button; Let’s add the back functionality. To do that we will use the **GoRouter.pop()** function inside the **onPressed** named argument that is inside the **ElevatedButton** widget.

```dart
 ElevatedButton(
            onPressed: () => GoRouter.of(context).pop(),
            child: Text('Back'),
          ),
```

![back](https://lh5.googleusercontent.com/-vreHJxhDkJBXM6gxRQPJqw4pV7rlVL4Pp_n2_6pelNbcDqVyrg80mwBUxswO0-cPeYYNWbqR9REp4cT8hMhF6BQbx-hziSuzgtURx_1hcIi0jFMYGUM5bW-S6zMzGOEDeV-UpYU)

27. We learned how to use the **push** and **pop** methods. Since we already have the back button icon inside the **AppBar** widget, we no longer need the **Back** button that we created. So, remove the **ElevatedButton**.
