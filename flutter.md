### Flutter

Use the Online Fluter Development IDE : [FlutLab.io](https://flutlab.io/)

- Create a Flutter project
- Start to work in the ```main.dart``` file.

# main.dart
- import the material from the package flutter, ```import 'package:flutter/material.dart';```
- ```void main() => runApp(MyApp());``` void main() is a function, runApp is a widget, MyApp() is a class.
- ```StatelessWidget``` is a one more widget
- Basic code with white screen
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(),
      );
    }
  }
  ```
<img width="278" height="497" alt="image" src="https://github.com/user-attachments/assets/75dac59d-cb66-4403-828a-5df3e129ba76" />


- ```debugShowCheckedModeBanner: false``` use this to remove the debug in the screen like above inside the ```MaterialApp()``` widget.
- Type ```Stless``` and choose the StatelessWidget we will have the full class syntax
- Chanege the Stless into ur class name, like MyApp
- Inside the scaffold we have the body attribute use that
- ```Center()``` widget to place the content in the center part of the screen, ```child``` is a attribute in the center that means chile of the center widget.
- ```Text()``` widget is used to display the Text with the style and font change, like ```fontSize```, ```fontWeight```, ```color``` and ```fontStyle```

```main.dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        body: Center(
            child: Text("Hello Mr. Hari",
                style: TextStyle(
                    fontSize: 40,
                    fontWeight: FontWeight.bold,
                    color: Colors.blue,
                    fontStyle: FontStyle.italic))),
      ),
    );
  }
}
```
## importent widget

- Widgets is nothing as like a fields in the HTML, like Text, button, icon ..
- ```StatelessWidget``` this is used to create a class for a flutter app, just type ```Stless``` choose the 4th suggestion to get the full stucture.
- ``` main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class Stless extends StatelessWidget {
    const Stless({super.key});
    @override
    Widget build(BuildContext context) {
      return Container(
        
      );
    }
  }
  ```
- ```MaterialApp()``` is a widget to use the all the avaiable material in the flutter, like ```home``` attribute and so on.
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class Stless extends StatelessWidget {
    const Stless({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        
      );
    }
  }
  ```
- ```Scaffold()``` is the base widget to start develop the sceen with the white screen and attributes like ```body```, same like this we can use ```Container()``` with a black screen
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(),
      );
    }
  }
  ```
- ```Icon()``` used to display the icon with the attributes
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(
          body: Icon(Icons.alarm, size: 40, color: Colors.yellow),
        ),
      );
    }
  }
  ```
- ```Center()``` used to display the content in the center screen
- ``` main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        home: Scaffold(
          body: Center(child: Icon(Icons.alarm, size: 80, color: Colors.yellow)),
        ),
      );
    }
  }
  ```
- ```Text()``` is used to sceen the text with the attributes.
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        debugShowCheckedModeBanner: false,
        home: Scaffold(
          body: Center(
              child: Text("Welcome to the flutter framework development by Hari",
                  textAlign: TextAlign.center,
                  style: TextStyle(
                      fontSize: 40,
                      fontWeight: FontWeight.bold,
                      color: Colors.blue,
                      fontStyle: FontStyle.italic))),
        ),
      );
    }
  }
  ```
- ```Image()``` is a widget to show the images in the screen, from the ```asset``` (flutter asset), ```network``` (from the internet), ```memory```(from the system memory), ```file```(from the file).
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        debugShowCheckedModeBanner: false,
        home: Scaffold(
          body: Center(
              child: Image.network(
                  "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSOO2q_l5g6ODZJLrjKqBy22kTejhANjhLAEw&s")),
        ),
      );
    }
  }
  ```
- ```Container()``` is like a div in the HTML tag
- ``` main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
          home: Scaffold(
        body: Center(
          child: Container(
            height: 250,
            width: 250,
            decoration: BoxDecoration(
                color: Colors.green,
                borderRadius: BorderRadius.circular(30),
                image: DecorationImage(
                    image: NetworkImage(
                        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSUrIlPDc9BFXePXVeewu7j3T0mbKU6V4bXlA&s"),
                    fit: BoxFit.cover)),
          ),
        ),
      ));
    }
  }
  ```
- Net


  

  

  

  

