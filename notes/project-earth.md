# Building Earth
Cameron Beccario

Aimless and jobless, came up with this idea to do an HTML5y weather map.

Visualizing wind data in a 3D sphere.

http://earth.nullschool.net/ - check it out

## 4 layers
* bottom : svg map and topography
* canvas : all particles
* canvas : color layers
* top : svg clip that anti-aliases everything

## Compression
* Huge file sizes from the weather database, gotta deal with that
* Filter
** Get the actual data (eg temperature 50) and for all adjacent points, just get the diff, which is likely a smaller number better for Gzipping.
* Node.js pulls data and uploads them to Amazon S3
* S3 has CloudFlare in front of it, edge network (just like Akamai)

It goes super viral - wooooo.

## Lessons
* Usability
* News organizations ran with this, and the accuracy of it is possibly slightly off given the way it was constructed.
* Free stuff
** Free software, free data
* With large amounts of data like this and computation.  Don't build a key value object {x: 1, y: 2, velocity: 10}.  Just do them as a flat array
* Binary encoding