# Flutter-createWidget
### Method 1:
```dart
import 'dart:core';
    import 'package:flutter/material.dart';

    void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Flutter Demo',
      theme: new ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: new MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  @override
  _MyHomePageState createState() => new _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int count = 0;
  TextEditingController noteSend = TextEditingController();

  @override
  Widget build(BuildContext context) {
    List<Widget> children = new List.generate(
    count,
    (int i) => new InputWidget(
          i,
          noteRec: listString[i],
        ));

    return new Scaffold(
        appBar: new AppBar(title: new Text('some title')),
        body: Column(
          children: <Widget>[
            Container(
              child: TextField(
                controller: noteSend,
              ),
              color: Colors.lightBlueAccent,
              width: 150,
              height: 50,
            ),
            Expanded(
              child: ListView(
                children: children,
                scrollDirection: Axis.vertical,
              ),
            ),
          ],
        ),
        floatingActionButton: new FloatingActionButton(
          child: new Icon(Icons.add),
          onPressed: () {
            setState(() {
              count = count + 1;
            });
          },
        ));
  }
}

class InputWidget extends StatefulWidget {
  final int index;
  final String noteRec;
  InputWidget(this.index, {Key key, this.noteRec}) : super(key: key);

  @override
  _InputWidgetState createState() => _InputWidgetState();
}

class _InputWidgetState extends State<InputWidget> {
  @override
  Widget build(BuildContext context) {
    return new Container(
      decoration: BoxDecoration(
        color: Colors.white,
        borderRadius: BorderRadius.circular(10),
      ),
      child: Row(
        children: <Widget>[
          Column(
            children: <Widget>[
              Icon(
                Icons.image,
                size: 75,
              )
            ],
          ),
          Container(
            margin: EdgeInsets.only(left: 80, right: 30),
            child: Column(
              children: <Widget>[
                Text('Note'),
              ],
            ),
          ),
          Column(
            children: <Widget>[
              Text("${widget.noteRec}"),
            ],
          ),
        ],
      ),
    );
  }
}
```
### Method 2:
```dart
class Body extends StatefulWidget {
  @override
  _BodyState createState() => _BodyState();
}

class _BodyState extends State<Body> {
  int count = 1;
  @override
  Widget build(BuildContext context) {
    return Expanded(
        child: Container(
            child: NotificationListener<OverscrollIndicatorNotification>(
                onNotification: (OverscrollIndicatorNotification overscroll) {
                  overscroll.disallowGlow();
                },
                child: PageView.builder(
                    reverse: true,
                    pageSnapping: false,
                    controller: PageController(viewportFraction: 0.85),
                    itemCount: count,
                    itemBuilder: (context, i) {
                      print(i);
                      if (i == 0) {
                        return Padding(
                            padding: EdgeInsets.only(
                                left:
                                    MediaQuery.of(context).size.height * 0.015,
                                right:
                                    MediaQuery.of(context).size.height * 0.015,
                                top: MediaQuery.of(context).size.width * 0.08,
                                bottom:
                                    MediaQuery.of(context).size.width * 0.15),
                            child: Material(
                                borderRadius: BorderRadius.circular(50.0),
                                color: Colors.white,
                                elevation: 8.0,
                                child: InkWell(
                                  onTap: () {
                                    setState(() {
                                      count++;
                                    });
                                  },
                                  splashColor: Colors.transparent,
                                  highlightColor: Colors.transparent,
                                  child: Column(
                                      mainAxisAlignment:
                                          MainAxisAlignment.center,
                                      children: <Widget>[
                                        Icon(
                                          Icons.add,
                                          size: 50.0,
                                        )
                                      ]),
                                )));
                      } else {
                        return Padding(
                            padding: EdgeInsets.only(
                                left:
                                    MediaQuery.of(context).size.height * 0.015,
                                right:
                                    MediaQuery.of(context).size.height * 0.015,
                                top: MediaQuery.of(context).size.width * 0.08,
                                bottom:
                                    MediaQuery.of(context).size.width * 0.15),
                            child: Material(
                              borderRadius: BorderRadius.circular(50.0),
                              color: Colors.white,
                              elevation: 8.0,
                            ));
                      }
                    }))));
  }
  ```
  
  ## EXPLANATION:
  
  
  
 ```dart
int count=1    // initialize count=1 and then if(i==1){first screen which appear when you have not pressed the button}
```


```dart
itemCount: count,
```




```dart

//if statement as above told ↑

                  if (i == 0)
                   {
                  return Padding
                    (
                      padding: EdgeInsets.only
                      (
                          left:
                              MediaQuery.of(context).size.height * 0.015,
                          right:
                              MediaQuery.of(context).size.height * 0.015,
                          top: MediaQuery.of(context).size.width * 0.08,
                          bottom:
                              MediaQuery.of(context).size.width * 0.15),
                          child: Material
                          (
                          borderRadius: BorderRadius.circular(50.0),
                          color: Colors.white,
                          elevation: 8.0,
                          child: InkWell
                          (
                            onTap: () 
                            {
                              setState(() 
                              {
                                count++;
                              });
                            },
                            splashColor: Colors.transparent,
                            highlightColor: Colors.transparent,
                            child: Column
                            (
                                mainAxisAlignment: MainAxisAlignment.center,
                                children: <Widget>
                                [
                                  Icon
                                  (
                                    Icons.add,
                                    size: 50.0,
                                  )
                                ]
                              ),
                            )
                          )
                        );
                     } 
```




```dart
onTap: ()
{
  setState(
   (){
        count++; // now here i!=1 ====> i>1. so if(i!=1){widget which appear when you have pressed the button}
     }
   );
},
```





```dart
else {
                        return Padding(
                            padding: EdgeInsets.only(
                                left:
                                    MediaQuery.of(context).size.height * 0.015,
                                right:
                                    MediaQuery.of(context).size.height * 0.015,
                                top: MediaQuery.of(context).size.width * 0.08,
                                bottom:
                                    MediaQuery.of(context).size.width * 0.15),
                            child: Material(
                              borderRadius: BorderRadius.circular(50.0),
                              color: Colors.white,
                              elevation: 8.0,
                            ));
                      }
```
  
