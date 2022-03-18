First, we need to add a new package to our project. run this command in the terminal:

```shell
flutter pub add go_router
```

Then, in your `main.dart` we need to import our new package to be able to use it:

```dart
import 'package:go_router/go_router.dart';
```

We need to create a new instance of our router:

```dart
  void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({Key? key}) : super(key: key);

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Movie APP',
      home: HomePage(),
    );
  }

  final _router = GoRouter();
}
```

Inside our `_router` instance, we will define our two routes, the `home` route and the `MoviePage` route.

```dart
  final _router = GoRouter(
    routes: [
      GoRoute(
        path: '/',
        builder: (context, state) => HomePage(),
      ),
      GoRoute(
        path: '/movie',
        builder: (context, state) => MoviePage(),
      ),
    ],
  );
```

The route that have the path of `/` will always be the home page of our application.

Import the `MoviePage` into this file:

```dart
import 'package:movies_app/pages/home_page.dart';
import 'package:movies_app/pages/movie_page.dart';
```

Now instead of returning a `MaterialApp` from our root widget, we will return a `MaterialApp.router`:

```dart
  @override
  Widget build(BuildContext context) {
    return MaterialApp.router(
        routeInformationParser: _router.routeInformationParser,
        routerDelegate: _router.routerDelegate,
      );
  }

```

We finished setting up our routes and paths.
