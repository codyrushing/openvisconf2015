# Interactive Datavis with React
## Taming the complexity of the changing state
Ilya Boyandin - http://www.interactivethings.com/

Has done lots of visualizations (d3, Backbone, maps, etc)

## Why interactivity
* There is not enough space for all the data
* Enforce sequential storytelling.
* Engaging

## Why is interactivity hard?
* Every interaction can change state.  Multiple states equals multiple transitions between those states.

## Scalability
* d3 and other DOM datavis tools are great, but scaling is a challenge
* React as an application wrapper helps a lot.

## MVC
* Has been the standard for a long time.
* d3 is the view, and controllers send updates down to it.  and models update.  User changes something in the view, goes up to controller and changes model.
* But with lots of views, this gets really difficult, and each component has its own state - what is the source of truth?

## Better approach
* Manage application state, and everything flows downstream from that.
* Use event management to get user changes in view up to the application state.
* Over time, state changes, but the mapping and relationships between state and views does not.
* But that means that every state change is a full re-render

## React to the rescue
* Uses virtual DOM to determine what needs to be changed in actual DOM.  No full re-render if not necessary.  Virtual DOM is cheap and fast.  Real DOM is expensive and slow.

## But say you have a particle system, which updates a lot and often
* React is not a good choice, because it's doing so much computation for every single update of every particle in the system.
* Better approach - use just plain d3 to do transitions between the nodes.  React doesn't need to handle every step of that.  So React issues a single update from 5 -> 10, and d3 does a transition.  React doesn't care about the animation.
* Use shouldComponentUpdate to filter out unnecessary re-renders.
* Problem, React destroyes old components and re-renders new.  Use React.addons.TransitionGroup.

## Flux architecture
* One way data flow.  With events emitted by views to a dispatcher which updates everything from above.

## Immutable-js
* Inspired by Clojure.
* Create immutable objects.  These are good for use in shouldComponentUpdate, because immutable objects are very easy to compare.  Easy to detect changes in large state objects.

## Server side rendering
* Easy to use React.renderToString(MyApp()) server side.  Super easy.

## New React implementations
* React Canvas - rendering to canvase
* React Native - iOS and Android (no graphic support yet, only UI)
* React Art - what?

## Dev tools
* Hot code updates - change your react template js, and do a re-render in the browser.  Kinda like browsersync for React (only available through WebPack).

