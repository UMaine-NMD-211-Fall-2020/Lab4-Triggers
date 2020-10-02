# Lab4-Triggers
This week's labs will deal with activating events after triggers. 
The Goal of this lab is for you to feel comfortable triggering events in processing

## To Turn IN
Code that uses 3 triggers as input, at least one from keyboard and one from mouse. 
Your code should be unique.

### WEDNESDAY LAB EXAMPLE END CODE
Contains an event triggered by a mouse, an event triggered by a key press, and an event triggered by hovering over and clicking on a certain color. 
```processing
/* 
Lab 4 - NMD 211
FirstName LastName
September 30, 2020

Trigger Lab
- 3 separate types of triggered events
  - One needs to be on a key press
  - One needs to be using the mouse
*/

int outputInt = 0;

color c;

int[] ellipseXY = { 250, 125};

int[] redCircleColors = {    255, 0};
int[] greenCircleColors = {  0,   255};
int[] blueCircleColors = {   0,   255};

void setup(){
  size( 500, 500 ) ;    // drawing space size
  
  // 
  noStroke() ;          // no outlines
  ellipseMode(CENTER);  // ellipses -> x, y, w, h
} // --- END SETUP

void draw(){
  background( 0 );      // black background
  
  // color changing Circle - on mouse click
  toggleCircleColor();
  fill(    redCircleColors[outputInt]   , 
           greenCircleColors[outputInt] ,
           blueCircleColors[outputInt]  );          // circle color - r, g, b
  ellipse( width/2, height/2, 100, 100);    // draw circle


  // moving ellipse on key press
   movingEllipse();
   
   // if your mouse hovers over teal, sound happens
   c = get( mouseX, mouseY);
   println(c == -16711681);
   if (c == -16711681){ // if mouse over teal
     // play sound
     background( 255, 0, 255);
   }
   
} // --- END DRAW

/* HELPER FUNCTION */
void toggleCircleColor(){
  // if mouse is pressed, teal
  if (mousePressed == true){
    outputInt = 1;
  }
  // else, red
  else {
    outputInt = 0;
  } 
} // --- END Toggle Circle Color

void movingEllipse(){
  fill ( 255, 255, 0, 200);                 // yellow seethrough
  ellipse(   ellipseXY[0], 
             ellipseXY[1], 
             100, 10);     // ellipse 
  
  if (keyPressed){
    if (key == 'w'){                        // if press w, move up
      ellipseXY[1] -= 1;                    // change y by -1 
      //println("YES - W");
    }
    if (key == 'a'){                        // if press a, move left
      ellipseXY[0] -= 1;
      //println("YES - A");
    }
    if (key == 'd'){                        // if press d, move right
      ellipseXY[0] += 1;
    }
    if (key == 's'){                        // if press s, move down
      ellipseXY[1] += 1; 
    }
  }
  else{
    println();
  }
}
```
### FRIDAY LAB EXAMPLE END CODE
Contains an event triggered by a mouse, an event triggered by a key press, and an event triggered by hovering over and clicking on a certain color. 
Also contains a loaded image. 


To run this code, you will need to download an image. 
Therefore, you can download my github repo here and run the code from this, or you can just see how the file is setup by reading the repo.  
```processing
/*   
 Lab 4 - NMD 211 
 FirstName LastName
 October 2, 2020
 
 Trigger Lab
 Make 3 Triggered event
 - Key Press
 - Mouse Activated
 - If over certain color and mouse clicked
 
 Spyro Image: https://vignette.wikia.nocookie.net/deathbattlefanon/images/3/33/Spyro_in_Spyro_Reignited_Trilogy.png/revision/latest?cb=20180405154517
 */
float ellipseX = 100;                                       // starting x of floating ellipse x
float ellipseY = 100;                                       // starting y of floating ellipse y

int stepSize = 1;                                           // how many spaces ellipse moves at a time

color mouseOverColor ;                                      // color mouse is hovering over
color targetColor = -51456;                                 // trigger color, -51456 , color of red circle over yellow 

PImage spyro;                                               // identifier for input image

void setup() {
  size( 500, 500);                                          // canvas size

  // Modes
  ellipseMode( CENTER );
  imageMode(CENTER);

  // Stroke
  noStroke();

  // Imaage
  spyro = loadImage("Spyro_in_Spyro_Reignited_Trilogy.png");   // image file to load
  spyro.resize(width/2, 0);                                    // spiro is a third of the page
  
} // -- END Setup

void draw() {
  background( 0, 0, 0);

  /* Mouse Pressed Example
   if press mouse, red circle appears on top of yellow circle
   */
  if (mousePressed == true ) {
    fill(255, 255, 0);                                       // yellow
    ellipse( width/2, height/2, 7*width/10, 7*height/10);   // ellipse dependent on canvas size

    fill(255, 0, 0, 200);                                    // red
    ellipse( width/2, height/2, 4*width/5, 4*height/5);      // ellipse dependent on canvas size
  } else { 
    fill(255, 255, 0);                                      // yellow
    ellipse( width/2, height/2, 7*width/10, 7*height/10);   // ellipse dependent on canvas size
  }

  /* Key Input Example 
   move something up, down, left right
     w - up
     s - down
     a - left
     d - right
   */
  fill( 0, 255, 255, 200);                                   // cyan
  ellipse( ellipseX, ellipseY, 100, 20);                     // ellipse to move

  if (keyPressed) {
    if (key == 'w' ) {
      ellipseY -= stepSize;
      println("key:", key, "| y:", ellipseY );
    }
    if (key == 's' ) {
      ellipseY += stepSize;
      println("key:", key, "| y:", ellipseY );
    }
    if (key == 'a' ) {
      ellipseX -= stepSize;
      println("key:", key, "| x:", ellipseX );
    }
    if (key == 'd' ) {
      ellipseX += stepSize;
      println("key:", key, "| x:", ellipseX );
    }
  } else {
    println("");
  }
  /* Pixel Color Trigger 
   - if mouse over color & mouse pressed 
   background turns magenta
   */
  mouseOverColor = get(mouseX, mouseY);  // color under mouse
  println( mouseOverColor );
  if (mouseOverColor == targetColor ) {
    //background(255, 0, 255);
    image( spyro, width/2, height/2);
  }
} // - END Draw
```

## Submissions
Submit your work by next lab session, via Google Drive or below.

- [Lab4-FirstName-LastName](http://example.com/)
