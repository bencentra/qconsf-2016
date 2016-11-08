# [Intuition Engineering](https://qconsf.com/sf2016/presentation/intuition-engineering)

Wednesday, Nov. 9 2016

@caseyrosenthal - Casey Rosenthal (Netflix)

## Intro

The "control plane" - all the interaction in Netflix before you start streaming a video.

Netflix has many small engineering team that own one or a few microservices.

Three things to optimize for: Performance, Fault Tolerance, Availability

Netflix adds a fourth thing: Feature Velocity - how will this help us optimize delivering features faster?

## The Beer Game

Three teams:
* Customers, drink the beer
* Retailers, sell the beer
* Brewers, brew the beer

Each team in a separate room, can only pass paper indicating goods/money exchanged.

Teams need to optimize for satisfaction of all teams.

Buy one, stock one, brew one - stable system

Surge of customer demand, retailer orders more (linear), brewer brews more (exponential)

Extreme drop in demand, retailer doesn't order any, brewer has too much stock and brews none

End result: retailer has unnecessary stock, brewer has too much as well, no one is satisfied

Every team did something that made sense, but had a systemic effect that was undesirable ("whiplash effect")

At Netflix, this "game" could happen with network traffic, load balancing, and caching. A danger in distributed systems.

## Intuition Engineering Example - Vizceral

Develop a tool that'll provide a split-second understanding of the whole system

Dumb metaphor: a suit covered in electrodes, shocks when something is wrong

The longer you wear "the pain suit," the more you'll intuitively understand causes of pain

Created [Vizceral](https://github.com/Netflix/vizceral), "WebGL component for displaying animated traffic graphs"

Started with a simple demo, visualize traffic as dots. Volume, errors, and latency. Proves there is valuable information that can be obtained at a glance.

By watching Vizceral for only a few minutes, you learn what "normal" is for a certain time of day.

Example: visualizing failover of a region (notice errors, proxy traffic, flip DNS, investigate, undo changes)

Example: visualizing traffic within a region between microservices.

Not a tool for digging into the code, just for discovering possible sources of problems faster.

Considered D3, went with WebGL (better at handling a ton of dots, gotta go "bare metal").

Backed by a Node.js tracing system, returns JSON rendered by client.

Future work: stateful, record/replay

Another example of Intuition Engineering - Ward Cunningham's web traffic simulator (New Relic)
* Duration of dot = total length of request
* Size of dot = how long server spent computing
* Big "Red" requests pool up, cause "Orange" requests grow, blocks traffic and causes "Yellow" dots to grow, massive slowdown for a bit, eventually returns to normal

Beyond Vision:
* Understanding Scale - Planets are REALLY far away (balloon in corner of room to pin at podium is Sun to Earth)
* Sound - soundscape of the system, sounds are added/removed (e.g. frogs croaking) to indicate failures

Intuition Engineering:
* System Aspect > Quantitative Analysis
* New Senses, ways of experiencing something
* Don't Limit to Software
* Useful > Interesting (but it's nice if it looks cool, too!)
* Race against Machine Learning (things the brain do that machines can't, at least not yet)
