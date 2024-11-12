
## Develop Android App Using Flutter and Android studio.
- This is the web based mobile app development, binding the web url with the mobile app.

#### Create New project as a Flutter project.

![Reffer](https://github.com/hari1119/Notes/blob/main/files/img/flutter-screenshort/step2.png)


#### Edit the ```Main.dart``` file
- ```title``` change the title based on you need,
- Replace the below code in the ```Main.dart``` file.

```dart

import 'package:flutter/material.dart';
import 'package:webview_flutter/webview_flutter.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'hari-portfolio',
      theme: ThemeData(
        // This is the theme of your application.
        //
        // TRY THIS: Try running your application with "flutter run". You'll see
        // the application has a blue toolbar. Then, without quitting the app,
        // try changing the seedColor in the colorScheme below to Colors.green
        // and then invoke "hot reload" (save your changes or press the "hot
        // reload" button in a Flutter-supported IDE, or press "r" if you used
        // the command line to start the app).
        //
        // Notice that the counter didn't reset back to zero; the application
        // state is not lost during the reload. To reset the state, use hot
        // restart instead.
        //
        // This works for code too, not just values: Most code changes can be
        // tested with just a hot reload.
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'hari-portfolio'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  // This widget is the home page of your application. It is stateful, meaning
  // that it has a State object (defined below) that contains fields that affect
  // how it looks.

  // This class is the configuration for the state. It holds the values (in this
  // case the title) provided by the parent (in this case the App widget) and
  // used by the build method of the State. Fields in a Widget subclass are
  // always marked "final".

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      // This call to setState tells the Flutter framework that something has
      // changed in this State, which causes it to rerun the build method below
      // so that the display can reflect the updated values. If we changed
      // _counter without calling setState(), then the build method would not be
      // called again, and so nothing would appear to happen.
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: null,
      body: const Center(
        child: WebView(
          initialUrl: 'https://hari1119.github.io/',
          javascriptMode: JavascriptMode.unrestricted,
        ),
      ),
    );
  }
}
```

#### Edit the ```pubspec.yaml```

- add the dependencies under the ```flutter:```
- ```webview_flutter``` to view the web in the flutter app.
- ```file_picker``` file uploading option.

```yaml
dependencies:
  flutter:
    sdk: flutter
  webview_flutter: ^3.0.4
  file_picker: ^4.0.0
```

#### Edit the ```Build.gradle```
- open the Build.gradle file Project/android/app/src/Build.gradle
- Change the following verssion.
- ```compileSdkVersion 34```
- ```minSdkVersion 19```
