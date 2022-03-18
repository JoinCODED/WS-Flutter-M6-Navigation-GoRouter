1. Download the starter project from GitHub, then open the project by using the VS Code, and get the packages.

   https://github.com/Northwest-content/flutter_movie_app

2. We are still developing the movie app that we developed earlier.
3. A good practice is to structure the files and folders in an organized way so that it is easier for us to develop the app.
4. Because we will have more than one screen, we will create a folder that holds all the screen files on the app, and we will name this folder **“pages”**. Inside the **lib** folder create a **“pages”** folder.
5. Also, because there can be more than one model inside our app, it is better to make a folder called “models” which will hold all the **models** for the app. For example, in our **movie** app, we have one model called a movie. Inside the lib folder create a **“models”** folder.
6. Then, move the **movie.dart** file inside **models** folder.
7. Inside **pages** folder, create a new file and name it **“home_page.dart”**
8. Then, cut the **HomePage** class and **\_HomePageState** class, paste it inside the **home_page.dart** file.

```dart
class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  List movies = [
    Movie(name: 'Toy Story', imgPath: 'assets/toy_story.jpeg', rating: 8),
    Movie(name: 'Spider Man', imgPath: 'assets/spider_man.jpeg', rating: 5),
    Movie(name: 'Inside out', imgPath: 'assets/inside_out.jpeg', rating: 7),
    Movie(name: 'The LEGO Movie', imgPath: 'assets/lego.jpeg', rating: 5.5),
    Movie(name: 'The Lion King', imgPath: 'assets/lion_king.jpeg', rating: 9),
    Movie(name: 'Frozen', imgPath: 'assets/frozen.jpeg', rating: 4.5),
    Movie(name: 'Shrek', imgPath: 'assets/shrek.jpeg', rating: 8.5),
    Movie(name: 'BIG HERO', imgPath: 'assets/big_hero.jpeg', rating: 8),
    Movie(name: 'ICE AGE', imgPath: 'assets/ice_age.jpeg', rating: 7.5),
    Movie(name: 'BRAVE', imgPath: 'assets/brave.jpeg', rating: 7),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          'Movie APP',
          style: TextStyle(
            fontWeight: FontWeight.bold,
          ),
        ),
      ),
      body: ListView.builder(
        itemCount: movies.length,
        itemBuilder: (BuildContext context, int index) {
          return Card(
            child: Row(
              children: [
                Expanded(
                  child: Container(
                    padding: EdgeInsets.all(10),
                    child: Column(
                      children: [
                        Text(
                          '${movies[index].name}',
                          style: TextStyle(
                            fontWeight: FontWeight.bold,
                            fontSize: 18,
                          ),
                        ),
                        Container(height: 10),
                        Text(
                          'Rating: ${movies[index].rating}/10',
                          style: TextStyle(
                            fontWeight: FontWeight.bold,
                            color: Colors.grey[700],
                            fontSize: 14,
                          ),
                        ),
                      ],
                    ),
                  ),
                ),
                Container(
                  padding: EdgeInsets.all(10),
                  child: Image.asset(
                    movies[index].imgPath, // <- Here
                    width: 125,
                    height: 125,
                  ),
                ),
              ],
            ),
          );
        },
      ),
    );
  }
}
```

9. Import the **material.dart** file & **movie.dart** file inside the **home_page.dart** file to remove the error that inside the **home_page.dart** file.

```dart
import 'package:flutter/material.dart';
import 'package:flutter_movie_app_starter/models/movie.dart';
```

10. Inside the **main.dart**, you will find one error because we need to import the **HomePage** class inside **main.dart** file. So, import the **home_page.dart** file.

```dart
import 'package:flutter_movie_app_starter/pages/home_page.dart';
```
