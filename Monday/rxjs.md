# [Building Robust Web Applications With RxJS](https://qconsf.com/sf2016/presentation/building-robust-web-applications-rxjs)

Monday, Nov. 7 2016

@BenLesh - Ben Lesh (Netflix)

## Common problems

* Bad connectivity
* Handle live data or streams
* Avoid page reloads
* Dashboards, chat apps, etc.

## Websockets

Basics:
* Requires some coordiation (timing when opening connections, event handling)
* Use resources on client and server
* Using one websocket per data stream, 4 streams = 4 requests. Good for 1 client per server, but not scalable.

Multiplexing - take all your streams and run them over one socket.
* First call opens connection if none exists. Need to close it when final data stream closes.
* Start a "subscription" to a data stream when you open a connection, might be many to track
* Filter all incoming requests to send them to the correct client data stream
* Need to unsubscribe from data stream (from server) you no longer care about

^^ That's all just how to set up a connection. What about reconnecting on failure?
* Imperative code around this can get hairy

## RxJS

_"Think of RxJS as Lodash for events."_

> ReactiveX combines the Observer pattern with the Iterator pattern and functional programming with collections to fill the need for an ideal way of managing sequences of events.

Observables push data at you, notify you of errors, and notify you when they are complete.

Observables wrap a function, executed on subscribe to set up observation.

That function can return teardown logic, executed on unsubscribe.

Use the observe you're given to emit values from you Observable

```js
const myObservable = new Observable(observer => {
  let i = 0;
  const id = setInterval(() => {
    observer.next(i++);
    if (i === 10) {
      observer.complete();
    }
  }, 100);
});
```

Observables:
* Any number of values
* Any amount of time
* Lazy
* Cancellable
* Execute setup on subscription
* Execute teardown on unsubscribe

Observers let us treat events as sets of things, such as our individual data streams, filtered from a single websocket

_Deep dive into Observables here. Read the docs._

Network failures - can listen to "retry errors," turn it into a stream of events you can control to handle reconnection

## Useful links

* RxJS 5 - https://github.com/ReactiveX/rxjs
* Docs - http://reactivex.io/rxjs/
* Example - https://github.com/blesh/robust-websocket-talk

Start by learning `Observable`, try it out. Move on to `filter` and `map` (also `flatMap` and `mergeMap`). Don't rush!
