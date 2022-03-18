When you want to create a new screen, you will first create a new file inside the pages folder, and the file that you created will be responsible for showing the new page you want to show.

11. Right now, we will create a new screen that will be responsible for showing the movie details when the user clicks one of the movie tiles.

![image](https://user-images.githubusercontent.com/24327781/142048135-1e3583a8-223e-4149-84a8-7e27af9752d2.gif)

12. The first step is to create a new dart file inside the **pages** folder, and we will call it **movie_page.dart**.

13. In order to create a new page, we will create a new widget of type stateless widget and we will call it **MoviePage**. Also, don’t forget to import **material.dart** file. Also, note that we started with the **Scaffold** widget, every time you create a new page, you will be used the **Scaffold** widget.

```dart
import 'package:flutter/material.dart';

class MoviePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold();
  }
}
```

**Note**: In our case, we don’t need a **setState** method that why we used the stateless widget, if your page needs a **setState** method use the stateful widget instead.

14. Inside the **movie_page.dart**, remove the empty **Scaffold** widget, and replace it with this widget tree.

```dart
import 'package:flutter/material.dart';

class MoviePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          'Toy Story',
          style: TextStyle(
            fontWeight: FontWeight.bold,
          ),
        ),
      ),
      body: Column(
        children: [
          Container(height: 30),
          Image.asset(
            'assets/toy_story.jpeg',
            width: 300,
            height: 400,
            fit: BoxFit.contain,
          ),
          Container(
            alignment: Alignment.centerLeft,
            padding: EdgeInsets.all(30),
            child: Text(
              'Rating: 8/10',
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
}
```

Here, we have a group of widgets that are responsible for drawing the **MoviePage** widget. Also, here we have static data that related to the **Toy Story** movie, later we will make the **MoviePage** dynamic.
