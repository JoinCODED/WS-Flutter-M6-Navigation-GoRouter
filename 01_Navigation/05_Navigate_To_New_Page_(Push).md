Now, we need to learn how to navigate between pages. However, to navigate to a new page, we have to specify when we need that navigation to happen.

In our case, we need to go to the movie page when the user clicks the move tile.

18. Wrap the `Row` with the **InkWell** widget to add the **onTap** event in the movie tile, which has the same functionality as the **GestureDetector** widget, but with a nice animation effect.

![image](https://lh6.googleusercontent.com/kot72_5VKV2laZStWICfrg8W0ZjJdyL_RVW6F00Tj68yEjD9q7ocgcN4t3beCCd9QMF1eQl07zW04JTJinzOhO7DWhZ0b4dVVOtlDTG-uimdJ-v6fYrm7z0CaE3bmTIAO-CtTDKI)

```dart
InkWell(      // <- Here
        onTap: () {},
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
      ),
```

Before we move to the new page, we need to understand how the Navigator works inside Flutter.

![navigator](https://lh6.googleusercontent.com/9j26ZwF5PsAngBZSIryDVKsTNUdQ0WjAJrvms2gu2PlCh46Tloblb_yGOqowMnqFIwk0J24P6due0dlF_6SUeOlU2r_mcs45mHth8aWzfHLWTToHLMbcF_-HbsqS_doIkkn-VXzm)

You can imagine the Navigator as the **Stack** that contains multiple pages.
The first top page inside the stack is the page that the user sees.
To enable the user to move to a new page in the stack, we use `GoRouter` methods.

`GoRouter` has a nice extension to the build context that allows you to call different methods such as `go`, `push`, `pop`, etc, with the given route.

19. Import the `GoRouter` package.

```dart
import 'package:go_router/go_router.dart';
```

20. Call the `GoRouter.push()` method inside the **onTap** event and place the path of the page you want to move to.

```dart
InkWell(
      onTap: () =>
          GoRouter.of(context).push('/movie'),
      child: Row(
```

Here, we used the `GoRouter.push` method to show the Movie Page widget.

**Note:** To use the **push** method, you need to pass the **context** object first. Then, you tell Flutter which screen you want to display.

21. Restart the app, and click one of the movie tiles.

![image2](https://user-images.githubusercontent.com/24327781/142048432-eb1dd37c-c0ed-449a-a4f4-aa51e5320bfc.gif)
