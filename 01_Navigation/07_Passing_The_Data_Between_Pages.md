Right now, when you click any of the movie tiles, you will always see the Toy Story data, and to solve this issue, you need to pass the movie data from the home page to the movie page.

![image](https://user-images.githubusercontent.com/24327781/142048646-087d0774-0602-42c7-b364-7673e4881f4b.gif)

To pass data from a specific file to other files in Flutter, you have to create a variable in the page where you want to receive the transferred data in order to be able to store it in this variable.

24. Create a variable of the `Movie` class type and call it movie:

```dart
final Movie movie; // <- Here

  @override
  Widget build(BuildContext context) {
```

Here, we declared a new movie variable of the **Movie** class type.
**Note:** we did not declare it with an initial value.

25. Import the **movie.dart** file, because we are using the Movie class as a type here.

```dart
import 'package:flutter_movie_app_starter/models/movie.dart';
```

26. Create a constructor inside the **MoviePage** class to get the **Movie** object through. To create the constructor easily, use the Vs Code shortcut.

Go to the final variable movie, and click:

- Mac: Command + .
- Windows: Ctrl + .

Then, choose **Generate constructor**.

![constructor](https://lh6.googleusercontent.com/v5bYq7OSmq2ftlIfKo4JNm3b7kgyDLXdoArMe5AVvYWyjd6zxAHOyYFCqz1TYwwsCBm5bghE9UZ5DdQqU-Fdop7k2E91z31OTm7yLfFwbeZd58Dv0d_gb0SfBF8_noRci5gDEtpw)

```dart
 const MoviePage({
    Key? key,
    required this.movie,
  }) : super(key: key);
```

Here, we created a constructor for the **MoviePage**, which contains: the **required** keyword that notifies you to pass the movie object when you call the movie class in any dart files, and the name and type of the variable that we created.

```dart
 const MoviePage({
    Key? key,
    required this.movie, // <- here
  }) : super(key: key);
```

Since we used the **required** keyword, we have to pass the **movie** object to the **MoviePage** widget in the route inside the `main.dart` file.

```dart
      GoRoute(
        path: '/movie',
        builder: (context, state) => MoviePage(movie: state.extra as Movie),
      ),
```

One thing left to do, you need to pass the movie to the `extra` named argument inside the `GoRouter.push` method in the `home_page.dart` file:

```dart
    GoRouter.of(context).push('/movie', extra: movies[index]),

```

Note that we did not pass the whole movies list, we passed one single object of the **movies** list variable using the index.

We finished the process of transferring data from the **home** page to the **movie** page.

Now, let's use the transferred data in the `movie_page.dart`:

27. Replace the **build** method with the code below:

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

We used the **movie** variable that we declared, and in each widget, we used the appropriate properties that were inside the **Movie** class, such as the **movie.name** and **movie.rating** properties.

## Exercise

- Create a **brief** property, and use it inside your app.
