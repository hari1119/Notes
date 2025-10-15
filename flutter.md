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
                    fit: BoxFit.cover),
                boxShadow: [
                  BoxShadow(
                      color: Color(0xff080808),
                      offset: Offset(4.5, 2.5),
                      blurRadius: 6.0),
                ]),
          ),
        ),
      ));
    }
  }

  ```
- ```CircleAvatar()``` used to create a profile pic, like what's app
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
          home: Scaffold(
        body: Center(
          child: CircleAvatar(
            backgroundColor: Colors.black,
            radius: 50,
            backgroundImage: NetworkImage(
                "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR-fHmKlKiDhirNAwa21TDkjjv1t1cwXv_BlA&s"),
          ),
        ),
      ));
    }
  }
  ```
- ```CircularProgressIndicator()``` circul progress bar, like loading...
- ```main.dart
  import 'package:flutter/material.dart';

  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    const MyApp({super.key});
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
          home: Scaffold(
        body: Center(
            child: CircularProgressIndicator(
          color: Colors.blue,
          backgroundColor: Colors.black,
          strokeWidth: 10,
          // value: 0.2,
        )),
      ));
    }
  }
  ```
- net
- ```AppBar()``` use to add a app bar in the screen
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
            appBar: AppBar(
                title: Text("Money Management"),
                backgroundColor: Colors.blue,
                elevation: 250,
                actions: [Icon(Icons.search), Icon(Icons.more_vert)],
                leading: Icon(Icons.menu),
            ),
            body: Center()),
        );
    }
    }
```
- ```ElevatedButton()``` Enable a button in the screen with the action.
``` main.dart
import 'dart:ui';

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
const MyApp({super.key});
@override
Widget build(BuildContext context) {
    return MaterialApp(
    debugShowCheckedModeBanner: false,
    home: Scaffold(
        appBar: AppBar(
            title: Text("Money Management"),
            backgroundColor: Colors.blue,
            elevation: 250,
            actions: [Icon(Icons.search), Icon(Icons.more_vert)],
            leading: Icon(Icons.menu),
        ),
        body: Center(
            child: ElevatedButton(
            style: ElevatedButton.styleFrom(
                backgroundColor: Colors.blue,
                elevation: 30,
                textStyle: TextStyle(fontSize: 15)),
            onPressed: () {
                print("Are You Sure?");
            },
            child: Text("Hit Me IF You Can"),
            ),
        )),
    );
}
}
```
- ```TextButton()``` button with only the text interface, like forgot button.
``` main.dart
import 'dart:ui';

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
          appBar: AppBar(
            title: Text("Money Management"),
            backgroundColor: Colors.blue,
            elevation: 250,
            actions: [Icon(Icons.search), Icon(Icons.more_vert)],
            leading: Icon(Icons.menu),
          ),
          body: Center(
            child: TextButton(
              style: TextButton.styleFrom(
                  // backgroundColor: Colors.blue,
                  elevation: 30,
                  textStyle: TextStyle(fontSize: 15)),
              onPressed: () {
                print("Are You Sure?");
              },
              child: Text("Hit Me IF You Can"),
            ),
          )),
    );
  }
}
```
- ```FloatingActionButton()``` float button like a what's a call button.
``` main.dart
import 'dart:ui';

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
          floatingActionButton: FloatingActionButton(
            onPressed: () {},
            child: Icon(Icons.notes),
            backgroundColor: Colors.blue,
            elevation: 20,
            hoverColor: Colors.red,
            foregroundColor: Colors.black,
          ),
          appBar: AppBar(
            title: Text("Money Management"),
            backgroundColor: Colors.blue,
            elevation: 250,
            actions: [Icon(Icons.search), Icon(Icons.more_vert)],
            leading: Icon(Icons.menu),
          ),
          body: Center(
            child: TextButton(
              style: TextButton.styleFrom(
                  // backgroundColor: Colors.blue,
                  elevation: 30,
                  textStyle: TextStyle(fontSize: 15)),
              onPressed: () {
                print("Are You Sure?");
              },
              child: Text("Hit Me IF You Can"),
            ),
          )),
    );
  }
}
```

- ```ButtonBar()``` Used to Align the buttons together.
``` main.dart
import 'dart:ui';

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
          floatingActionButton: FloatingActionButton(
            onPressed: () {},
            child: Icon(Icons.notes),
            backgroundColor: Colors.blue,
            elevation: 20,
            hoverColor: Colors.red,
            foregroundColor: Colors.black,
          ),
          appBar: AppBar(
            title: Text("Money Management"),
            backgroundColor: Colors.blue,
            elevation: 250,
            actions: [Icon(Icons.search), Icon(Icons.more_vert)],
            leading: Icon(Icons.menu),
          ),
          body: Center(
              child: ButtonBar(
            alignment: MainAxisAlignment.spaceEvenly,
            children: [
              ElevatedButton(
                style: ElevatedButton.styleFrom(
                    backgroundColor: Colors.blue,
                    elevation: 30,
                    textStyle: TextStyle(fontSize: 15)),
                onPressed: () {
                  print("You Pressed The Button : A");
                },
                child: Text("A"),
              ),
              ElevatedButton(
                style: ElevatedButton.styleFrom(
                    backgroundColor: Colors.blue,
                    elevation: 30,
                    textStyle: TextStyle(fontSize: 15)),
                onPressed: () {
                  print("You Pressed The Button : B");
                },
                child: Text("B"),
              ),
              ElevatedButton(
                style: ElevatedButton.styleFrom(
                    backgroundColor: Colors.blue,
                    elevation: 30,
                    textStyle: TextStyle(fontSize: 15)),
                onPressed: () {
                  print("You Pressed The Button : C");
                },
                child: Text("C"),
              ),
            ],
          ))),
    );
  }
}
```
- ```Row()``` use to set the widgets row wise in the screen
``` main.dart
// import 'dart:ui';

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        body: Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            Text(
              "Row-1",
              style: TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
            ),
            Text(
              "Row-2",
              style: TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
            ),
            Text(
              "Row-3",
              style: TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
            )
          ],
        ),
      ),
    );
  }
}
```
- ```Column()``` used to set the widgets column wise.
``` main.dart
// import 'dart:ui';

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        body: Column(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            Text(
              "Column-1",
              style: TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
            ),
            Text(
              "Column-2",
              style: TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
            ),
            Text(
              "Column-3",
              style: TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
            )
          ],
        ),
      ),
    );
  }
}
```

- ```ListTile()``` create a line by line objects like whats app list view.

- ```SingleChildScrollView()``` enable the Scrolling option in the screen.
- <img width="258" height="458" alt="image" src="https://github.com/user-attachments/assets/73ed7f4f-56ed-41f0-87d3-8b604964f8e0" />


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
        floatingActionButton: FloatingActionButton(
            onPressed: () {},
            child: Icon(Icons.message_sharp),
            backgroundColor: Color(0xff075e54),
            foregroundColor: Colors.white),
        appBar: AppBar(
          backgroundColor: Color(0xff075e54),
          title: Text(
            "WhatsApp",
            style: TextStyle(color: Colors.white),
          ),
        ),
        body: SingleChildScrollView(
          child: Column(
            children: [
              WhatsappListTile(
                  "STR",
                  "Hi Simbu, What's up?",
                  "data:image/jpeg;base64,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",
                  "03/02/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "VJD",
                  "Rowdy store?",
                  "data:image/jpeg;base64,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",
                  "15/10/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
              WhatsappListTile(
                  "AK",
                  "Okey, AK Sir",
                  "https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRSRaHlbpeY22gUh_oxDyaMoLqknmjotQpYUB8MAiXZsTSCZol9kan493bPTc4Me-7_4qpgHHROdBTruRZ7Aq22PhzP3EXlFAcOpNE3PmUY",
                  "01/05/2025"),
            ],
          ),
        ),
      ),
    );
  }

  ListTile WhatsappListTile(name_src, message_src, image_src, date_src) {
    return ListTile(
      leading: CircleAvatar(
        backgroundImage: NetworkImage(image_src),
      ),
      title: Text(
        name_src,
        style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
      ),
      subtitle: Text(message_src),
      trailing: Column(children: [
        Text(date_src),
        Icon(Icons.done_all, color: Colors.blue),
      ]),
    );
  }
}
```










### Custom Function in Fluter

- Want to create within the class 

``` main.dart

  ListTile WhatsappListTile(name_src, message_src, image_src, date_src) {
    return ListTile(
      leading: CircleAvatar(
        backgroundImage: NetworkImage(image_src),
      ),
      title: Text(
        name_src,
        style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
      ),
      subtitle: Text(message_src),
      trailing: Column(children: [
        Text(date_src),
        Icon(Icons.done_all, color: Colors.blue),
      ]),
    );
  }
```
  


  

  

  

  

