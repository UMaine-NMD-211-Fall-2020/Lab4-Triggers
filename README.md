# Lab4-Triggers
This week's labs will deal with activating events after triggers. 
The Goal of this lab is for you to feel comfortable triggering events in processing

## To Turn IN
Code that uses 3 triggers as input, at least one from keyboard and one from mouse. 
Your code should be unique.

### WEDNESDAY LAB EXAMPLE END CODE
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

### FRIDAY LAB EXAMPLE END CODE

## Submissions
Submit your work by next lab session, via Google Drive or below.

- [Lab4-FirstName-LastName](http://example.com/)
