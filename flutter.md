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
<img width="278" height="497" alt="image" src="https://github.com/user-attachments/assets/75dac59d-cb66-4403-828a-5df3e129ba76" />
- ```debugShowCheckedModeBanner: false``` use this to remove the debug in the screen like above inside the ```MaterialApp()``` widget


