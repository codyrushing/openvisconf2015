# Mapping the Cosmos
Ian Webster - Google

Prompted by the Feb 2013 asteroid impact in Russia

## Browser is single-threaded
this means bottlenecks.  Rendering and computation can't happen at the same time

## Data chunking
* Timed array processing
** You break up a large data set into several smaller ones
** Give a short timeout (say 25ms), and it processes whatever it can in that time
** then give control back to the renderer.
** Shorter callbacks is the way.
* Monitor fps, and gracefully degrade the simulation
