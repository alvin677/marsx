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

**A list of useful Javascript keywords:**
```js
// Creating variables
let integerVariable = 10; // integer (add decimal to make float)
var boolVariable = true; // boolean
const stringVariable = "string"; // string

// Loops
for (let i = 0; i < 10; i++) {} // Loop will run 10 times, value 'i' will increase by 1 each time

// Statements
if (boolVariable) {console.log("true");}
if (10 > 5) {console.log("10 is greater than 5");}

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
```

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
console.log(scene); // This one is very basic
```
<br /><br /><br />
**Additional Three.js documentation can be found at: https://threejs.org/docs/** <br />
**Ask questions on MarsF: https://ullblocks.jonhosting.com/forums/ (currently under development)**

Contact me on Discord with suggestions: *Cedric#0591*
