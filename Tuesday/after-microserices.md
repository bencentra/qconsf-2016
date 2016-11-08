# [What Comes After Microservices?](https://qconsf.com/sf2016/presentation/what-comes-after-microservices)

Tuesday, Nov. 8 2016

@mranney - Matt Ranney (Uber)

## Intro

Uber is growing, hire a lot of engineers. 200 -> 2500 in 2 years.

Like all good engineers, they wrote a lot of software! Deployed as (micro)services.

1797 services!

Uber has embraced microservices hard, but comes with its own problems.
* Hard to debug
* Difficult to understand the system as a whole
* Hard to measure performance
* Problems collaborating?

## Why Microservices?

Easier releases
* Releasing smaller parts are less disruptive

Efficiency maybe?
* Scaling out only the parts that need it

Scaling the organization
* Uber couldn't have scaled as quickly without microservices

Loose coupling
* Small, modular pieces
* Uber dismantled a monolith into microservices
* Easier to manage

Uber has many repos, whereas Google has a monorepo

## New Problems

The expected:
* Sharded databases
* RPC
* Service discovery
* Rate limiting
* Circuit breaking
* Tracing
* Release management

Momentum is slowing down
* Yes, the org is bigger
* It's hard to know where to make a change
* Simple changes involve many parts, owned by many teams

Composability
* Unix philosophy, lots of small parts
* Really hard to do in practice
* What if it's easier to write a new service than update an existing one?

```
mobile -> RTAPI -> demand -> optic -> pricing
                          -> geobase
                          -> disco (routing) -> various others
                          -> supply
```

_Diagram of simplified Uber architecture_

Actual diagram is a horrifying maze

Implementing a small change (e.g. cute puppies in a car!) affects tons of critical services, cross team boundaries.

System is not actually composable, can't just add in the puppy logic.

## Fixing Composablility

Services want their own storage, lots of services means lots of storage installations to manage

Hard to cache, or a burden on traffic/performance, difficult to test, hard to update schemas

Goals:
* Having 1M services should be as easy as 1K or 10.
* Provisioning should be as easy as checking in code
* Should be able to safely test with real production data
* Fancy types are useful

Create a new layer, reads come from production, saved to pre-prod, layered "scopes" to evolve schemas

A bunch of services all talk directly to each other (via RPC)

Async message passing FTW, right?

Puppies team wants to inject a filter to ensure users like puppies. Can't do that in RPC framework.

Instead of services, use "composable event processors"
* Pass along a request, let it get processed by N filters.
* What about service discovery?
* Developers want to devleop, not think about the big picture

Let's make the tools for building big be _better_ than those for building small

At first, developer convenience _always_ trumps correctness. Don't want to go out of business!
