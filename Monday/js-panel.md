# [The Past, Present, and Future of JavaScript](https://qconsf.com/sf2016/presentation/past-present-future-javascript-language)

Monday, Nov. 7 2016

@jhusain - Jafar Husain
@stefanpenner - Stefan Penner
@_jayphelps - Jay Phelps (host)

_Pre-talk survey, didn't even mention Backbone!_

## What is TC-39

Companies, browser makers, framework designers, implementers, etc. Come up with proposals, get people on board (transpilers, browsers), try it out, eventual adoption by all platforms.

Deciding what's important - member companies and framework designers come together, understand what features would make their jobs easier. Users can also submit their own proposals - just needs a "champion" on TC-39.

"User-land" - features that could be implemented in the browser in JS today: promises, new Array methods, etc.

## How'd we get to ES2015

Tried to do one big release - ES4 - with all the features for everyone. It didn't work. "A battle for the soul of JavaScript," some might have wanted to alter JS dramatically. Decided to take is smaller with ES5, ES2015, and on - embrace what is good about JS and build on it. The TC also got better at working together.

\#JavaScriptFatigue - ES2015 was a big release, started getting implemented in 2012. Now it's a "train"-style: new spec every year, if a feature is on time is goes out. ES2016 additions will be small in comparison.

## Interacting with TC-39

A GitHub issue is all it takes! Start the conversation there. https://github.com/tc39

## What version to teach

Committee sees features as features, working its way through the stages. Serious JS devs today have a build process, so include a transpiler. Is a bit annoying for just playing around. Teach Stage 4 or 5, haven't made it to the browser yet, but "pave the cow path" - features/patterns are already being used (via libraries, etc), TC-39 starts to work it into the spec.

TC-39 doesn't build ahead of the web - why waste time on something no one will use? If a library, framework, NPM module, etc has a good feature/pattern peoeple are using, the TC-39 will standardize it (or something like it).

## Feature adoption and collision

Big companies on TC-39 - Google, Microsoft - can use telemetry data to anticipate API collisions. Example: `Promise` was fine, but `Array.contains()` had to be called `Array.includes()`.

Don't pin polyfills on a global, OR name it something unique (not after the spec). This will help prevent backwards-incompatibility. Use modules (CommonJS or AMD) whenever possible.

Test suite `test262` will run against Stage 4 and 5 features, you can run your polyfill against that.

## Web Assembly

JS is "the assembly language of the web" (esp. with transpilers). It's a common base, but it isn't always efficient.

Web assembly puts more primitives on the web for devs to adopt, lower-level than JS, much easier to target with compilers and ship ANY language, not just JS. Still in its early stages, ideal for high-performance but little DOM manipulation (e.g. cryptography).

ASM.js started by Mozilla. A small subset of JS that is like C, can be optimized to 30-50% performance of C (not great, but better than today). Still sending JS, needs to be parsed, how do we skip that stage? Web assembly will be stack-based.

## TypeScript

TC-39 is nervous to build a type system into the language. Some language constructs are reserved (eg. `var x:int = 1`) for TypeScript, Flow, etc, make it easy to shim types into the language. One day, these constructs might make it back into the spec.

Type systems are so important to get right, don't want to make a mistake. Take advantage of hindsight with TS and Flow if types should ever be adopted in the future.

Maintainability is a big motivator, also small IoT devices. Can't just "declare bankruptcy" and bump a version, we're always shipping source to clients and the browsers need to support it all.

## New Features vs. Performance

Example: i18n. Each request sends i18n libraries, what if it was baked into the web? Helps pull stuff out of source. ES2015 classes (without transpilers) will enable less boilerplate, too.

## Concurrency

Working on it: `SharedArrayBuffer`. Tried working high-level down (e.g. make `Array.map` concurrent), had a bad time. Trying again from a lower-level, taking their time, make sure the memory model is sound.

## Upcoming features

Stef - Private scope for classes and property decorators in classes. More terse code, hides more implementation details. Async iterables, observables, though they might be in contention with each other

Jafar - Iterators are currently sync, might want async to handle I/O streams or events. Observables are like iterators, but control is reversed - iterables pull next value, observables push next value. For event streams - `addEventListener` will be built on top of observable, create "drag" event out of existing mouse events. Can treat event streams like arrays, `map` and `filter`. For I/O streams - async iterator to request value, get promise, then act and request more. Different types, different problems, need to work well together.

__JS is never "done."__
