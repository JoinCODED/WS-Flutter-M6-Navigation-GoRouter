1. Fork and clone the starter point of the project from [GitHub](https://github.com/Northwest-content/flutter_movie_app), open it in the VS Code, and get the packages.
2. We will structure the files and folders in a way that makes it easier for us to develop the app.
3. Since we will have more than one screen, we will create a folder named **pages** inside the **lib** folder. This folder will hold all the screens files in the app.
4. Since there might be more than one model inside the app, it is better to make a folder called **models** which holds all the **models** in the app.
5. Inside the **models** folder, create a file named **movie.dart**.
6. Inside the **pages** folder, create a file named **“home_page.dart”**
7. Cut the **HomePage** and **\_HomePageState** classes and paste them inside the **home_page.dart** file.

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

8. Import the **material.dart** & **movie.dart** files inside the **home_page.dart** file to get rid of the error there.

```dart
import 'package:flutter/material.dart';
import 'package:flutter_movie_app_starter/models/movie.dart';
```

9. Import the **HomePage** class inside **main.dart** file.

```dart
import 'package:flutter_movie_app_starter/pages/home_page.dart';
```
