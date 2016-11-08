# [The Strengths of Ember, Angular & React Explored](https://qconsf.com/sf2016/presentation/strengths-ember-angular-react-explored)

Monday, Nov. 7 2016

## React

Lee Byron (Facebook)

Started at Facebook in 2012 - Comments, Chat, Notifications, Instagram.com

Open-sourced React in 2013, criticized at first, very different from other UI frameworks

3 Primary Differences

### 1) Not MVC, MVVM, MV*, etc
  * All share models, specifically mutable models
  * React does not require models, can use objects and arrays
  * React is a Component-based UI

```js
function ExampleComponent(props) {
  return React.createElement(
    "div", {className: "fancy"},
    "Hello" + props.name
  );
}
```

JSX is an optional templating language often used with React

Whenever data changes, re-render the view - but "Reconcile" differences to avoid rendering everything.

Component-based UI with functions, not templates.

### 2) Not about rendering HTML

React Components take Data and return an Element, not straight HTML

Elements have a type, attributes, and children
* UI = Elements, Browser = DOM, Server = HTML, iOS Apps = UIView, Android Apps = Android.View, VR = 3D Scene Graph
* React, React Native, and React VR

### 3) React is designed to be adopted incrementally

React is used in Facebook where dynamicism is necessary. NOT EVERYWHERE.

Can introduce React "bottom up" into an existing app

Components have lifecycle hooks, an "escape hatch" to use React with existing frameworks if you really have to.

### BONUS - React has a great community

Provide, education, tools, etc.

## Angular (2)

Rob Wormald (Google, Angular Core Team)

### Component Architecture

Learned from React!

Applications, not just Views. Assemble your application out of Components.

Component = HTML + CSS + Class (JS logic), connected by metadata

Very little Angular inside your application logic

HTML Templates with data binding hooks (directives, events, 2-way data binding)

Directives let you modify the behavior of existing elements by attaching some extra logic

Services are just classes.

Provides a dependency injection system via the Injector (at runtime)

Routing functionality, provides lazy loading, code splitting, etc.

Can pre-compile Views (ahead-of-time), take the work away from the browser, huge performance boosts.

### One App, Everywhere

Server-side rendering

Web, native, etc

Generates Closure compiler-friendly output, optimize!

### TypeScript

Maintained by Microsoft, provides types and many other nice features

## Ember

Taras Mankovski ("The Ember Sherpa")

Released in December 2011

"A framework for building ambitions web applications"
* created by many people
* maintained for a long time
* upgraded, not rewritten

Features:
* Routing
* Component Architecture
* DOM Diffing
* One or Two-way property binding
* HTML Templating (Handlebars)
* Service Composition, dependency injection

### 1) Framework for large applications

Too valuable, too big to be rewritten every several years

Moving to SPAs from multi-page, how do we prepare for the future?

Contributing to web standards:
* Involved in TC39
* Polyfill new features
* Provide feedback

Contributing and adopting good ideas:
* Introduced 1st class URL based routing
* Introduced CLI development environment (`ember-cli`), adopted by Angular 2
* Adopted unidirectional data flow and re-render from React

"All good ideas eventually end up in Ember"

Predictable Upgrade Path
* Strict adherence to semver
* 6 week releases for early adopters (minor releases)
* LTS releases for slower adopters
* Guide upgrades with deprecation warnings

### 2) Support from community

Big companies - LinkedIn, Nest, Bustle, ZenDesk, and many more!

3000+ add-ons

### 3) Comprehensive tooling

`ember-cli`, standard development environment, maintains conventions, common for all users

Ember FastBoot - Server-side rendering, speed up initial render, NodeJS server

Ember Engines - Big app = many small apps, package apps as add-ons, lazy load support

## Panel

__Angular 1 -> Angular 2, WTF?!?__
* Angular 1 is pre-modules, pre-Promises, felt it was a good time to adopt new standards
* Built `ng-upgrade` to run both Angular 1 and 2 together, incrementally upgrade
* Learned from Ember, wanted a stable release and upgrade path, deprecation policies
* 2 major release deprecation cycle

__React is just a rendering layer, what about state management?__
* React is not a framework! Only opinionated about Views.
* Facebook - lots of apps, lots of architectures, didn't want to update everything
* Leverage the JS community to amplify good ideas (e.g Facebook made Flux for data flow, improved by community with Redux)
* Can keep React as other better tools come out for state, networking, etc.

__Ember has a LOT to learn, APIs keep changing, how do I sell this?__
* Ember tries to give the developer everything they need
* No huge company backing it, but it's been consistently good
* Built for long term support, it's a reliable choice

__Advice with starting with your framework:__
* React - Start simple, just use React! No Flux, no JSX, just understand Components and such. (JSX requires Babel).
* Angular - Start simple, and read the docs! Understand the basics like Components.
* Ember - Jump in, write a simple Ember app!

__How do you handle mobile?__
* React - Open-source what we use. Facebook is a mobile app! It uses React! It's used around the world on low power devices, not so great networks! React has to support those cases. Also there's React Native for mobile apps. Also translate React to other languages for other system (e.g. ComponentKit for Objective-C)
* Angular - Mobile was top priority. AoT compilation helps save bytes, improve performance. By solving mobile problems, you get desktop performance for free.
* Ember - Has mobile perforance in mind - server-side rendering, etc. But Ember is often used for very big sites, dashboards, etc, so desktop performance is often considered first, then make it better for mobile.

__What tools are available, and what tech do you need to know?__
* React - Introduce tools as they become relevant. `create-react-app` to generate boilerplate. Need Babel to compile JSX. Flux or Redux (or other) for managing state, gonna have to think about what your app needs.
* Angular - Push for TypeScript, requires tooling but the payoff is huge, especially for big/distributed teams. Don't _need_ TS, but you _really should_ use it. CLI tooling - forked from Ember! - now does heavy lifting. Supports Flux and Redux!
* Ember - The more JS you know the better. Ember teaches you good ways to solve problems (e.g. Promises). Don't need to know ES6 to write JS or Ember. Ember Objects have custom events and other functionality that make it different from plain JS.

__What is the craziest thing build with your framework?__
* React - Watching React get repurposed, such as using React with Closure, fits well with functional programming!
* Angular - A music generation app made by @teropa, uses Angular, RxJS, other new tech
* Ember - Gavin Joyce, made a piano app with Ember
