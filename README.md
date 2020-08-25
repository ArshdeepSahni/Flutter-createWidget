# Flutter-createWidget


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
  
