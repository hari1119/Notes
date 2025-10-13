### Flutter

Use the Online Fluter Development IDE : [FlutLab.io](https://flutlab.io/)

- Create a Flutter project
- Start to work in the ```main.dart``` file.

# main.dart
- import the material from the package flutter, ```import 'package:flutter/material.dart';```
- ```void main() => runApp(MyApp());``` void main() is a function, runApp is a widget, MyApp() is a class.
- ```StatelessWidget``` is a one more widget
- Basic code with white screen
- ```
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
