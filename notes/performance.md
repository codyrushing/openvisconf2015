# Weighing Performance Against Pain - SVG, Canvas, and WebGL
Dominkus Baur 

Only this year has iOS supported WebGL - now is a good time.

Again, avoid redraws as much as possibly.  Come up with solutions to avoid redraws (eg, scale something out instead of re-rendering it smaller)

## Know your tools
* Learn about Chrome's detailed performance tools

## Remove stuff
* Think about which elements and even CSS you need (eg, radians in css are expensive)
* Throttle your window events

## Shift things
* Use a web worker to do heavy computation, so that GUI rendering is not blocked.  Do it early and hold onto it, because communicating between worker and browser is expensive.

## You ultimately have to take over the browser's job
* eg. CSS transitions are something the browser can properly time and understand.  A JS animation is done by you and the browser doesn't know what's going on.
* DOM is slow.
* Reflows and repains are slow.
** Even just getting the height/width of an element triggers a reflow.
** You can remove elements from the DOM, do your transformations on them, and then reinsert.  Only causes two repaints, potentially faster.

## SVG
* Great, flexible, and all DOM conventions apply (CSS, events, etc)
* Tree structure, so you can move all children by simply moving the parent.
* But when you have a lot of items or particles, they all get a DOM node and it's super slow.
** No more than 10,000 static elements, and no more than 1,000 animated.

## Canvas
* Non-declarative.  You ahve to keep track of your own objects, and you have to know what and when to render.
* So you set up a render loop, just like draw() in Processing.
** requestAnimationFrame(cb) - run something on next possible frame
* Events are harder, basically you put an event on the canvas DOM element and when that even happens you look at the mouseX and mouseY.
* But performance is better than SVG noticeably.

## WebGL
* Low level graphics.  Essential simple triangles and textures.
# Raw WebGL javascript, very painful to work with
# GLSL - used to write shaders
# Three.js and pixi.js - excellent libraries.
# Shaders are where the power is at.