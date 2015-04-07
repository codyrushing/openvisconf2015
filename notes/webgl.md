# WebGL for Graphics and Data Visualization
Nicolas Carcia Belmonte - Uber (and Twitter)

## WebGL
- JS API to access GPU (implementation of OpenGL)

## Use cases
* Real-time data analysis
* Scientific visualization (lots of data)
* Data art
* When rendering would otherwise be a bottleneck with say, SVG

Bottleneck is instead computational JS

Color decomposition - on every frame running lots of processing on each image.

Space filling algorithm (same as circle packing, but with any shape)

## How does it work
Example: you send an array of float (x,y,z) for some 3D thing to render

* Vertex shader - programmable, change how things are oriented (rotation, translation, etc)
* Triangle assembly - non-programmable - build faces from points
* Raserization - non-programmable make it presentable on a screen (not vector)
* Fragment shader - how things look (color, shadows)

# GLSL
* The language you use to write the shader
* C-like
* Built-in types for graphics
* Operator overloading (using + to add two vectors, for example)
* Instanced Arrays - new builtin in GLSL.  Good for data conversion inside of GLSL that would be too costly in JS
** Eg add interpolated data to JS data

## Interactivity
* WebGL is like canvas in that you just get an array of pixels.  It's not like working with DOM.
* So from a pixel, you may have to map that pixel index to something else.

GLSL is very low-level - so use a library.