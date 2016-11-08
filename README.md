# MapSCII - The Whole World In Your Console.

A node.js based [Vector Tile](http://wiki.openstreetmap.org/wiki/Vector_tiles) to [Braille](http://www.fileformat.info/info/unicode/block/braille_patterns/utf8test.htm) and [ASCII](https://de.wikipedia.org/wiki/American_Standard_Code_for_Information_Interchange) renderer for [xterm](https://en.wikipedia.org/wiki/Xterm)-compatible terminals.

<img src="http://i.imgur.com/yYVt7No.png" width="100%" />

## Features

* Use your mouse to drag and zoom in and out
* Discover Point-of-Interests around any given location
* Highly customizable layer styling with [Mapbox Styles](https://www.mapbox.com/mapbox-gl-style-spec/) support
* Connect to any public or private vector tile server
* Or just use the supplied and optimized [OpenStreetMap](https://en.wikipedia.org/wiki/OpenStreetMap) based one
* Work offline and discover local [VectorTile](https://github.com/mapbox/vector-tile-spec)/[MBTiles](https://github.com/mapbox/mbtiles-spec)
* Compatible with most Linux and OSX terminals
* Highly optimizied algorithms for a smooth experience
* 100% pure Coffee-/JavaScript! :sunglasses:

## How to install

If you haven't already got Node.js >= version 4, then [go get it](http://nodejs.org/).

```
npm install -g mapscii
```

If you're on OSX, or get an error about file permissions, you may need to do ```sudo npm install -g mapscii```

## Running

This is pretty simple too.

```
mapscii
```

## Keyboard shortcuts

* Arrows **up**, **down**, **left**, **right** to scroll around
* Press **a** or **z** to zoom in and out
* Press **q** to quit

## Mouse control

If your terminal supports mouse events you can drag the map and use your scroll wheel to zoom in and out.

## Behind the scenes
### Libraries
#### Mastering the console
  * [`x256`](https://github.com/substack/node-x256) for converting RGB values to closest xterm-256 [color code](https://en.wikipedia.org/wiki/File:Xterm_256color_chart.svg)
  * [`term-mouse`](https://github.com/CoderPuppy/term-mouse) for mouse handling
  * [`keypress`](https://github.com/TooTallNate/keypress) for input handling

#### Discovering the map data
* [`vector-tile`](https://github.com/mapbox/vector-tile-js) for [VectorTile](https://github.com/mapbox/vector-tile-spec/tree/master/2.1) parsing
* [`pbf`](https://github.com/mapbox/pbf) for [Protobuf](https://developers.google.com/protocol-buffers/) decoding
* [`mbtiles`](https://github.com/mapbox/node-mbtiles) for [MBTiles](https://github.com/mapbox/mbtiles-spec/blob/master/1.2/spec.md) parsing

#### Juggling the vectors and numbers
* [`earcut`](https://github.com/mapbox/earcut) for polygon triangulation
* [`rbush`](https://github.com/mourner/rbush) for 2D spatial indexing based label and mouse collision detection
* [`breseham`](https://github.com/madbence/node-bresenham) for line calculations
* [`sphericalmercator`](https://github.com/mapbox/node-sphericalmercator) for [EPSG:3857](http://spatialreference.org/ref/sr-org/6864/) <> [WGS84](http://spatialreference.org/ref/epsg/wgs-84/) conversions
* [`tilebelt`](https://github.com/mapbox/tilebelt) for some [slippy map tilename](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames) calculations

#### Handling the flow
* [`bluebird`](https://github.com/petkaantonov/bluebird) for all the asynchronous [Promise](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Promise) magic
* [`request-promise`](https://github.com/request/request-promise) for promisified HTTP request handling
* [`userhome`](https://github.com/shama/userhome) to determine where to persist downloaded tiles

### TODOs
* MapSCII
  * [ ] CLI support
    * [ ] startup parameters
      * [ ] TileSource
      * [ ] Style
      * [ ] center position
      * [ ] zoom
      * [ ] demo mode?

  * [ ] mouse control
    * [ ] accurate mouse drag&drop with instant update
    * [ ] hover POIs/labels
    * [ ] hover maybe even polygons/-lines?
    * [ ] get hover lat/lng
    * [ ] zoom into mouse pos

* Styler
  * [ ] respect zoom based style stops

* Renderer
  * [ ] polygons
    * [ ] holes
    * [ ] use rbush?

  * [ ] label drawing
    * [ ] multi line label?

* TileSource
  * [ ] implement single vector-tile handling

## License
#### The MIT License (MIT)
Copyright (c) 2016 Michael Straßburger

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
