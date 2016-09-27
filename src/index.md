title: WebVR - Creating Virtual Worlds With JavaScript
output: public/index.html
style: styles.css
script: script.js
controls: true


-- bg-lights-of-city

# WebVR

## Creating Virtual Worlds with JavaScript 

<div class="contact">
  <p>Peter O'Shaughnessy, Samsung Internet</p>
  <p>[@poshaughnessy](https://twitter.com/poshaughnessy)</p>
</div>


-- valign-top bg-rollercoaster

### We're on the edge of a new era...


-- bg-lights-of-city

<blockquote style="font-weight:900">&ldquo;VR is the next major computing platform after mobile.&rdquo;</blockquote>

Mark Zuckerberg


<!-- TODO slide showing different headsets: Gear VR, Vive, Oculus Rift, Cardboard, Daydream -->


-- valign-top bg-cliff

## Presence


-- valign-bottom bg-grandma

<blockquote>&ldquo;I've made a lot of applications & nothing I ever created was ever going to make someone 
laugh, cry, recoil or scream like VR can.&rdquo;</blockquote>

Josh Carpenter


-- valign-bottom bg-another-world

## From web sites to web *worlds*


-- bg-lights-of-city

# WebVR

* Headset discovery
* Full-screen headset display
* Sensor integration, e.g. orientation
* Rendering for different hardware


-- bg-lights-of-city

### Stereoscopic

<img src="images/oculus-stereo-normal.jpg" alt="Stereoscopic" style="width:80%"/>


-- bg-lights-of-city

### Browser handles distortion

<img src="images/oculus-stereo-distortion.jpg" alt="Distortion" style="width:80%"/>


-- bg-lights-of-city

### Browser enthusiasm (so far)

![WebVR browser enthusiasm](images/webvr-browser-enthusiasm.png)

<p class="caption"><a href="https://iswebvrready.org/">iswebvrready.org</a></p>


-- bg-lights-of-city

* [Chrome](https://webvr.info/get-chrome/): *special build & flag*
* [Firefox](http://mozvr.com/#start): *nightly build & add-on*
* [Samsung Internet](http://developer.samsung.com/internet#gearvr-overview): *visit `internet://webvr-enable`*
* [Edge](https://blogs.windows.com/msedgedev/2016/09/09/webvr-in-development-edge/): *in development*

[webvr.info](https://webvr.info/)


-- bg-lights-of-city

![Requirements](images/webvr-requirements.png)


-- bg-lights-of-city

## WebVR API

#### Version "1.1" - [bit.ly/webvr-update-sep-2016](http://blog.tojicode.com/2016/09/update-on-webvr-spec-chrome-and-https.html)

-- bg-lights-of-city

```javascript
// Get list of available headsets
navigator.getVRDisplays();

// Request fullscreen on headset
VRDisplay.requestPresent({ source: myCanvas })
```

-- bg-lights-of-city

```javascript
// Like normal rAF but could be 90hz or more 
VRDisplay.requestAnimationFrame();

// Render what's on the source canvas
VRDisplay.submitFrame();
```


-- bg-lights-of-city

```javascript
/**
 * Get eye offset & rendering dimensions to help us
 * construct a stereoscopic scene for the user.
 */ 
VRDisplay.getEyeParameters(VREye);

/**
 * Get view & projection matrices for current frame
 * & VRPose with pos, orientation, accel & velocity.
 */
 VRDisplay.getFrameData();

```


-- bg-lights-of-city

![WebGL](images/webgl-logo.png)


-- bg-lights-of-city

## three.js

![threejs.org](images/threejs_org.png)

<p class="caption"><a href="https://threejs.org/">threejs.org</a></p>


-- bg-lights-of-city

### Let's make a spinning cube

```javascript
var renderer = new THREE.WebGLRenderer();

renderer.setSize( width, height );

document.body.appendChild( renderer.domElement );
```


-- bg-lights-of-city

```javascript
var scene = new THREE.Scene();

var camera = new THREE.PerspectiveCamera(
  45,             // Field of view angle
  width / height, // Aspect ratio
  1,              // zNear
  1000            // zFar
);

camera.position.z = 100;

scene.add( camera );
```


-- bg-lights-of-city

```javascript
var cube = new THREE.Mesh(
  new THREE.BoxGeometry( 50, 50, 50 ), // w, h, d
  new THREE.MeshBasicMaterial( {color: 0xFF0000} );
);

scene.add( cube );
```


-- bg-lights-of-city

```javascript
function animate() {
  cube.rotation.y += 0.1;
  renderer.render( scene, camera );
  requestAnimationFrame( animate );
}

animate();
```


-- bg-lights-of-city iframe

<iframe src="demos/threejs-spinning-cube/index.html" scrolling="no" width="100%" height="100%"></iframe>


-- bg-lights-of-city

```javascript
var controls = new THREE.VRControls( camera );
var effect = new THREE.VREffect( renderer );

...

controls.update();
effect.render( scene, camera );
```


-- bg-lights-of-city

<img src="images/sbrowser-cubes1.jpg" alt="WebVR cubes on Samsung Internet" style="max-height:calc(100vh - 5em)"/>

[threejs.org/examples/webvr_cubes.html](https://threejs.org/examples/webvr_cubes.html)


-- bg-webvr-cubes


-- bg-aframe valign-top

## A-Frame


-- bg-lights-of-city

```html
<script src="js/a-frame.js"></script>
```


-- bg-lights-of-city

```html
<a-scene>
  <a-sphere position="0 1.25 -1" radius="1.25" 
            color="#EF2D5E"></a-sphere>
  <a-box position="-1 0.5 1" rotation="0 45 0" 
         color="#4CC3D9"></a-box>
  <a-cylinder position="1 0.75 1" radius="0.5" 
              color="#FFC65D"></a-cylinder>
  <a-plane rotation="-90 0 0" width="4" height="4" 
            color="#7BC8A4"></a-plane>
  <a-sky color="#ECECEC"></a-sky>
</a-scene>
```


-- bg-lights-of-city iframe

<iframe src="demos/aframe-basic/index.html" scrolling="no" width="100%" height="100%"></iframe>


-- bg-llama-carousel


-- bg-lights-of-city

# Thanks!

<div class="contact">
  <p>[@poshaughnessy](https://twitter.com/poshaughnessy)</p>
  <p>[@sbrowserdevrel](https://twitter.com/sbrowserdevrel)</p>
  <p>[medium.com/samsung-internet-dev](https://medium.com/samsung-internet-dev)</p>
</div>

<p class="credits">Image credits: rollercoaster photo by <a href="https://www.flickr.com/photos/apol-photography/3729520874/">apol photography</a>, cliff photo by <a href="http://www.fotolia.com">Fotolia (purchased)</a></p>
