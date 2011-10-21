Intro
=====

Have you ever wanted to tar something, but you didn't want to push it to your server first?

Tar-js is here to the rescue!!

With tar-js, you can construct a tar archive in the browser. This is basically a port of tar-async for Nodejs for the browser, with a couple differences.

Here's what it supports:
  * Add strings to a tar archive as files
  * Customizable uid, gid, mtime, and permissions (defaults work well though too)
  * Add files in a directory heirarchy

Dependencies
------------

Tar needs an HTML5 compliant browser. More specifically it needs `Uint8Array` to work.


Installation
------------

Tar needs [Ender](http://ender.no.de) to work. If you have Ender
installed on your system, then Tar can be installed by typing `ender
build tar-js`, or `ender add tar-js` if you already have an ender file.

Usage Guide
===========

Require the library like so:

    var Tar = require('tar-js'),
        tape = new Tar();

Then just call `tape.append` with your params and it'll be added to the archive. That's it!

Here's the api for append: `append(filepath, content, [opts], [callback])`

* filepath- string path (can include directories and such)
* content- string or Uint8Array
* opts- options:
  * mode- permissions of resulting file (octet) [default: 777]
  * mtime- modification time in seconds (integer) [default: current time]
  * uid- user id (integer) [default: 0]
  * gid- group id (integer) [default: 0]
* callback- callback when done (takes a Uint8Array as it's only parameter)
  * This is a reference to the tar so far
  * Copy it if you want to use it, because subsequent adds may break stuff
