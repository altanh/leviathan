# Leviathan Design Document
This document lays out the WIP design of Leviathan, a highly approximate model of 'societal' behavior.
It will be subject to frequent change as better design choices become apparent.

## Leading Questions
- Can certain societal behaviors be effectively modeled as multiagent problems?
    - See Wooldridge "Intro. to Multiagent Systems"
- What specific techniques might be applicable? To what situations?

## Problem(s) and Objective(s)

## Scope and Granularity
Before making any design decisions, it will help to first lay out expectations for the scope and
granularity of the project. By this, we mean both the breadth of the simulation, and the depth
of individual components of the simulation. It may be feasible to have a wide breadth of interacting
components, but each of those components have little to no internal behavior. Conversely, we may
wish to have few components, but each one having high detailed internal behavior (or subcomponents,
in a sense). This is a fairly smooth two dimensional design space.

### The Physical World
For computational reasons, it seems infeasible to simulate the physical world to any degree beyond
high level system interactions. As such, we will not simulate any real-time Newtonian (or beyond)
physics. Large-scale systems like weather and day-night cycles are more readily simulated, and their
effects on society are easier to reason about.

Regardless of the granularity, the simulation must occur in a physical world, so we will need a way
of representing the space in/on which we simulate. There are multiple choices here, with unclear
effects. We could simluate the world as a bounded plane, with hard 'walls' at the edges that can be
thought of as inpenetrable obstacles. Alternatively, we could simulate the world as a sphere,
parametrized by two angular coordinates. This removes the unnatural walls. Leaving the 2D realm, we
could represent the world abstractly as a graph, with (potentially weighted) edges representing paths
between nodes representing locations.

### Agents
A person/sentient being/member of society in Leviathan is called an *agent*. In most respects, agents
are the primary subjects of this simulation. For this reason, they deserve the most detail (i.e. the
highest granularity). Agents have *intrinsic components*, like a measure of health (which may be
further deconstructed), maybe some kind of memory, etc. They also have *extrinsic components* which are tied to the society/world in some capacity, like capital or relationships. Agents also have
*sensors*, which digest the physical world into actionable information. Naturally, agents then have
*motors* which allow them to affect the physical world.

**Question.** Is this too much detail?

### Resources
Resources will likely have a range of granularities - things like water probably don't need anything
beyond potability and quantity properties, while things like stocks (which are 'artificial' resources,
in a sense) will have more properties like price, volatility, sentiment, etc.
