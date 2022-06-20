13. Run the command below to get the `go_router` package:

```shell
flutter pub add go_router
```

14. In the `main.dart` file, import the new package to be able to use it:

```dart
import 'package:go_router/go_router.dart';
```

To use the `go_router` package, there are two main classes you need to use:

- GoRouter.
- GoRoute.

By creating the `GoRouter` class, you can provide an initial route and the routes you need for each screen.

Let's start implementing the router. First, we will create a variable called `_router` that holds the instance of the `GoRouter` class:

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

  final _router = GoRouter();  // HERE
}
```

`GoRouter` uses a `GoRoute` class which contains a path — like a URL, an optional name that you can use instead of paths, and either a page builder that returns a page or a redirect handler that redirects you to another route.

15. Inside the `_router` instance, define two routes: the `home` and the `MoviePage` routes.

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

> Remember that all the paths are always defined as strings.
> The route with the path `/` will always be the home page of the application.

16. Import the `MoviePage` and `HomePage` into the `main.dart` file:

```dart
import 'package:movies_app/pages/home_page.dart';
import 'package:movies_app/pages/movie_page.dart';
```

17. Replace the `MaterialApp` with the `MaterialApp.router`:

```dart
  @override
  Widget build(BuildContext context) {
    return MaterialApp.router(
        routeInformationParser: _router.routeInformationParser,
        routerDelegate: _router.routerDelegate,
      );
  }

```

> **Note:** Creating a `GoRouter` gives you a `RouterDelegate` and a `RouterInformationParser` for free.

We finished setting up the routes and paths for the screens.
