# [Mastering Chaos - A Netflix Guide to Microservices](https://qconsf.com/sf2016/presentation/mastering-chaos-netflix-guide-microservices)

Tuesday, Nov. 8 2016

Josh Evans (Ex-Netflix)

## Intro

Guillain-Barre Syndrome
* Antibodies start attacking mylan sheath on axons of nerves, diffuse signals
* Autoimmune disorder, externally triggered, treatable

Breathing is a miraculous act of bravery, so is taking traffic with microservices!
* Bad input from the world could cause a world of trouble!

## Microservice Basics

Netflix 2000 (aka how NOT to build services):
* Load Balancer -> Apache/Tomcat -> Java -> Oracle Database(s)
* Monolithic codebase deployed (bi)weekly, single database instance, vertically scaled
* Tight coupling, not fault tolerant, difficult to debug

Microservices are:
* Developing a single app as a suite of small services, each running in its own process, communicate with lightweight mechanisms, often HTTP API
* An extreme reaction to monolithic application issues
* Encourages separation of concerns, horizontal scaling, virtualization and elasticity

Netflix has:
* Edge services (load balaner, dynaimc routing, API, legacy)
* Middle Tier and platofmr (product, routing, persistence, recommendations, caching, storage)

Microservices are an abstraction:
* More than just a horizontal scaling pattern
* You WILL need to interact with data!
* Netflix pattern: application -> [ orchestration -> cache client -> client libraries (java) -> services -> databases ]

## Challenges and Solutions

### Dependencies

Crossing the Chasm
* Services calling other services introduces problems: network failure, congestion, scaling, logic, etc
* Cascading failures, one service fails and takes down others
* Hystrix - tool from Netflix, handle failures, provide fallbacks, etc
* How do you know if it works? Fault Injection Testing (FIT)! Synthetic transactions, test against live traffic

Critical Microservices:
* Not all services are created equal. Some are core to the experience, others are "optional"
* Example: users can browse popular movies (critical), but don't see a list of their recommendation (optional).

Client Libraries:
* Make REST calls shareable among other apps/services
* Slippery slope back towards a monolith, API gateway running a lot of code
* Simple logic, common patterns

Persistence:
* CAP Theorem: In the presence of a network partition, you must choose between consistency and availability.
* Netflix chose Eventual Consistency - Y number of X (Cassandra) nodes must respond that a write has been saved to be considered a "success," will eventually get copied to all nodes.
* Don't put all cloud instances in one region, even Amazon could go down. Multi-region strategy, complete failover.

### Scalability

Stateless Services:
* Not a cache or a database, frequently ccessed metadata, no instance affinity, loss of a node is not critical
* Auto-scaling groups: min/max, metrics to determine scaling, pull images out of S3 as needed. Efficient, handles failure and traffic spikes
* Chaos Monkey - take nodes down, ensure the system is tolerant.

Stateful Services:
* Databases and caches, custom apps with large amounts of data, loss of a node is a notable event
* Dedicated Shards (anti-pattern): dedicated nodes for specific customers, single point of failure
* Redundancy is fundamental - EVCache (wrapper around memcached), write changes to multiple nodes in multiple availability zones. Want to read from same zone, can fall back to other zones (slower) if necessary

Hybrid Service:
* Example: Netflix Subscriber service
* Don't lean on EVCache too much, dangers of excessive load. Fallback to service/db, increases load, takes service down.
* Solutions: workload partitioning, request-level caching, secure token fallback (in case Subscriber fails)

### Variance

Operational Drift:
* Over time - alert thresholds, timeouts, fallbacks, throughput
* Across microservices - reliability best practices
* Exciting at first, becomes tedious quickly
* Make as many best practices as automatic as possible

Continuous Learning & Automation:
* Incident occurs, is resolved, reviewed, analyzed, best practice determined, automate it, get it adopted
* "Production Ready" - Alerts, autoscaling, chaos, ELB config, healthcheck, immustable machine images, squeeze testing, staging deploys , timeouts

Polyglot & Containers (Intentional Variance):
* While developing the "paved road" (Java, EC2), teams started introducing new tech (Python, Node, Docker)
* Push key endpoints out of API, into separate containers (Node), isolate and improve fault tolerance
* Cost of variance: productivity tooling, triage capabilities, base image fragmentation, node management, library/platform duplication (per language), learning curve (things will break in new and interesting ways!)
* Results in multiple "paved roads," prioritize by impact, seec reusable solutions

Integrated, Automated Practices:
* Spinnaker: conformity checks, red/black pipelines, automated canaries, staging

## Organization and Architecture

Electronic Delivery (early Streaming)
* Consumer device, download content, client and server teams worked together
* Netflix API, public at first, became valuable for internal use (metadata, JSON schema, oauth)
* Hybrid architecture: REST vs RPC, distinct schemas, security models, protocols
* Trying to find the right long-term solution might impact the organization

Conway's Law
* Any team working on a system will make it reflect their organization

Outcomes and Lessons:
* Productivity & new capabilities, refactored organization
* Solutions first, team second, reconfigure teams to reflect architecture

Health of services depends on discipline and chaos

http://netflix.github.io
