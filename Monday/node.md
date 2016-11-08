# [The Node.js Ecosystem in Perspective](https://qconsf.com/sf2016/presentation/nodejs-ecosystem-perspective)

Monday, Nov. 7 2016

Dan Shaw (NodeSource)

JS is taking over, baby!

NodeSource = Entrprise Node.js

## In The Beginning...

Created by Ryan Dahl
* Wanted to improve application developent (over Rails, etc)
* Created on GitHub in the open
* Evented I/O
* C++ and JavaScript
* No package manager
* Mostly \*nix-based

Node.js is born!
* Tiny cloud as the "dot" in the logo, fitting (deploying Node apps to Docker containers, tiny "clouds", constrained environments)

## Key platform decisions

Ships with "batteries included"
* Platform and base API provided
* JS And Native interfaces provided by Google Chrome's V8 VM
* V8 is bundled with Node.js
* Evented I/O originally built using libev (replaced with libuv for Windows support)
* Built-in package manager in npm!
  * Scuffle with Debian - packages should link rather than bundle (node bundles)

Node.js was built with a very liberal license
* Licensed under MIT
* Project identity is protected by copyright law
* Permissive license enabled io.js to happen (a very good thing!)

Node.js has no standard library and encourages userland experimentation
* Core is kept as small as possible, forced to rely on user contributions
* Helps with quickly evovling standards and community trends

Node.js chose to standardize on npm for package management
* There were originally many managers - `kiwi`, `npm`, and more
* npm adopted with v0.6, built the first registry, now the largest!

Node.js is fully cross-platform
* Windows support since v0.6
* Node.js still exposes some very \*nix APIs even on Windows
* Nearly 50% of all Node.js developers run Windows

Node.js applications run everywhere (take that, Java!)
* JS code runs everywhere
* Exception: Native code needs to be compiled for each target platform
* Companies like Netflix are limiting native code usage to maximize compatibility

io.js was an important exploration

Node.js exists under the Node.js foundation

## Node.js in the present

A Quick Aside on Promises
* Love them, hate them, they're here to stay!
* Adoption is increasing rapidly
* Driven by front-end frameworks
* Bluebird is the library of choice (for now)
* Asyc/Await changes everything (relies on native promises), making libraries challenging OR obsolete

Node.js Promises Support
* Native Promise support in Node.js provided by V8
* Node.js event loop must be aware of every event
* Currently, Promises are managed by microtask queue outside of Node.js visibility
* One solution is to replace built-in Promises with language-level implementation provided by Node.js

Node.js <3's V8
* V8 provides the JS language capabilities, object allocation, memory management
* Node.js incorporates V8 releases far more rapidly than browsers
* V8 releases can trigger a major semver bump
* VM Working Group working on ABI (bindings) stability
* Thanks to ChakraCore, Node.js has a test suite

Node.js <3's ChakraCore
* ChakraCore provides JS language capabilities for Edge and Windows
* Time-travel debugging is amazing
* test262 provides cross-VM conformance tests
* Experimental features are easier to test with ChakraCore because it's more open

Node.js <3's TC-39
* Worries over Fetch API, aligning CommonJS with ES modules
* Node.js has over 5 million users who don't want their code to break
* Node.js Technical Steering Committee now represented on TC-39 and will maintain active membership

Node.js <3's ES Modules
* Working with TC-39 to sort out details
* Will need to changes ES Modules spec for backwards-compatibility with Node.js
* However, JS and NOde.js are aligning on one true way to express modules

Node.js is Everywhere!
* Front-end tooling
* Server-side rendering
* APIs
* Internet of Things
* Desktop Applications with Electron (e.g. Slack)
