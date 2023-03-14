# MarsX
This is the official MarsX scripting documentation. MarsX uses Javascript to create game logic.


**Websites recommended to learn JavaScript at:**

  https://www.w3schools.com/js/ <br />
  https://www.freecodecamp.org/ <br />
  https://www.learn-js.org/ <br />

MarsX is using Three.js and our modified version of their editor.
Everything possible with Three.js is possible in the MarsX editor.
Credit to the Three.js community.

# Lifecycle methods
```js
function update(event) {} // Executed right before a frame is going to be rendered. Its primary purpose is to update the state of the 3D object which owns the script. The method has an event parameter which holds a time and delta property. time represents the elapsed time in milliseconds and delta represents the time between two frames in milliseconds.
function init() {} // Executed once after the application has been loaded.
function start() {} // Executed once when the application is ready to start rendering.
function stop() {} // Executed once when the application is stopped.
```

# Events
It is also possible to implement event listeners for selected browser events. The following events are supported by the editor:
* keydown
* keyup
* pointerdown
* pointerup
* pointermove

# Script variables
Certain application components are accessible in the scope of scripts as variables: <br />
`player` A reference to the application player (a wrapper component which executes the editor application). <br />
`renderer` A reference to the renderer. <br />
`scene` A reference to the scene graph. <br />
`camera` A reference to the application's camera.

# Miscellaneous
Code outside of lifecycle and event listeners is immediately executed when the script is loaded. <br />
The ```this``` reference can be used to refer to the 3D object which owns the script.

<br /><br /><br /><br /><br />
# Scripting Guide

It is recommended to have the Developer Console open when working in a project. <br /> There are multiple ways to open the console: `CTRL + SHIFT + I`, `CTRL + SHIFT + J` or by pressing `F12`

**A list of useful Javascript keywords/code:**
```js
// Creating variables
let integerVariable = 10; // integer (add decimal to make float)
var boolVariable = true; // boolean
const stringVariable = "string"; // string
integerVariable += 10; // add 10 to the variable
integerVariable -= 10; // remove 10 from the variable
stringVariable += 'c'; // This would have added the character 'c', however, the variable is a constant (use let/var instead).

// Debugging/logging
console.log(integerVariable); // output: 10
console.log(integerVariable + 10) // output: 20
console.alert("warning");

// Loops (the 'i' stands for index)
for (let i = 0; i < 10; i++) {} // Loop will run 10 times, value 'i' will increase by 1 each time
while (true) {} // While loops tend to freeze the application as they execute as fast and much as they can.

// Statements
if (boolVariable) {console.log("true");}
if (10 > 5) {console.log("10 is greater than 5");}
else if ("word" == "word") {}
else {console.log("else");}

switch (2) { // Put expression where the '2' is. (could be a variable)
case 1:
  console.log(1);
  break;
case 2:
  console.log("this piece will execute");
  break
default:
  console.alert("Hello World!");
}

// Datatype conversion
parseInt(stringVariable); // Convert string to int
integerVariable.toString(); // Convert int to string

// Math
Math.floor(Math.random() * 100); // Retrieve random number between 0 and 100 without any decimals
Math.PI // Pi (3.1415..)
Math.sin, Math.tan, Math.cos, Math.asin, Math.atan, Math.acos; // Trigonometry

console.log(1+1); // Addition
console.log(1-1); // Subtraction
console.log(1*1); // Multiplication
console.log(1/1); // Division
console.log(1%1); // Remainder


// Functions
function test() {
  console.log("test");
}
test(); // output: "test"

function test(text) {
  console.log(text);
}
test("hello"); // output: "hello"

function test(text) {
  return text;
}
test("hello"); // output: nothing, instead:
console.log(test("hello")); // output: "hello"


// Stop code
return;
break;

// Try catch (useful when you don't want your program to stop running if it encounters an error)
try {console.log("success");} // Tries to execute the code, if it fails, then code in the 'catch' will be executed.
catch (error) {console.log(error);} // Code inside 'try' somehow failed. (put nothing inside {} if you don't want it to do anything on fail)

// Array
let array = [100, 50, 20];
console.log(array[1]); // output: 50, index starts at 0

for (let i = 0; i < array.length; i++) {console.log(array[i]); // output: 100 50 20
```
It is also recommended that you learn about JSON in Javascript, structure and how to use it.

**Scope object:**
```js
let cube = scene.getObjectByName('Box'); // Object scoping in the scene
```

**Sleep functions:**
```js

// Sync sleep function
function sleep(ms) {
  var start = new Date().getTime(), expire = start + ms;
  while (new Date().getTime() < expire) {}
  return;
}

sleep(2000); // example


// Async sleep function
function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

await sleep(2000); // example
```

**User input:**
```js
function init( event ) {
  window.addEventListener('keypress', (event) => {
    console.log(event.key);
  })
}
```

**Moving camera:**
```js
camera.position.x = this.position.x;
camera.position.y = this.position.y;
camera.position.z = this.position.z;
camera.position.y += 20;

// or

camera.position.copy(this.position)
camera.position.y += 20;
```

**Delete objects:**
```js
scene.remove(this);
// or
scene.remove(scene.getObjectByName('Box'));
```

**Log objects:**
```js
for (let i = 0; i < scene.children.length; i++) {
  console.log(scene.children[i]); // Logs every object created
}
```
<br /><br /><br />
**Additional Three.js documentation can be found at: https://threejs.org/docs/** <br />
**Ask questions on MarsF: https://ullblocks.jonhosting.com/forums/ (currently under development)**

Contact me on Discord with suggestions (or open an issue): *Cedric#0591*
