This was one of my first real projects from years ago. I made it in the final half of my 8th grade year. I lost it and just now rediscovered this code, and I completely forget how it works. At the time, I was attempting to create a more straightforward game development process with JavaScript. Unfinished and I don't understand it because it has been so long, but it's nice to look back on how I've evolved as a programmer.

# 2dev.js Version 2
2dev.js is a 2D game development library I created for HTML5 Canvas. I originally started developing this library so I could create my games quickly without having to redo any of the math for collision logic. But I kept adding new functions to the library and decided to publish it. This library is very simple and is intended to make game development on an HTML5 Canvas as easy as possible.
<br/>
# Tutorial (unfinished)
### NOTE: The origin of any object's position and rotation is always the center.
### Events
```javascript
// Use 'K_' followed by the key's event.code in all caps to refer to a key
On.KeyDown(key, func, shouldPreventDefault);        // Adds a new key down event to the document body
On.KeyUp(key, func shouldPreventDefault);           // Adds a new key up event to the document body
On.MouseDown = function () {                        // Adds a new mouse down event to the document body
  // do something
}
On.MouseUp = function () {                          // Adds a new mouse up event to the document body
  // do something
}
canvas.On.KeyDown(key, func, shouldPreventDefault); // Adds a new key down event to the canvas
canvas.On.KeyUp(key, func, shouldPreventDefault);   // Adds a new key up event to the canvas
canvas.On.MouseDown = function () {                 // Adds a new mouse down event to the canvas
  // do something
}
canvas.On.MouseUp = function() {                    // Adds a new mouse up event to the canvas
  // do something
}
if (KeysPressed[key]) {                             // A variable that stores an array of the keys that are pressed
  // do something
}
if (IsMouseDown) {                                  // A variable to check if the mouse is down or up
  // do something
}
```
### Canvas Properties
```javascript
const canvas = new Canvas(width, height); // Creates a new canvas

// Canvas variables
canvas.width, canvas.height;    // Gets canvas width and height
canvas.HTML;                    // Gets the canvas DOM properties
canvas.ctx;                     // Gets the canvas 2D context, same as 'canvas.getContext("2d");'
canvas.centerX, canvas.centerY; // Gets the center x or y position on the canvas
canvas.Mouse.x, canvas.Mouse.y; // Gets the mouse position on the canvas
canvas.objects;                 // Gets an array of all objects that are currently drawn on the canvas

// Drawing functions
// Use 'C_' followed by a common color name in all caps to refer to any common colors
canvas.Fill(color);    // Fills the canvas with a solid color
canvas.Draw(objects);  // Draws any number of objects to the canvas. The first objects
                       // given will be drawn first. Any objects must be drawn to the canvas using this function
canvas.Erase(objects); // Erases any number of objects from the canvas
canvas.Clear();        // Clears the canvas
```
### Images and Audio
```javascript
// Loading image and audio files
LoadImg(images);   // Loads any number of image files
LoadSound(sounds); // Loads any number of audio files

// Accessing loaded sounds
LoadedSounds[index];       // An array storing all loaded sounds
LoadedSounds[index].audio; // A property storing the sound's HTML audio element
LoadedSounds[index].src;   // A property storing the sound's source

// Playing sounds
PlaySound(src); // Plays a sound. Make sure to load the audio
                // file using 'LoadSound()' before playing it
```
### Creating Objects
```javascript
const img = Img(src, x, y, width, height);              // Creates a new image object
const line = Line([x, y], [x, y], color);               // Creates a new line object
const polygon = Polygon([x, y], [x, y], [x, y], color); // Creates a new polygon object with any
                                                        // number of points
const rect = Rect(x, y, width, height, color);          // Creates a new rectangle object
const circle = Circle(x, y, radius, color);             // Creates a new circle object
const text = Text(text, font, fontSize, x, y, color);   // Creates a new text object
```
### Image Object Properties
```javascript
img.src = newSrc;                    // Sets the source of the image. Make sure to load
                                     // the image before drawing it to a canvas
img.x = newXPosition;                // Sets the x position of the image
img.y = newYPosition;                // Sets the y position of the image
img.width = newWidth;                // Sets the width of the image
img.height = newHeight;              // Sets the height of the image
img.opacity = newOpacity;            // Sets the opacity of the image. Opacity can be any number
                                     // from 0 to 100
img.velocityX = newVelocityX;        // Sets the x velocity of the image. This value
                                     // is added to the image's x position every frame
img.velocityY = newVelocityY;        // Sets the y velocity of the image. This value
                                     // is added to the image's y position every frame
img.gravityXStrength = newXStrength; // Sets the x gravity strength of the image. This value is
                                     // added to the image's x velocity every frame if x gravity
                                     // is enabled
img.gravityYStrength = newYStrength; // Sets the y gravity strength of the image. This value is
                                     // added to the image's y velocity every frame if y gravity
                                     // is enabled
img.gravityXEnabled = true|false;    // Enables or disables x gravity
img.graivtyYEnabled = true|false;    // Enables or disables y gravity
img.rotation = newRotation;          // Sets the rotation of an image. This number is always in degrees
img.borderWidth = newWidth;          // Sets the width of the image's border in pixels
img.borderColor = newColor;          // Sets the color of the image's border
img.showBorder = true|false;         // Shows or hides the image's border
img.SetBorder(width, color);         // Sets the image's border width and color and it shows the border
img.SetPosition(x, y);               // Sets the image's x and y position
img.GlideTo(x, y, timeInMs);         // Moves the image to a point over x milliseconds
img.PointTowards(x, y);              // Rotates the image towards a specific point
img.On.MouseDown = function () {     // Sets the mouse down event for the image
  // do something
}
img.On.MouseUp = function () {       // Sets the mouse up event for the image
  // do something
}
```
### Line Object Properties
```javascript
line.point1, line.point2;         // Access the start and end points of the line. The functions
                                  // for both points are the same

// Line Properties
line.midPoint.x, line.midPoint.y; // Gets the middle x or y position of the line
line.length;                      // Gets the length of the line
line.angle;                       // Gets the angle of the line
line.color = newColor;            // Sets the color of the line
line.lineWidth = newLineWidth;    // Sets the line width of the line
line.opacity = newOpacity;        // Sets the opacity of the line. This can be any number
                                  // from 0 to 100
line.On.MouseDown = function () { // Sets the mouse down event for the line
  // do something
}
line.On.MouseUp = function () {   // Sets the mouse up event for the line
  // do something
}

// Point Properties
line.(point1|point2).x = newX;                        // Sets the x position of the point
line.(point1|point2).y = newY;                        // Sets the y position of the point
line.(point1|point2).velocityX = newVelocityX         // Sets the x velocity of the point. This value is added
                                                      // to the x position every frame
line.(point1|point2).velocityY = newVelocityY         // Sets the y velocity of the point. This value is added
                                                      // to the y position every frame
line.(point1|point2).gravityXStrength = newXStrength; // Sets the gravity x strength of the point. This value is
                                                      // is added to the x velocity every frame if x gravity is
                                                      // enabled
line.(point1|point2).gravityYStrength = newYStrength; // Sets the gravity y strength of the point. This value is
                                                      // is added to the y velocity every frame if y gravity is
                                                      // enabled
line.(point1|point2).gravityXEnabled = true|false;    // Enable or disable x gravity
line.(point1|point2).gravityYEnabled = true|false;    // Enable or disable y gravity
line.(point1|point2).SetPosition(x, y);               // Sets the x and y position of the point
line.(point1|point2).GlideTo(x, y, timeInMs);         // Moves the point to another point over x milliseconds
```
### Polygons
```javascript
polygon.x = newX;                 // Sets the polygon's x position
polygon.y = newY;                 // Sets the polygon's y position
polygon.SetPosition(x, y);        // Sets the polygon's x and y position
polygon.GlideTo(x, y, timeInMs);  // Moves the polygon to an x and y position over
                                  // x milliseconds
polygon.color = newColor;         // Sets the color of the polygon
polygon.opacity = newOpacity;     // Sets the opacity of the polygon. This can be any number from
                                  // 0 to 100
polygon.stroke = true|false;      // Determines if the polygon should be filled or stroked
polygon.lineWidth = newLineWidth; // Sets the polygon's line width

polygon.rotation = newRotation;   // Sets the polygon's rotation
polygon.PointTowards(x, y);       // Rotates the polygon towards a point

polygon.borderWidth = newBorderWidth // Sets the polygon's border width
polygon.borderColor = newborderColor // Sets the polygon's border color
polygon.showBorder = true|false;     // Shows or hides the polygon's border
polygon.SetBorder(width, color);     // Sets the polygon's border width and color,
                                     // and shows the polygon's border if hidden

polygon.points[index]; // Array that stores all of the points of the polygon
polygon.sides[index];  // Array that stores all of the sides of the polygon as lines

polygon.points[index].SetX(x);               // Sets the x position of the point
polygon.points[index].SetY(y);               // Sets the y position of the point
polygon.points[index].SetPosition(x, y);     // Sets the x and y position of the point
polygon.points[index].SetOffsetX(x);         // Sets the x position offset of the point
                                             // from the center of the polygon
polygon.points[index].SetOffsetY(y);         // Sets the y position offset of the point
                                             // from the center of the polygon
polygon.points[index].SetOffset(x, y);       // Sets the x and y position offset of the point
                                             // from the center of the polygon
polygon.points[index].GlideTo(x, y, timeInMs // Moves the point to an x and y position over
                                             // x milliseconds

polygon.velocityX = newVelocityX // Sets the x velocity of the polygon. This number is
                                 // added to the x position of the polygon every frame
polygon.velocityY = newVelocityY // Sets the y velocity of the polygon. This number is
                                 // added to the y position of the polygon every frame

polygon.gravityXStrength = newXStrength; // Sets the x gravity strength of the polygon. This value is
                                         // added to the polygon's x velocity every frame if x gravity
                                         // is enabled
polygon.gravityYStrength = newYStrength; // Sets the y gravity strength of the polygon. This value is
                                         // added to the polygon's y velocity every frame if y gravity
                                         // is enabled
polygon.gravityXEnabled = true|false;    // Enables or disables x gravity
polygon.graivtyYEnabled = true|false;    // Enables or disables y gravity

polygon.On.MouseDown = function () { // Sets the polygon's mouse down event
  // do something
}
polygon.On.MouseUp = function () {   // Sets the polygon's mouse up event
  // do something
}
```
### Rectangles
### Circles
### Text
### Collision Detection
```javascript
IsColliding(object1, object2); // Use the 'IsColliding()' function to detect
                               // collision between any 2 objects (except text objects)
```
### Other Functions
```javascript
// Loops
const loop = Loop(function () { // Runs a function every x milliseconds, or
  // do something               // every frame if timeInMs is undefined
}, timeInMs);
loop.ClearLoop();               // Stops the loop

// The 'Repeat()' Function
const repeat = Repeat(function () { // Runs a function x number of times
  // do something
}, num);
repeat.Stop();                      // Stops running the function

// The 'After' Function
After(timeInMs, function () { // Runs a function after x milliseconds
  // do something
});

// Random Numbers
RandomNum(minimum, maximum); // Gets a random number between 2 values
RandomInt(minimum, maximum); // Gets a random integer between 2 values

// Math Functions
GetDistance([x, y], [x, y]);                 // Gets the distance between 2 points using the
                                             // Pythagorean theorem
GetMidPoint([x, y], [x, y]);                 // Gets the middle position of 2 points
GetAngle([x, y], [x, y]);                    // Gets the angle of a line. The first parameter 
                                             // is the middle point of the line. The second is one of the
                                             // points of the line
DegreesToRadians(degrees);                   // Converts degrees to radians
RadiansToDegrees(radians);                   // Converts radians to degrees
GetRotatedPosition([x, y], [x, y], degrees); // Gets the rotated position of a point
                                             // around another point. The first parameter is the origin,
                                             // and the second is the point to be rotated
```
