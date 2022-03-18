Right now when you click any of the movie tiles, you will always see the Toy Story data, and to solve this issue, we need to pass the movie data from the home page to the movie page.

![image](https://user-images.githubusercontent.com/24327781/142048646-087d0774-0602-42c7-b364-7673e4881f4b.gif)

28. To pass the data from one page to other pages, you will do that with just three steps. The first step is creating a variable on the page you want to transfer data to; In our case, we want to transfer data from the home page to the movie page, so we will create the variable inside the movie page (**MoviePage**).

Also, we should specify the data we want to transfer, in our case we want to pass the Movie object to it. Above the build method, add this variable

```dart
final Movie movie; // <- Here


  @override
  Widget build(BuildContext context) {
```

Here, we declared a new movie variable, and its type is **Movie** class. Also, note here we did not declare it with an initial value.

29. Since we used the **Movie** type class inside the **MoviePage** class, we need to import the **movie.dart** file.

```dart
import 'package:flutter_movie_app_starter/models/movie.dart';
```

30. The second step is to create a constructor inside the **MoviePage** class because we will use it later to pass the **Movie** object through it. To create the constructor easily, we can use the Vs Code shortcut.

Go to the final variable movie, and then click

- Mac: Command + .
- Windows: Ctrl + .

Then click **Generate constructor**,

![constructor](https://lh6.googleusercontent.com/v5bYq7OSmq2ftlIfKo4JNm3b7kgyDLXdoArMe5AVvYWyjd6zxAHOyYFCqz1TYwwsCBm5bghE9UZ5DdQqU-Fdop7k2E91z31OTm7yLfFwbeZd58Dv0d_gb0SfBF8_noRci5gDEtpw)

```dart
 const MoviePage({
    Key? key,
    required this.movie,
  }) : super(key: key);
```

Here, we created a constructor for the **MoviePage**, and we typed the name of the variable that we created which is the **movie** variable.

31. Also, note here the **required** keyword that was typed before the movie variable, this keyword tells the user when you declare the **MoviePage** class on another dart file, you need to pass the movie object inside the **MoviePage** class.

```dart
 const MoviePage({
    Key? key,
    required this.movie, // <- here
  }) : super(key: key);
```

Because of this **required** keyword, we got an error on the **main.dart**, This error tells us that we need to pass the **movie** object inside the **MoviePage** widget.

```dart
      GoRoute(
        path: '/movie',
        builder: (context, state) => MoviePage(), // error
      ),
```

To fix it, pass the movie object inside it like this,

```dart
      GoRoute(
        path: '/movie',
        builder: (context, state) => MoviePage(movie: state.extra as Movie),
      ),
```

32. The last step we need to do, is to navigate to our `home_page.dart` push function, and pass the movie under a property named `extra`:

```dart
    GoRouter.of(context).push('/movie', extra: movies[index]),
```

Here, we passed the **movies** list variable, but also note here that we did not pass the movies list variable completely, we just passed one single object of the **movies** list variable, and we did that by using the **index** with the **movies** list variable.

33. Thus, we finished the process of transferring data from the **home** page to the **movie** page. Now let's use the data that we transferred to the data page.

Replace the **build** method with

```dart
@override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          movie.name, // <- Here
          style: TextStyle(
            fontWeight: FontWeight.bold,
          ),
        ),
      ),
      body: Column(
        children: [
          Container(height: 30),
          Image.asset(
            movie.imgPath, // <- Here
            width: 300,
            height: 400,
            fit: BoxFit.contain,
          ),
          Container(
            alignment: Alignment.centerLeft,
            padding: EdgeInsets.all(30),
            child: Text(
              'Rating: ${movie.rating}/10', // <- Here
              style: TextStyle(
                fontWeight: FontWeight.bold,
                color: Colors.grey[600],
                fontSize: 21,
              ),
            ),
          ),
          Container(
            alignment: Alignment.centerLeft,
            padding: EdgeInsets.only(left: 30, right: 30),
            child: Text(
              "A cowboy doll is profoundly threatened and jealous when a new spaceman figure supplants him as top toy in a boy's room.",
              style: TextStyle(
                fontWeight: FontWeight.bold,
                color: Colors.grey[700],
                fontSize: 18,
              ),
            ),
          ),
        ],
      ),
    );
  }
```

Here, we used the **movie** variable that we declare, and on each widget, we use the appropriate properties that were inside the **Movie** class; such as the **movie.name** and **movie.rating**

## Exercise

- create a **brief** property, and use it inside your App.
