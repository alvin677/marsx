# MarsX
This is the official MarsX scripting documentation. <br /> MarsX uses Javascript to create game logic.


Websites recommended to learn JavaScript at:

  https://www.w3schools.com/js/ <br />
  https://www.freecodecamp.org/ <br />
  https://www.learn-js.org/ <br />

MarsX is using Three.js and a modified version of their editor.
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
```js
keydown
keyup
pointerdown
pointerup
pointermove
```

# Script variables
Certain application components are accessible in the scope of scripts as variables:
```js
player // A reference to the application player (a wrapper component which executes the editor application).
renderer // A reference to the renderer.
scene // A reference to the scene graph.
camera // A reference to the application's camera.
```

# Miscellaneous
Code outside of lifecycle and event listeners is immediately executed when the script is loaded.
The ```this``` reference can be used to refer to the 3D object which owns the script.


# Scripting Guide

It is recommended to have the Developer Console open when working in a project. There are multiple ways to open the console: `CTRL + SHIFT + I`, `CTRL + SHIFT + J` or by pressing `F12`

* Scope object:
```js
let cube = scene.getObjectByName('Box'); // Object scoping in the scene
```

* Sleep functions:
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

* User input:
```js
function init( event ) {
  window.addEventListener('keypress', (event) => {
    console.log(event.key);
  })
}
```

* Moving camera:
```js
camera.position.x = this.position.x;
camera.position.y = this.position.y;
camera.position.z = this.position.z;
camera.position.y += 20;

// or

camera.position.copy(this.position)
camera.position.y += 20;
```

* Delete objects:
```js
scene.remove(this);
// or
scene.remove(scene.getObjectByName('Box'));
```

Additional Three.js documentation can be found at: https://threejs.org/docs/

Contact me on Discord with suggestions: Cedric#0591
