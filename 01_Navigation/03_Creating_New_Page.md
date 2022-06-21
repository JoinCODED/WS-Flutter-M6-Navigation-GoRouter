When you want to create a new screen, you have create a new file inside the pages folder. This file will be responsible for showing the new page.

10. Create a new screen named **movie_page.dart**, which is responsible for showing the movie details when the user clicks one of the movie tiles.

![image](https://user-images.githubusercontent.com/24327781/142048135-1e3583a8-223e-4149-84a8-7e27af9752d2.gif)

11. In the **movie_page.dart** file, create a new stateless widget named **MoviePage**, import the **material.dart** file, and set it up with the **Scaffold** widget.

```dart
import 'package:flutter/material.dart';

class MoviePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold();
  }
}
```

12. Copy the code in the **Scaffold** widget below and paste it into your empty **Scaffold** widget in the **movie_page.dart** file.

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

Now, we have a group of widgets responsible for drawing the **MoviePage** widget, and static data related to the **Toy Story** movie. Later, we will make the **MoviePage** dynamic.
