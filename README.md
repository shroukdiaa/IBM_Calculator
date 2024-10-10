import 'dart:math'; // Remove dart:html

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: CalculatorScreen(),
    );
  }
}

class CalculatorScreen extends StatefulWidget {
  @override
  _CalculatorState createState() {
    return _CalculatorState();
  }
}

class _CalculatorState extends State<CalculatorScreen> {
  bool isMALE = true;
  double heightcm = 120;
  int AGE = 18;
  double widthg = 50;

  @override
  void initState() {
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          "BML Calculator ",
          textAlign: TextAlign.center,
          style: TextStyle(
            fontWeight: FontWeight.bold,
          ),
        ),
      ),
      body: Container(
        child: Column(
          children: [
            Expanded(
              child: Padding(
                padding: EdgeInsets.all(20.0),
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                  children: [
                    Expanded(
                      child: GestureDetector(
                        onTap: () {
                          setState(() {
                            isMALE = false;
                          });
                        },
                        child: Container(
                          decoration: BoxDecoration(
                            borderRadius: BorderRadius.circular(10.0),
                            color: !isMALE ? Colors.blue : Colors.grey[300],
                          ),
                          child: Column(
                            mainAxisAlignment: MainAxisAlignment.center,
                            children: [
                              Image(
                                image: NetworkImage(
                                    "https://th.bing.com/th/id/R.ed1ff40dc9e0a9dac2108890f29a003a?rik=WAyudQSFSfDG0w&riu=http%3a%2f%2fclipart-library.com%2fimages%2f8czr7L9Ki.png&ehk=lw%2bSHvUuwp0Uu%2brPu4lshxGKavcqXh2Gp4Ubashhydg%3d&risl=&pid=ImgRaw&r=0"),
                                height: 80.0,
                                width: 90.0,
                              ),
                              SizedBox(height: 15.0),
                              Text(
                                "FEMALE", // Corrected spelling
                                textAlign: TextAlign.center,
                                style: TextStyle(
                                  fontSize: 20.0,
                                  fontWeight: FontWeight.bold,
                                ),
                              ),
                            ],
                          ),
                        ),
                      ),
                    ),
                    SizedBox(width: 20.0),
                    Expanded(
                      child: GestureDetector(
                        onTap: () {
                          setState(() {
                            isMALE = true;
                          });
                        },
                        child: Container(
                          decoration: BoxDecoration(
                            borderRadius: BorderRadius.circular(10.0),
                            color: isMALE ? Colors.blue : Colors.grey[300],
                          ),
                          child: Column(
                            mainAxisAlignment: MainAxisAlignment.center,
                            children: [
                              Image(
                                image: NetworkImage(
                                    "https://th.bing.com/th/id/R.06ea528c5dc840a34fd308d97fbd4aae?rik=MHaysz%2fSQ%2f%2bSjw&riu=http%3a%2f%2fcliparts.co%2fcliparts%2fpTo%2fdqK%2fpTodqKkpc.png&ehk=VsOalULdNxVd4xLk6jwssFWxKmMZRLXuVh5ZNH4n9DE%3d&risl=&pid=ImgRaw&r=0"),
                                height: 80.0,
                                width: 90.0,
                              ),
                              SizedBox(height: 15.0),
                              Text(
                                "MALE",
                                textAlign: TextAlign.center,
                                style: TextStyle(
                                  fontSize: 20.0,
                                  fontWeight: FontWeight.bold,
                                ),
                              ),
                            ],
                          ),
                        ),
                      ),
                    ),
                  ],
                ),
              ),
            ),
            // Height Slider
            Expanded(
              child: Padding(
                padding: EdgeInsets.symmetric(horizontal: 20.0),
                child: Container(
                  decoration: BoxDecoration(
                    borderRadius: BorderRadius.circular(20.0),
                    color: Colors.grey[300],
                  ),
                  width: double.infinity,
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.center,
                    children: [
                      Text(
                        "HEIGHT",
                        textAlign: TextAlign.center,
                        style: TextStyle(
                          fontSize: 25.0,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        crossAxisAlignment: CrossAxisAlignment.baseline,
                        textBaseline: TextBaseline.alphabetic,
                        children: [
                          Text(
                            "${heightcm.round()}",
                            textAlign: TextAlign.center,
                            style: TextStyle(
                              fontSize: 25.0,
                              fontWeight: FontWeight.w900,
                            ),
                          ),
                          Text(
                            "cm",
                            textAlign: TextAlign.center,
                            style: TextStyle(
                              fontSize: 15.0,
                              fontWeight: FontWeight.bold,
                            ),
                          ),
                        ],
                      ),
                      Slider(
                        value: heightcm,
                        max: 220.0,
                        min: 80.0,
                        onChanged: (value) {
                          setState(() {
                            heightcm = value;
                          });
                        },
                      ),
                    ],
                  ),
                ),
              ),
            ),
            // Age and Weight Inputs
            Expanded(
              child: Padding(
                padding: EdgeInsets.all(20.0),
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.center,
                  crossAxisAlignment: CrossAxisAlignment.center,
                  children: [
                    // Age
                    Expanded(
                      child: Container(
                        decoration: BoxDecoration(
                          borderRadius: BorderRadius.circular(10.0),
                          color: Colors.grey[300],
                        ),
                        child: Column(
                          mainAxisAlignment: MainAxisAlignment.center,
                          children: [
                            Text(
                              "AGE",
                              textAlign: TextAlign.center,
                              style: TextStyle(
                                fontSize: 25.0,
                                fontWeight: FontWeight.bold,
                              ),
                            ),
                            Text(
                              "${AGE}",
                              textAlign: TextAlign.center,
                              style: TextStyle(
                                fontSize: 25.0,
                                fontWeight: FontWeight.w900,
                              ),
                            ),
                            Row(
                              mainAxisAlignment: MainAxisAlignment.center,
                              children: [
                                FloatingActionButton(
                                  onPressed: () {
                                    setState(() {
                                      AGE--;
                                    });
                                  },
                                  heroTag: "AGE--",
                                  mini: true,
                                  child: Icon(Icons.remove),
                                ),
                                FloatingActionButton(
                                  onPressed: () {
                                    setState(() {
                                      AGE++;
                                    });
                                  },
                                  heroTag: "AGE++",
                                  mini: true,
                                  child: Icon(Icons.add),
                                )
                              ],
                            ),
                          ],
                        ),
                      ),
                    ),
                    SizedBox(width: 20.0),
                    // Weight
                    Expanded(
                      child: Container(
                        decoration: BoxDecoration(
                          borderRadius: BorderRadius.circular(10.0),
                          color: Colors.grey[300],
                        ),
                        child: Column(
                          mainAxisAlignment: MainAxisAlignment.center,
                          children: [
                            Text(
                              "WEIGHT",
                              textAlign: TextAlign.center,
                              style: TextStyle(
                                fontSize: 25.0,
                                fontWeight: FontWeight.bold,
                              ),
                            ),
                            Text(
                              "${widthg.round()}",
                              textAlign: TextAlign.center,
                              style: TextStyle(
                                fontSize: 25.0,
                                fontWeight: FontWeight.w900,
                              ),
                            ),
                            Row(
                              mainAxisAlignment: MainAxisAlignment.center,
                              children: [
                                FloatingActionButton(
                                  onPressed: () {
                                    setState(() {
                                      widthg--;
                                    });
                                  },
                                  heroTag: "weight--",
                                  mini: true,
                                  child: Icon(Icons.remove),
                                ),
                                FloatingActionButton(
                                  onPressed: () {
                                    setState(() {
                                      widthg++;
                                    });
                                  },
                                  heroTag: "weight++",
                                  mini: true,
                                  child: Icon(Icons.add),
                                ),
                              ],
                            ),
                          ],
                        ),
                      ),
                    ),
                  ],
                ),
              ),
            ),
            // Calculate Button
            Container(
              color: Colors.blue,
              width: double.infinity,
              child: MaterialButton(
                onPressed: () {
                  double result = widthg / pow(heightcm / 100, 2);
                  Navigator.push(
                    context,
                    MaterialPageRoute(
                      builder: (context) => BMIResult(
                        isMALE: isMALE,
                        RESULT: result.round(),
                        age: AGE,
                      ),
                    ),
                  );
                },
                child: Text(
                  "Calculate",
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 20.0,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
            )
          ],
        ),
      ),
    );
  }
}

class BMIResult extends StatelessWidget {
  final bool isMALE;
  final int RESULT;
  final int age;

  BMIResult({
    required this.isMALE,
    required this.RESULT,
    required this.age,
  });

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          "Result",
          style: TextStyle(fontWeight: FontWeight.bold),
        ),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              "Gender: ${isMALE ? 'Male' : 'Female'}",
              style: TextStyle(
                fontSize: 25.0,
                fontWeight: FontWeight.bold,
              ),
            ),
            Text(
              "Result: $RESULT",
              style: TextStyle(
                fontSize: 25.0,
                fontWeight: FontWeight.bold,
              ),
            ),
            Text(
              "AGE: $age",
              style: TextStyle(
                fontSize: 25.0,
                fontWeight: FontWeight.bold,
              ),
            ),
          ],
        ),
      ),
    );
  }
}
