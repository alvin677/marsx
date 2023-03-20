# MarsX
This is the official MarsX scripting documentation. MarsX uses Javascript to create game logic.<br />You may use `CTRL + F` to search on this documentation. 

**Websites recommended to learn JavaScript at:**

  https://www.w3schools.com/js/ <br />
  https://www.freecodecamp.org/ <br />
  https://www.learn-js.org/ <br />
  
  https://codepen.io/ for tons of code examples
  
  Also recommended to use https://chat.openai.com/ with specific questions, you could refer to the words 'Three.js editor' when asking questions for better answers.

MarsX is using Three.js and our modified version of their editor.
Everything possible with Three.js is possible in the MarsX editor.
Built in to the MarsX editor is also cannon.js.
<br />Credit to the Three.js and cannon.js developers/community.

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
`player` A reference to the application player (a wrapper component which executes the editor application).<br />
`renderer` A reference to the renderer.<br />
`scene` A reference to the scene graph.<br />
`camera` A reference to the application's camera.<br />

`THREE` A reference to the three.js library.<br />
`world` A reference to the cannon.js world.<br />
`two` A reference to the two.js canvas.

`editor` A reference to the editor, used in the web console (F12).

# Miscellaneous
Code outside of lifecycle and event listeners is immediately executed when the script is loaded. <br />
The ```this``` reference can be used to refer to the 3D object which owns the script. <br />
To refer to the physical body, you may use `this.body`.

<br /><br /><br /><br /><br />
# Scripting Guide

It is recommended to have the Developer Console open when working on a project. <br /> There are multiple ways to open the console: `CTRL + SHIFT + I`, `CTRL + SHIFT + J` or by pressing `F12`

**A list of useful Javascript keywords/code:**
```js
// Creating variables
globalVariable = null; // create a global variable, can be modified later
let integerVariable = 10; // integer (add decimal to make float)
var boolVariable = true; // boolean
const stringVariable = "string"; // string
integerVariable += 10; // add 10 to the variable
integerVariable -= 10; // remove 10 from the variable
stringVariable += 'c'; // This would have added the character 'c', however, the variable is a constant (use let/var instead).
boolVariable = !boolVariable; // This will switch the bool from true to false, and false to true whenever executed. ! stands for 'not'

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
else if ("word" == "word") {} // == stands for 'equal to'
else {console.log("else");}

if (variable1 != variable2) {} // != stands for 'not equal to'
if (variable1 >= variable2) {} // >= or <= stands for 'greater or equal to' or 'less or equal to'
if (variable1 || variable2) {} // || stands for 'or'
if variable1 && variable2) {} // && stands for 'and'

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

eval(10+20); // output: 30, eval() can be used to calculate any expression

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

// Comments

// This is a comment
/* This is
a multiline
comment*/

// String

let example = "this is a string";
let example2 = 'this is a string';
let example3 = `this is also a string`;

let age = 30;
console.log(`Age is: ${age}`); // Using the ` to make strings, you can easily pass in variables
// instead of
console.log("Age is: "+age);

console.log("\n"); // The \n makes a 'new line', it can be put anywhere in a string

// Input
let input = prompt("Enter number: ");
let ok = confirm("Do you agree?");
if (ok) {/* code */} // if 'ok' is 'true', then the code inside the curly brackets will execute

```
It is also recommended that you learn about JSON in Javascript, structure and how to use it.

**Scope object:**
```js
let cube = scene.getObjectByName('Box'); // Object scoping in the scene, target another object
```

**Sleep functions:**
```js

// Sync sleep function
function sleep(ms) {
  var start = Date.now(), expire = start + ms;
  while (Date.now() < expire) {}
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

**Moving camera or other objects:**
```js
camera.position.x = this.position.x;
camera.position.y = this.position.y;
camera.position.z = this.position.z;
camera.position.y += 20;

// or

camera.position.copy(this.position);
camera.position.y += 20;

// or

camera.position.set(10, 10, 10);
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

**Information about current object:**
```js
console.log(this); // Very simple, will output everything about the object that the script created on.
```

**Rotate object:**
```js
this.rotation.x += 0.01; // In radians
```

**Clone object:**
```js
let objectClone = this.clone(); // Define clone variable as a clone of 'this' object
objectClone.position.copy(this.position); // Set position to 'this' position
scene.add(objectClone); // Add clone to the scene
```

**Change object color:**
```js
this.material.color.setRGB(0, 255, 0);

// or

this.material.color.g = 255;
```

**Switching camera:**
```js
player.setCamera(this); // 'this' can be replaced with something such as scene.getObjectByName('newCamera');
```

**Create object:**
```js
// Create a new box geometry
var geometry = new THREE.BoxGeometry( 1, 1, 1 );

// Create a new material
var material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );

// Create a new mesh with the geometry and material
var cube = new THREE.Mesh( geometry, material );

// Set the position of the cube
cube.position.set( 0, 0, 0 );

// Add the cube to the scene
scene.add( cube );
```
<br /><br /><br /><br /><br />
# Examples
**Smooth movement example, try it on a cube, capsule or similar:**
```js
let keysDown={}; // Array with pressed down keys

function keyDown(e){ keysDown[e.key]=true; } // Function to set key to true if it's held down
function keyUp(e){ delete keysDown[e.key]; } // Function to delete key from array if it's released
window.addEventListener( 'keydown', keyDown, false ); // Event listener to detect if a key is down
window.addEventListener( 'keyup', keyUp, false ); // Event listener to detect if a key is released

function update( event ) { // Main loop
	if (keysDown['a']) {this.position.x -= 0.1;} // Move left if 'a' is held down
	if (keysDown['d']) {this.position.x += 0.1;} // Move right if 'd' is held down
	if (keysDown['w']) {this.position.z -= 0.1;} // Move forward if 'w' is held down
	if (keysDown['s']) {this.position.z += 0.1;} // Move backward if 's' is held down
	
	camera.position.copy(this.position); // Set camera to 'this' object's position
	camera.position.y += 15; // Add offset on 'y' axis
	camera.position.z += 15; // Add offset on 'z' axis
	camera.rotation.set(-0.75, 0, 0); // Set correct camera rotation
}
```

**Collision detection:**
```js
function update( event ) { // Main loop
	const box1 = new THREE.Box3().setFromObject(this); // Create collision boxes, required to be in the loop or they won't update
	const box2 = new THREE.Box3().setFromObject(scene.getObjectByName('Plane')); // This could be any object, in this case, it's the floor
	
	if (box1.intersectsBox(box2)) { // Check if they collide
  		console.log("collides"); // Do code
	}
	
	this.position.y += 0.01; // Move 'this' object up 
}
```

**Adding simple gravity:**
```js
const box1 = new THREE.Box3().setFromObject(this); // Create collision boxes
const box2 = new THREE.Box3().setFromObject(scene.getObjectByName('Plane')); // This could be any object, in this case, it's the floor
	
if (!box1.intersectsBox(box2)) { // Check if they collide
  	this.position.y -= 0.5;
}
```

**Object velocity and jumping:**
```js
let keysDown={}; // Array with pressed down keys
let yVel = 0; // Assign y-axis velocity variable
let jumping = false; // Jumping state boolean

function keyDown(e){ keysDown[e.key]=true; } // Function to set key to true if it's held down
function keyUp(e){ delete keysDown[e.key]; } // Function to delete key from array if it's released
window.addEventListener( 'keydown', keyDown, false ); // Event listener to detect if a key is down
window.addEventListener( 'keyup', keyUp, false ); // Event listener to detect if a key is released

function update( event ) { // Main loop
	const box1 = new THREE.Box3().setFromObject(this); // Create collision boxes
	const box2 = new THREE.Box3().setFromObject(scene.getObjectByName('Plane')); // This could be any object, in this case, it's the floor
	
	if (box1.intersectsBox(box2) && !jumping) { // If NOT jumping and touching 'Plane'
		yVel = 0; // Set velocity to 0
	}
	else if (!box1.intersectsBox(box2)) { // If not colliding with the ground
  		yVel -= 0.01; // Add negative value to the velocity, will cause 'this' object to fall
	}
	this.position.y += yVel; // Set 'this' object's position to the velocity
	if (box1.intersectsBox(box2) && keysDown[' ']) {yVel += 0.1; jumping = true;} // Jumping, only works if you're touching the ground
	else {jumping = false;} // Change the jumping state boolean to false if you're not jumping anymore
	if (keysDown['a']) {this.position.x -= 0.1;} // Move left if 'a' is held down
	if (keysDown['d']) {this.position.x += 0.1;} // Move right if 'd' is held down
	if (keysDown['w']) {this.position.z -= 0.1;} // Move forward if 'w' is held down
	if (keysDown['s']) {this.position.z += 0.1;} // Move backward if 's' is held down
	
	camera.position.copy(this.position); // Set camera to 'this' object's position
	camera.position.y += 15; // Add offset on 'y' axis
	camera.position.z += 15; // Add offset on 'z' axis
	camera.rotation.set(-0.75, 0, 0); // Set correct camera rotation
}
```

**Velocity:**
```js
let yVelocity = 0; // Define velocity variable

function update(event) {
yVelocity -= 0.01; // Add negative velocity, cause object to fall
this.position.y += yVelocity; // Apply/update velocity to object's position (y)
```

**2.5D camera angle:**
```js
function update( event ) {
	camera.position.copy(this.position);
	camera.position.x += 80;
	camera.rotation.set(0, Math.PI/2, 0);
}
```
<br /><br /><br /><br /><br />
# Addons
**Three.js Github Addons:** https://github.com/mrdoob/three.js/tree/dev/examples/jsm <br />
**CDN (must be 0.147.0 or below):** https://cdn.jsdelivr.net/npm/three@0.147.0/examples/js/ <br />
**Great websites for additional javascript cdn:** https://cdnjs.com/ and https://www.jsdelivr.com/

**Import and use a Three.js example addon (PointerLockControls.js in this example):**
```js
function loadControls() { // Function
  const controls = new THREE.PointerLockControls(camera, document.body); // Addon code inside this function, in this case defining 'controls'
  controls.lock(); // Locking cursor
}

const controlsScript = document.createElement('script'); // Make script to import addon
controlsScript.src = 'https://cdn.jsdelivr.net/npm/three@0.147.0/examples/js/controls/PointerLockControls.js'; // Importing addon
controlsScript.onload = loadControls; // Make sure it executes our code after successfully loading
document.head.appendChild(controlsScript); // Add the script element to the document head (finishing initialization)

function stop() {
	controlsScript.remove(); // Getting rid of addon after stopped playing
}
```
**Cannon.js physics with three.js:**<br />
*This example imports the cannon.js library, however, MarsX automatically imports it into the editor now. The importing step of this example is unnecessary.**
```js
const boxes = []; // Three.js boxes
const boxBodies = []; // Cannon.js bodies

function loadCannon() { // Function
	const world = new CANNON.World(); // Define cannon.js world
	world.gravity.set(0, -9.82, 0); // Set world gravity -9.82m/s
	
	const platformGeometry = new THREE.BoxGeometry(10, 0.5, 10);
	const platformMaterial = new THREE.MeshPhongMaterial({ color: 0xffffff });
	const platform = new THREE.Mesh(platformGeometry, platformMaterial);
	scene.add(platform); // Creating the platform and adding it to the scene

	const platformShape = new CANNON.Box(new CANNON.Vec3(5, 0.25, 5));
	const platformBody = new CANNON.Body({ mass: 0 });
	platformBody.addShape(platformShape);
	world.addBody(platformBody); // Creating the body of the platform
	
	const boxGeometry = new THREE.BoxGeometry(1, 1, 1);
	const boxMaterial = new THREE.MeshPhongMaterial({ color: 0xff0000 });
	// Creating box base
	
	// Creating 100 boxes
	for (let i = 0; i < 100; i++) {
  		const box = new THREE.Mesh(boxGeometry, boxMaterial);
  		box.position.set(Math.random() * 8 - 4, 5 + i * 2, Math.random() * 8 - 4);
  		scene.add(box);
  		boxes.push(box);

  		const boxShape = new CANNON.Box(new CANNON.Vec3(0.5, 0.5, 0.5));
  		const boxBody = new CANNON.Body({ mass: 1 });
  		boxBody.addShape(boxShape);
  		boxBody.position.copy(box.position);
  		boxBodies.push(boxBody);
  		world.addBody(boxBody);
	}
	
	// Creating light
	const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
	scene.add(ambientLight);

	const directionalLight = new THREE.DirectionalLight(0xffffff, 0.5);
	directionalLight.position.set(10, 20, 10);
	scene.add(directionalLight);
	
	// Animate function
	function animate() {
  		requestAnimationFrame(animate);

  		world.step(1 / 60);

		// Updating boxes
  		for (let i = 0; i < boxes.length; i++) {
    		boxes[i].position.copy(boxBodies[i].position);
    		boxes[i].quaternion.copy(boxBodies[i].quaternion);
  		}

  		renderer.render(scene, camera);
	}

	animate();
	
	
	
	// Clean up function
	loadCannon.stop = function() {
        // remove boxes from scene
        for (let i = 0; i < boxes.length; i++) {
            scene.remove(boxes[i]);
        }
        // remove box bodies from world
        for (let i = 0; i < boxBodies.length; i++) {
            world.remove(boxBodies[i]);
        }
        // reset boxes and boxBodies arrays
        boxes.length = 0;
        boxBodies.length = 0;
    }
}

function stop() { // When the program stops, call the clean up function
	loadCannon.stop();
}

const cannonScript = document.createElement('script'); // Make script to import addon
cannonScript.src = 'https://cdnjs.cloudflare.com/ajax/libs/cannon.js/0.6.2/cannon.min.js'; // Importing addon
cannonScript.onload = loadCannon; // Make sure it executes our code after successfully loading
document.head.appendChild(cannonScript); // Add the script element to the document head (finishing initialization)
```
<br /><br /><br /><br /><br />
# Physics
For physics we are using cannon.js. More information about cannon.js and what's possible can be found at: https://github.com/schteppe/cannon.js

**Apply physics to project, put in 'scene' script or add the physics directly through the Toolbox:** <br />
*Important notice: In the `User data` of each object, you can enter 2 parameters (not mandatory, default would be anchored set to false and mass set to 1):  `anchored` and `mass` of the object! <br />Example 1: `{
  "anchored": true,
  "mass": 10000
}` Example 2: `{}`* <br />*Remember that objects such as platforms want a high mass to prevent objects from clipping through.*<br />`world` is a global variable to refer to the cannon.js world and `this.body` can be used to refer to the current object's physical cannon.js body
```js
world.broadphase = new CANNON.NaiveBroadphase();
let bodies = [];

scene.children.forEach(object => {
  if (!object.geometry) return;

  let shape;
  if (object.geometry.type === "BoxGeometry") {
    const box3 = new THREE.Box3().setFromObject(object);
    const size = box3.getSize(new THREE.Vector3());
    const halfWidth = size.x / 2;
    const halfHeight = size.y / 2;
    const halfDepth = size.z / 2;
    shape = new CANNON.Box(new CANNON.Vec3(halfWidth, halfHeight, halfDepth));
    if (object.rotation) {
      const rot = new THREE.Euler().setFromQuaternion(object.quaternion);
      const halfSize = new THREE.Vector3(halfWidth, halfHeight, halfDepth);
      halfSize.applyEuler(rot);
      shape = new CANNON.Box(new CANNON.Vec3(halfSize.x, halfSize.y, halfSize.z));
    }
  } else if (object.geometry.type === "SphereGeometry") {
    const radius = object.geometry.parameters.radius;
    shape = new CANNON.Sphere(radius);
    if (object.scale) shape.radius *= Math.max(object.scale.x, object.scale.y, object.scale.z);
  } else if (object.geometry.type === "CylinderGeometry") {
  const radiusTop = object.geometry.parameters.radiusTop;
  const radiusBottom = object.geometry.parameters.radiusBottom;
  const height = object.geometry.parameters.height;

  object.updateMatrixWorld();
  const boundingBox = new THREE.Box3().setFromObject(object);
  const size = boundingBox.getSize(new THREE.Vector3());
  const scaleFactor = Math.max(...object.scale.toArray());
  const halfHeight = height / 2 * scaleFactor;
  const radius = Math.max(radiusTop, radiusBottom) * scaleFactor;
  
  shape = new CANNON.Cylinder(radius, radius, halfHeight, 16);
  const quat = new CANNON.Quaternion();
  quat.setFromAxisAngle(new CANNON.Vec3(1, 0, 0), -Math.PI / 2);
  shape.transformAllPoints(new CANNON.Vec3(), quat);

  if (object.scale) {
    shape.radiusTop *= scaleFactor;
    shape.radiusBottom *= scaleFactor;
    shape.height *= scaleFactor;
  }

} else {
    console.warn("Unsupported geometry type:", object.geometry.type);
    return;
  }

  let mass = 1;
  if (typeof object.userData["mass"] !== "undefined") mass = object.userData["mass"];
  const body = new CANNON.Body({mass});
  if (shape.type === CANNON.Shape.types.CYLINDER) shape.centerOfMass = new CANNON.Vec3(0, -shape.height / 2, 0);
  body.addShape(shape);
  body.position.copy(object.position);
  body.quaternion.copy(object.quaternion);
  world.addBody(body);
  bodies.push(body);
  object.body = body;

  if (object.userData["anchored"] == true) {
    body.mass = 1e9;
    body.type = CANNON.Body.STATIC;
  }
	
    function update() {
        if (object.userData !== "anchored") {
            object.position.copy(body.position);
            object.quaternion.copy(body.quaternion);
        }
        requestAnimationFrame(update);
    }
    update();
});

function stop() {
  for (let i = 0; i < bodies.length; i++) {
    world.remove(bodies[i]);
  }
  bodies = [];
}
```

**Applying force on an object's physical body:**
*`this.body` can be used to refer to the cannon.js body of the object.*
```js
let keysDown = {}; // Array with pressed down keys

// Creating the force and point variables to apply on the body of the object: 'this.body'
var force = new CANNON.Vec3(0, 3000, 0); // The force is in the negative y-direction
var point = new CANNON.Vec3(0, 0, 0); // Apply the force at the center of the body

function keyDown(e) {
  keysDown[e.key] = true;
} // Function to set key to true if it's held down
function keyUp(e) {
  delete keysDown[e.key];
} // Function to delete key from array if it's released
window.addEventListener("keydown", keyDown, false); // Event listener to detect if a key is down
window.addEventListener("keyup", keyUp, false); // Event listener to detect if a key is released

function update(event) {
  if (keysDown[" "]) { // If Spacebar is pressed
    this.body.applyForce(force, point); // Applying force upwards
  } 

  camera.position.copy(this.body.position); // Set camera to body's position
  camera.position.z += 40; // Add offset on 'z' axis
  camera.rotation.set(0, 0, 0); // Set correct camera rotation
}
```
<br /><br /><br /><br /><br />
# User Interface/2D
We are using two.js to draw user interface/2 dimensional elements. For more information about two.js and what's possible with it, check here: https://github.com/jonobr1/two.js/ <br />
`two` is a global variable to interact with the two.js library.

**Create a rotating rectangle:**
```js
var rect = two.makeRectangle(two.width / 2, two.height / 2, 50 ,50);
function update() {
  rect.rotation += 0.01;
}
```

**Change color:**
```js
var rect = two.makeRectangle(100, 100, 50, 50);
rect.fill = 'rgb(255, 100, 100)';
rect.noStroke();
```

**Change position:**
```js
function update() {
	rect.translation.x += 1;
  	rect.translation.y += 1;
}
```

**Detect when shape is clicked on:**
```js
var rect = two.makeRectangle(100, 100, 50, 50);
rect.fill = 'rgb(255, 100, 100)';
rect.noStroke();
two.update(); // Important to update or it won't work

rect._renderer.elem.addEventListener('click', function() {
	console.log("Rect was clicked.")
}, false);
```

**Text and counter:**
```js
// Create a text object
var counter = two.makeText("0", two.width / 2, two.height / 2);

// Set the font size, alignment and color
counter.size = 80;
counter.alignment = "center";
counter.fill = "lime";

// Initialize the counter value
var count = 0;

function update() {
  counter.value = count.toString(); // Set the value to the variable 'count' but string converted
  count++; // Add 1 to the value
}
```

**Load image/texture:**
```js
const texture = new Two.Texture('https://upload.wikimedia.org/wikipedia/commons/3/3a/Cat03.jpg');
const image = two.makeSprite(texture);
image.translation.set(two.width / 2, two.height / 2);
```
<br /><br /><br /><br /><br />
# Shaders
Shaders can be found at: https://www.shadertoy.com/
Select and object and head over to the material tab and from there you want to set the type to SHADERMATERIAL.
On the program row, you can now set INFO, VERT and FRAG (information, vertices and color).

An examples from Three.js on an Icosahedron mesh:

**INFO:**
```js
{
	"defines": {},
	"uniforms": {
		"time": {
			"value": 0
		}
	}
}
```

**VERT:**
```js
uniform float time;
varying vec3 vPosition;
void main() {
	vPosition = position;
	vPosition.x += sin( time + vPosition.z * 4.0 ) / 4.0;
	vPosition.y += cos( time + vPosition.z * 4.0 ) / 4.0;
	gl_Position = projectionMatrix * modelViewMatrix * vec4( vPosition, 1.0 );
}
```

**FRAG:**
```js
varying vec3 vPosition;
void main() {
	gl_FragColor = vec4( vPosition * 2.0, 1.0 );
}
```

**SCRIPT:**
```js
function update( event ) {
	this.material.uniforms.time.value = event.time / 500.0;
}
```
<br /><br /><br />
**Additional Three.js documentation can be found at:** https://threejs.org/docs/ <br />
**Ask questions on MarsF: https://ullblocks.jonhosting.com/forums/ (currently under development)** <br /> **Or you can join our Discord server: https://discord.gg/s78zWvwV6d**

Contact me on Discord with suggestions (or open an issue): *Cedric#0591*
