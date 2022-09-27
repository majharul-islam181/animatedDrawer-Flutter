# neumorphism_animation

```
A new Flutter project.
```
## Getting Started
```
import 'package:flutter/material.dart';

class Neumorphism extends StatefulWidget {
  const Neumorphism({Key? key}) : super(key: key);

  @override
  State<Neumorphism> createState() => _NeumorphismState();
}

class _NeumorphismState extends State<Neumorphism> with TickerProviderStateMixin {
  double turns = 0.0;
  bool isClicked = false;
  late AnimationController _controller ;
  Color customBlackColor = const Color.fromARGB(255, 53, 53, 53);
  Color customWhiteColor = const Color.fromARGB(255, 237, 237, 237);


  @override
  void initState(){
    _controller = AnimationController(vsync: this, duration: const Duration(microseconds: 800));
    super.initState();
  }

  @override
  void dispose(){
    _controller.dispose();
    super.dispose();
  }


  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Appbar') ,
        centerTitle: true,
        backgroundColor: Colors.white,
      ),
      body: Center(
        child: AnimatedRotation(
          duration: const Duration(seconds: 1),
          turns: turns,
          curve: Curves.easeOutExpo,
          child: GestureDetector(
            onTap: (){

              if(isClicked){
                setState(() {
                  turns -= 1/4;
                  _controller.reverse();
                });
              }else{
                setState(() {
                  turns += 1/4;
                  _controller.forward();
                });
              }
              isClicked = !isClicked;
            },
            child: AnimatedContainer(
              duration: const Duration(seconds: 1),
              curve: Curves.easeOutExpo,
              child: Container(
                decoration: BoxDecoration(
                  borderRadius: BorderRadius.circular(25.0),
                  color: customWhiteColor,
                  boxShadow: [
                    BoxShadow(
                      blurRadius: 30.0,
                      offset: isClicked ?  const Offset(20, -20): const Offset(20, 20),

                      color: Colors.grey,
                    ),
                    BoxShadow(
                      blurRadius: 30.0,
                      offset: isClicked ?  const Offset(-20, 20): const Offset(-20, -20),
                      color: Colors.white,
                    ),
                  ]
                ),
                child: SizedBox(
                  height: 150,
                  width: 150,
                  child: Center(
                    child: AnimatedIcon(
                      icon: AnimatedIcons.menu_close,
                      progress: _controller,
                      color: customBlackColor,
                      size: 100,
                    ),
                  ),
                ),

              ),
            ),
          ),
        ),
      ),
    );
  }
}
```
#
This project is a starting point for a Flutter application.




![ani1](https://user-images.githubusercontent.com/86792533/192199960-fca6ff53-0225-4cd6-8b6a-f732093da339.png)\
![ani2](https://user-images.githubusercontent.com/86792533/192199967-a7de1f3b-fffd-47fa-8da6-7769e16a8774.png)
