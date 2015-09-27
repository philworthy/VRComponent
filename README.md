# VRComponent

A virtual reality component for Framer. The virtual enviroment is created using the [cubemap technique](https://en.wikipedia.org/wiki/Cube_mapping). The cube requires six images, one for each side. Your own layers can be augmented on top of the virtual environment using a `heading` and `elevation`.

You can listen for orientation updates using the `OrientationDidChange` event. This event contains information about heading, elevation and tilt.

## Examples
- [Base setup](http://share.framerjs.com/nbm68qngj9oi/)
- [Event data](http://share.framerjs.com/6ui2dok637qt/)
- [VR shape puzzle](http://share.framerjs.com/vfa1wqhsqldw/)

## Properties
- **`front`** (set: imagePath *\<string>*, get: layer)
- **`right`** (set: imagePath *\<string>*, get: layer)
- **`back`** (set: imagePath *\<string>*, get: layer)
- **`left`** (set: imagePath *\<string>*, get: layer)
- **`top`** (set: imagePath *\<string>*, get: layer)
- **`bottom`** (set: imagePath *\<string>*, get: layer)
- **`heading`** *\<number>* (0 to 360 degrees)
- **`elevation`** *\<number>* (-90 to 90 degrees)
- **`tilt`** *\<number>* (-180 to 180 degrees)
- **`lookAtLatestAugmentedLayer`** *\<bool>*

```coffee
{VRComponent} = require "VRComponent"

vr = new VRComponent
	front: "images/front.png"
	left: "images/left.png"
	right: "images/right.png"
	back: "images/back.png"
	top: "images/top.png"
	bottom: "images/bottom.png"
```

## Functions
- **`augmentLayer`(**layer, heading, elevation**)**
- **`hideCube`()**

```coffee
# either augment a layer by giving the heading and elevation as function parameters
layer = new Layer
vr.augmentLayer(layer, 230, 10)

# or set these values on the layer before augmenting
layer.heading = 230
layer.elevation = 10
vr.augmentLayer(layer)
```

## Events
- **`Events.OrientationDidChange`**, (heading, elevation, tilt)

## Future plans
- Integrate support for Google Street View panoramas
- Add support for spheremap projection (WebGL)
- Hit detection of the layers in front of the viewer, and those behind the location of mouse and touch