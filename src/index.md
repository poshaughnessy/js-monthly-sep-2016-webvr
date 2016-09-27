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

### Browser enthusiasm (so far)

![WebVR browser enthusiasm](images/webvr-browser-enthusiasm.png)

<p class="caption"><a href="https://iswebvrready.org/">iswebvrready.org</a></p>


-- bg-lights-of-city

* Chrome - special build & flag
* Firefox - nightly build & add-on
* Samsung Internet - visit `internet:`
* Edge - they're working on it

[webvr.info](https://webvr.info/)


-- bg-lights-of-city

![Requirements](images/webvr-requirements.png)


-- bg-lights-of-city

## WebVR API

Version "1.1" - [bit.ly/webvr-update-sep-2016](http://blog.tojicode.com/2016/09/update-on-webvr-spec-chrome-and-https.html)

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

## three.js

-- bg-lights-of-city

## A-Frame


-- bg-eee

![A-Frame basic scene](images/aframe-basic.png)


-- bg-llama-carousel


-- bg-lights-of-city

# Thanks!

<div class="contact">
  <p>[@poshaughnessy](https://twitter.com/poshaughnessy)</p>
  <p>[@sbrowserdevrel](https://twitter.com/sbrowserdevrel)</p>
  <p>[medium.com/samsung-internet-dev](https://medium.com/samsung-internet-dev)</p>
</div>

<p class="credits">Image credits: rollercoaster photo by <a href="https://www.flickr.com/photos/apol-photography/3729520874/">apol photography</a>, cliff photo by <a href="http://www.fotolia.com">Fotolia (purchased)</a></p>
