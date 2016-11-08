# [Webpack: The One Build Step To Rule Them All](https://qconsf.com/sf2016/presentation/webpack-one-build-step-rule-them-all)

Monday, Nov. 7 2016

@thelarkinn - Sean Larkin (Webpack Core Team)

## JS Modules

How to use them:
* ~~Script tag~~
* ~~Globals~~
* Module loaders!

Many module syntaxes:
* AMD (RequireJS)
* CommonJS (Node)
* import/export (ES2015)

Webpack handles all formats!

Webpack is a __module bundler__ and NOT a _task runner_.

Treats your code like a module.

How to use it:
* webpack.config.js
* Webpack CLI
* Node API

## Core Concepts

Use NodeJS's module loading system, put it in the browser.

```
bootstrap.js -> app.component.js -> external.lib.js -> dependency.js -> external.css
```

Webpack Config options:
* `entry` property tells Webpack what files to use by specifying the "index" file
* `output` property determines where and how to distribute bundles
* `loaders` tell Webpack how to load files in your content base, and return "compilations"
  * Webpack only understands JS, loaders can "transform" other content (ES2015 w/ Babel, CSS/Sass, etc)
  * Syntax: `loaders: [{ test: /\.*css$/, loader: 'css' }, ...]`
  * Include, exclude, and additional config options (example - don't bundle up specs!)
* Loaders can be chained (right -> left): `{ test: /\.less$/, loaders: ['style', 'css', 'less'] }`
  * Compile Less -> CSS, Load CSS as string, inline as JS
* `plugins` add additional functionality to "compilations", makes Webpack infinitely configurable
  * Plugins are just ES5 "classes", implement an `apply` function
  * Syntax: `plugins: [ new wepack.optimize.UglifyJSPlugin() ]` - use `new` to pass in params
  * 80% of Webpack itself is the plugin system!

## Common Questions

_Why use Webpack over Grunt/Gulp?_
* Webpack knows the entire dependency graph, can help with optimizations
* Instead of having tools that only understand one language, Webpack is one tool for many languages

_Webpack or SystemJS?_
* Trick questions, they're different things!
* SystemJS will have its own bundler, but it can't optimize like Webpack can

_Won't HTTP2 fix everything?_
* Some parallel loading will help, but it's not a silver bullet
* Can use Webpack to optimize your bundles, even if you serve multiple bundles over HTTP2

_Dev Server, Hot Module Replacement, Code Sharing, Lazy Loading, Source Maps?!?_
* Webpack does it all

## Webpack 2

In beta, coming soon!
* Native ES2015 module support
* Tree shaking
* Faster compilation
* More built-in optimizations
* Better loader syntax
* Config validation
* And much more!

Staying in beta until first-time user docs are updated.

Looking into the future...
* HTTP2: Webpack's AggressiveSplittingPlugin (in latest), split up by min/max file size, load sync or async
* HTTP2: Dependency tree-driven Push Manifest
* Usability: Complete overhaul of the main interface
* Optimization: Module inlining and concatenation (Rollup)
* DevTools: Working with multiple browser teams to bring custom instrumentation to Webpack
* Crazy Ideas: Headless Chrome (timeline stats) + Machine Learning = Tweaked Configs
* Accessibility: Make it easier!

State of the art:
* Used for Angular 2's cli, React, Laravel, .NET, JHipster (Spring), and many more

## Why Care?

Page load matters, long load times = less business

Webpack is open source, has a rich plugin ecosystem thanks to the users!

New docs - http://webpack.js.org/concepts

Tweet with #webpack
