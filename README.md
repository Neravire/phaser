Phaser
======

Version: 0.9.5 - Released: 2nd May 2013

By Richard Davey, [Photon Storm](http://www.photonstorm.com)

Phaser is a 2D JavaScript/TypeScript HTML5 Game Framework based heavily on [Flixel](http://www.flixel.org).

Follow on [Twitter](https://twitter.com/photonstorm)<br />
Read the [Development Blog](http://www.photonstorm.com)<br />
Join the [Support Forum](http://www.html5gamedevs.com/forum/14-phaser/)

Try out the [Phaser Test Suite](http://gametest.mobi/phaser/)

![Blasteroids](http://www.photonstorm.com/wp-content/uploads/2013/04/phaser_blaster.png)

Latest Update
-------------

V0.9.5

* Moved the BootScreen and PauseScreen out of Stage into their own classes (system/screens/BootScreen and PauseScreen).
* Updated the PauseScreen to show a subtle animation effect, making it easier to create your own interesting pause screens.
* Modified Game so it splits into 3 loops - bootLoop, pauseLoop and loop (the core loop).
* Updated the BootScreen with the new logo and new color cycle effect.
* Added Game.isRunning - set to true once the Game.boot process is over IF you gave some functions to the constructor or a state.
* Fixed small bug in Signal.removeAll where it could try to shorten the _bindings even if undefined.
* Added the new FXManager which is used for handling all special effects on Cameras (and soon other game objects).
* Removed Flash, Fade and Shake from the Camera class and moved to the new SpecialFX project.
* SpecialFX compiles to phaser-fx.js in the build folder, which is copied over to Tests. If you don't need the FX, don't include the .js file.
* The project is now generating TypeScript declaration files and all Tests were updated to use them in their references.
* Fixed a bug in Flash, Fade and Shake where the duration would fail on anything above 3 seconds.
* Fixed a bug in Camera Shake that made it go a bit haywire, now shakes correctly.
* Added new Scanlines Camera FX.
* Fixed offset values being ignored in GeomSprite.renderPoint (thanks bapuna).
* Added new Mirror Camera FX. Can mirror the camera image horizontally, vertically or both with an optional fill color overlay.
* Added Camera.disableClipping for when you don't care about things being drawn outside the edge (useful for some FX).
* Updated TilemapLayer so that collision data is now stored in _tempTileBlock to avoid constant array creation during game loop.
* TilemapLayer.getTileOverlaps() now returns all tiles the object overlapped with rather than just a boolean.
* Tilemap.collide now optionally takes callback and context parameters which are used if collision occurs.
* Added Tilemap.collisionCallback and Tilemap.collisionCallbackContext so you can set them once and not re-set them on every call to collide.
* Collision.separateTile now has 2 extra parameters: separateX and separateY. If true the object will be separated on overlap, otherwise just the overlap boolean result is returned.
* Added Tile.separateX and Tile.separateY (both true by default). Set to false if you don't want a tile to stop an object from moving, you just want it to return collision data to your callback.
* Added Tilemap.getTileByIndex(value) to access a specific type of tile, rather than by its map index.
* Added TilemapLayer.putTile(x,y,index) - allows you to insert new tile data into the map layer (create your own tile editor!).
* TilemapLayer.getTileBlock now returns a unique Array of map data, not just a reference to the temporary block array
* Added TilemapLayer.swapTile - scans the given region of the map for all instances of tileA and swaps them for tileB, and vice versa.
* Added TilemapLayer.replaceTile - scans the given region of the map and replaces all instances of tileA with tileB. tileB is left unaffected.
* Added TilemapLayer.fillTiles - fills the given region of the map with the tile specified.
* Added TilemapLayer.randomiseTiles - fills the given region of the map with a random tile from the list specified.
* Added fun new "map draw" test - rebound those carrots! :)
* Changed SoundManager class to respect volume on first play (thanks initials and hackmaniac)

Requirements
------------

Games created with Phaser require a modern web browser that supports the canvas tag. This includes Internet Explorer 9+, Firefox, Chrome, Safari and Opera. It also works on mobile web browsers including stock Android 2.x browser and above and iOS5 Mobile Safari and above.

For developing with Phaser you can use either a plain-vanilla JavaScript approach or [TypeScript](https://typescript.codeplex.com/). We made no assumptions about how you like to code your games, and were careful not to impose any form of class/inheritance/structure upon you.

If you are compiling via TypeScript from the command-line please use `--target ES5` and `--nolib`

If you need it the included Grunt file will generate a RequireJS/CommonJS version of Phaser on build.

Phaser is just 45KB gzipped and minified.

Features
--------

Phaser was born from a cross-pollination of the AS3 Flixel game library and our own internal HTML5 game framework. The objective was to allow you to make games _really_ quickly and remove some of the speed barriers HTML5 puts in your way.

Phaser fully or partially supports the following features. This list is growing constantly and we are aware there are still a number of essential features missing:

*	Asset Loading<br />

	Images, Sprite Sheets, Texture Packer Data, JSON, Text Files, Audio File.

*	Cameras<br />

	Multiple world cameras, camera scale, zoom, rotation, deadzones and Sprite following.

*	Sprites<br />

	All sprites have physics properties including velocity, acceleration, bounce and drag.
	ScrollFactor allows them to re-act to cameras at different rates.

*	Groups<br />

	Group sprites together for collision checks, visibility toggling and function iteration.

*	Animation<br />

	Sprites can be animated by a sprite sheet or Texture Atlas (JSON Array format supported).
	Animation playback controls, looping, fps based timer and custom frames.

*	Scroll Zones<br />

	Scroll any image seamlessly in any direction. Or create multiple scrolling regions within an image.

*	Collision<br />

	A QuadTree based Sprite to Sprite, Sprite to Group or Group to Group collision system.

*	Particles<br />

	An Emitter can emit Sprites in a burst or at a constant rate, setting physics properties.

*	Input<br />

	Keyboard, Mouse and Touch handling supported (MSPointer events coming soon)

*	Stage<br />

	Easily change properties about your game via the stage, such as background color, position, size and scale.

*	World<br />

	The game world can be any size and Sprites and collision happens within it.

*	Sound<br />

	Currently uses WebAudio for playback. A lot more work needs to be done in this area.

*	State Management<br />

	For larger games it's useful to break your game down into States, i.e. MainMenu, Level1, GameOver, etc.
	The state manager makes swapping states easy, but the use of a state is completely optional.

*	Cache<br />

	All loaded resources are stored in an easy to access cache, which can be cleared between State changes
	or persist through-out the whole game.

*	Tilemaps<br />

	Support for CSV and Tiled JSON format tile maps. Supports Layered Tiled maps and layer based collision.

*	Game Scaling<br />

	Game scaling under your control. Removes URL/status bar on mobile (iOS and Android) and allows proportional scaling, fixed size and orientation checks.

![Phaser Particles](http://www.photonstorm.com/wp-content/uploads/2013/04/phaser_particles.png)

Work in Progress
----------------

We've a number of features that we know Phaser is lacking, here is our current priority list:

*	Better sound controls
*	MSPointer support
*	Text Rendering
*	Buttons

Beyond this there are lots of other things we plan to add such as WebGL support, Spine animation format support, sloped collision tiles, path finding and support for custom plugins. But the list above are priority items, and by no means exhaustive either! However we do feel that the core structure of Phaser is now tightly locked down, so safe to use for small scale production games.

Test Suite
----------

Phaser comes with an ever growing Test Suite. Personally we learn better by looking at small refined code examples, so we create lots of them to test each new feature we add. Inside the Tests folder you'll find the current set. If you write a particularly good test then please send it to us.

The tests need running through a local web server (to avoid file access permission errors from your browser).

Make sure you can browse to the Tests folder via your web server. If you've got php installed then launch:

    Tests/index.php

Right now the Test Suite requires PHP, but we will remove this requirement soon.

You can also browse the [Phaser Test Suite](http://gametest.mobi/phaser/) online.

Contributing
------------

Phaser is in early stages and although we've still got a lot to add to it, we wanted to just get it out there and share it with the world.

If you find a bug (highly likely!) then please report it on github.

If you have a feature request, or have written a small game or demo that shows Phaser in use, then please get in touch. We'd love to hear from you.

You can do this on the Phaser board that is part of the [HTML5 Game Devs forum](http://www.html5gamedevs.com/forum/14-phaser/) or email: rich@photonstorm.com

Bugs?
-----

Please add them to the [Issue Tracker][1] with as much info as possible.

![Phaser Tilemap](http://www.photonstorm.com/wp-content/uploads/2013/04/phaser_tilemap.png)

Change Log
----------

V0.9.4

* Added Tilemap.getTile, getTileFromWorldXY, getTileFromInputXY
* Added Tilemap.setCollisionByIndex and setCollisionByRange
* Added GameObject.renderRotation boolean to control if the sprite will visually rotate or not (useful when angle needs to change but graphics don't)
* Added additional check to Camera.width/height so you cannot set them larger than the Stage size
* Added Collision.separateTile and Tilemap.collide
* Fixed Tilemap bounds check if map was smaller than game dimensions
* Fixed: Made World._cameras public, World.cameras and turned Game.camera into a getter for it (thanks Hackmaniac)
* Fixed: Circle.isEmpty properly checks diameter (thanks bapuna)
* Updated Gruntfile to export new version of phaser.js wrapped in a UMD block for require.js/commonJS (thanks Hackmaniac)

V0.9.3

* Added the new ScrollZone game object. Endlessly useful but especially for scrolling backdrops. Created 6 example tests.
* Added GameObject.hideFromCamera(cameraID) to stop an object rendering to specific cameras (also showToCamera and clearCameraList)
* Added GameObject.setBounds() to confine a game object to a specific area within the world (useful for stopping them going off the edges)
* Added GameObject.outOfBoundsAction, can be either OUT OF BOUNDS STOP which stops the object moving, or OUT OF BOUNDS KILL which kills it.
* Added GameObject.rotationOffset. Useful if your graphics need to rotate but weren't drawn facing zero degrees (to the right).
* Added shiftSinTable and shiftCosTable to the GameMath class to allow for quick iteration through the data tables.
* Added more robust frame checking into AnimationManager
* Re-built Tilemap handling from scratch to allow for proper layered maps (as exported from Tiled / Mappy)
* Tilemap no longer requires a buffer per Camera (in prep for WebGL support)
* Fixed issues with Group not adding reference to Game to newly created objects (thanks JesseFreeman)
* Fixed a potential race condition issue in Game.boot (thanks Hackmaniac)
* Fixed issue with showing frame zero of a texture atlas before the animation started playing (thanks JesseFreeman)
* Fixed a bug where Camera.visible = false would still render
* Removed the need for DynamicTextures to require a key property and updated test cases.
* You can now pass an array or a single value to Input.Keyboard.addKeyCapture().

V0.9.2

* Fixed issue with create not being called if there was an empty init method.
* Added ability to flip a sprite (Sprite.flipped = true) + a test case for it.
* Added ability to restart a sprite animation.
* Sprite animations don't restart if you call play on them when they are already running.
* Added Stage.disablePauseScreen. Set to true to stop your game pausing when the tab loses focus.

V0.9.1

* Added the new align property to GameObjects that controls placement when rendering.
* Added an align example to the Sprites test group (click the mouse to change alignment position)
* Added a new MicroPoint class. Same as Point but much smaller / less functions, updated GameObject to use it.
* Completely rebuilt the Rectangle class to use MicroPoints and store the values of the 9 points around the edges, to be used
for new collision system.
* Game.Input now has 2 signals you can subscribe to for down/up events, see the Sprite align example for use.
* Updated the States examples to bring in-line with 0.9 release.

V0.9

* Large refactoring. Everything now lives inside the Phaser module, so all code and all tests have been updated to reflect this. Makes coding a tiny bit more verbose but stops the framework from globbing up the global namespace. Also should make code-insight work in WebStorm and similar editors.
* Added the new GeomSprite object. This is a sprite that uses a geometry class for display (Circle, Rectangle, Point, Line). It's extremely flexible!
* Added Geometry intersection results objects.
* Added new Collision class and moved some functions there. Contains all the Game Object and Geometry Intersection methods.
* Can now create a sprite animation based on frame names rather than indexes. Useful when you've an animation inside a texture atlas. Added test to show.
* Added addKeyCapture(), removeKeyCapture() and clearCaptures() to Input.Keyboard. Calls event.preventDefault() on any keycode set to capture, allowing you to avoid page scrolling when using the cursor keys in a game for example.
* Added new Motion class which contains lots of handy functions like 'moveTowardsObject', 'velocityFromAngle' and more.
* Tween Manager added. You can now create tweens via Game.createTween (or for more control game.tweens). All the usual suspects are here: Bounce, * Elastic, Quintic, etc and it's hooked into the core game clock, so if your game pauses and resumes your tweens adjust accordingly.

V0.8

* Added ability to set Sprite frame by name (sprite.frameName), useful when you've loaded a Texture Atlas with filename values set rather than using frame indexes.
* Updated texture atlas 4 demo to show this.
* Fixed a bug that would cause a run-time error if you tried to create a sprite using an invalid texture key.
* Added in DynamicTexture support and a test case for it.

V0.7

* Renamed FullScreen to StageScaleMode as it's much more fitting. Tested across Android and iOS with the various scale modes.
* Added in world x/y coordinates to the input class, and the ability to get world x/y input coordinates from any Camera.
* Added the RandomDataGenerator for seeded random number generation.
* Setting the game world size now resizes the default camera (optional bool flag)

V0.6

* Added in Touch support for mobile devices (and desktops that enable it) and populated x/y coords in Input with common values from touch and mouse.
* Added new Circle geometry class (used by Touch) and moved them into a Geom folder.
* Added in Device class for device inspection.
* Added FullScreen class to enable full-screen support on mobile devices (scrolls URL bar out of the way on iOS and Android)

V0.5

* Initial release

![Phaser Cameras](http://www.photonstorm.com/wp-content/uploads/2013/04/phaser_cams.png)

License
-------

Copyright 2013 Richard Davey, Photon Storm Ltd. All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are
permitted provided that the following conditions are met:

   1. Redistributions of source code must retain the above copyright notice, this list of
      conditions and the following disclaimer.

   2. Redistributions in binary form must reproduce the above copyright notice, this list
      of conditions and the following disclaimer in the documentation and/or other materials
      provided with the distribution.

THIS SOFTWARE IS PROVIDED BY RICHARD DAVEY ``AS IS'' AND ANY EXPRESS OR IMPLIED
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL RICHARD DAVEY OR
CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON
ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

The views and conclusions contained in the software and documentation are those of the
authors and should not be interpreted as representing official policies, either expressed

[1]: https://github.com/photonstorm/phaser/issues
[phaser]: https://github.com/photonstorm/phaser
