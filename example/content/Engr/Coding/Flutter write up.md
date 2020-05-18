# Flutter write up

## [part 1](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt1)

###　A super simple flutter app

``` dart
import 'package:flutter/material.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: const Text('Welcome to Flutter'),
        ),
        body: const Center(
          child: const Text('Hello World'),
        ),
      ),
    );
  }
}
```

important:

```dart
 return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: const Text('Welcome to Flutter'),
        ),
        body: const Center(
          child: const Text('Hello World'),
        ),
      ),
    );
```

- MaterialApp
  - title
  - home
    - appBar
      - title
    - body
      - child

### [External Package](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt1/#3)

description is in **pubspec.yaml**

``` dart
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final wordPair = new WordPair.random(); // Add this line.
    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(    // Change "const" to "new".
          //child: const Text('Hello World'),   // Replace this text...
          child: new Text(wordPair.asPascalCase),  // With this text.
        ),
      ),
    );
  }
}
```



So WordPair is just a class and we init our object wordPair with the construct function WordPair.random(), and access the method asPascalCase.

And in this part, we can usehot reload button (![img](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt1/img/7f9a9e103c7b5e5.png)) .

### Stateful Widget

Add two new class

```dart
class RandomWords extends StatefulWidget {
  @override
  RandomWordsState createState() => new RandomWordsState();
}
```

```dart
class RandomWordsState extends State<RandomWords> {
  @override                                  // Add from this line ... 
  Widget build(BuildContext context) {
    final WordPair wordPair = new WordPair.random();
    return new Text(wordPair.asPascalCase);
  }                                          // ... to this line.
}
```

``` dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final WordPair wordPair = new WordPair.random();  // Delete this line.

    return new MaterialApp(
      title: 'Welcome to Flutter',
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(
          //child: new Text(wordPair.asPascalCase), // Change this line to... 
          child: new RandomWords(),                 // ... this line.
        ),
      ),
    );
  }
}
```

### Infinite scrolling ListView

add (enforced private (because of _)) lists and font size.

This time we are not gonna return a Scaffold directly to main class.

```dart
class RandomWordsState extends State<RandomWords> {
  // Add the next two lines.
  final List<WordPair> _suggestions = <WordPair>[];
  final TextStyle _biggerFont = const TextStyle(fontSize: 18.0); 
  ...
}
```

```dart
  Widget _buildSuggestions() {
    return new ListView.builder(
      padding: const EdgeInsets.all(16.0),
      // The itemBuilder callback is called once per suggested 
      // word pairing, and places each suggestion into a ListTile
      // row. For even rows, the function adds a ListTile row for
      // the word pairing. For odd rows, the function adds a 
      // Divider widget to visually separate the entries. Note that
      // the divider may be difficult to see on smaller devices.
      itemBuilder: (BuildContext _context, int i) {
        // Add a one-pixel-high divider widget before each row 
        // in the ListView.
        if (i.isOdd) {
          return new Divider();
        }

        // The syntax "i ~/ 2" divides i by 2 and returns an 
        // integer result.
        // For example: 1, 2, 3, 4, 5 becomes 0, 1, 1, 2, 2.
        // This calculates the actual number of word pairings 
        // in the ListView,minus the divider widgets.
        final int index = i ~/ 2;
        // If you've reached the end of the available word
        // pairings...
        if (index >= _suggestions.length) {
          // ...then generate 10 more and add them to the 
          // suggestions list.
          _suggestions.addAll(generateWordPairs().take(10));
        }
        return _buildRow(_suggestions[index]);
      }
    );
  }
```

In this section, itemBuilder is the generator run every time to build list view. So every time we calculate the real index of the words and check if we need to add more words to _suggestions or not.

```dart
 Widget _buildRow(WordPair pair) {
    return new ListTile(
      title: new Text(
        pair.asPascalCase,
        style: _biggerFont,
      ),
    );
  }
```

```dart
@override
  Widget build(BuildContext context) {
    //final wordPair = new WordPair.random(); // Delete these... 
    //return new Text(wordPair.asPascalCase); // ... two lines.

    return new Scaffold (                   // Add from here... 
      appBar: new AppBar(
        title: new Text('Startup Name Generator'),
      ),
      body: _buildSuggestions(),
    );                                      // ... to here.
  }

```

```dart
@override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Startup Name Generator',
      home: new RandomWords(),
    );
  }
```

