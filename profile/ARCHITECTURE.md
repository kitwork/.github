
# Architecture Overview

## A system designed around mobile logic

Kitwork is built around a single architectural premise:

**Logic is a movable unit of execution, not a static property of a server.**

Every component in the system exists to support this premise safely, efficiently, and at scale.

Rather than organizing the architecture around services, endpoints, or deployments, Kitwork organizes itself around the lifecycle of a **Logic Capsule**.


## Core building blocks

At a high level, the Kitwork architecture consists of five primary layers:

1. Client SDK
2. Gateway (Edge Layer)
3. Zone Command Layer
4. Worker Nodes
5. Federation Layer (Inter-Zone)

Each layer has a narrow responsibility and avoids leaking assumptions into others.


## Client SDK

The Client SDK is not a remote API wrapper.

Its role is to **capture intent**, not to execute business logic locally. When a developer writes a function through the SDK, that function is analyzed, partially evaluated, and serialized into bytecode.

Key responsibilities of the Client SDK:

* Scope capture and pre-evaluation
* Bytecode generation
* Capability declaration
* Gas estimation
* Signature attachment

The SDK deliberately avoids runtime execution of side effects. Its output is a **Logic Capsule**, not a result.

The client never “calls the database”.
It defines *what should happen*, not *where it happens*.


## Gateway (Edge Layer)

Gateways sit at the boundary of the network and operate under a zero-trust model.

They do not execute logic.
They do not make authorization decisions beyond verification.

Their responsibilities are strictly limited to:

* Identity verification
* Signature validation
* Basic capability sanity checks
* Traffic filtering and early rejection
* Routing to the appropriate Zone

This design ensures that malformed or malicious logic is discarded as early as possible, reducing pressure on the core system.

Gateways are stateless and replaceable. Any Worker Node may temporarily assume the Gateway role if needed.


## Zones and the Command Layer

A Zone represents an autonomous execution domain. Zones are not merely geographic regions; they are **units of trust, consensus, and resource accounting**.

Each Zone contains a Command Layer composed of:

* One Leader
* Multiple Followers

The Command Layer is responsible for deciding whether a Logic Capsule may execute within the Zone.

Decisions are made via consensus. No single node has unilateral authority.

Responsibilities of the Command Layer include:

* Capability verification
* Gas budget enforcement
* Resource availability assessment
* Consensus-based admission control
* Execution authorization

Only after consensus is reached is logic released to the execution layer.


## Worker Nodes

Worker Nodes are responsible for actual execution.

They host the Kitwork Virtual Machine and manage the transition from interpretation to JIT compilation.

Execution flow inside a Worker Node follows three phases:

1. Initial interpretation for safety and observation
2. Hot path detection
3. Native compilation via JIT

Worker Nodes are intentionally unaware of global system state. They execute only what they are authorized to execute and only for as long as gas permits.

This isolation ensures predictable behavior under load and simplifies failure handling.


## Gas and execution limits

Gas is a fundamental architectural constraint.

Every opcode has a cost.
Every execution consumes gas.
No execution is infinite.

Gas accounting is enforced at the VM level and cannot be bypassed by logic itself.

This design eliminates entire classes of failure modes, including infinite loops, uncontrolled recursion, and resource starvation.


## Federation and inter-zone execution

Zones are autonomous but not isolated.

When logic requires data or execution in another Zone, the system performs an **inter-zone handover** rather than remote invocation.

In this process:

* Execution state is snapshotted
* Capabilities are revalidated
* Gas budgets are renegotiated
* Control is transferred to the target Zone’s Command Layer

The logic continues execution without assuming shared memory, shared trust, or shared infrastructure.

This enables horizontal scaling without a global coordinator.


## Failure as a normal condition

Kitwork assumes failure as a normal state, not an exception.

Nodes may disappear. Zones may become unreachable. Gateways may fail.

The architecture avoids tight coupling and long-lived assumptions. Consensus boundaries, stateless edges, and bounded execution ensure that failure degrades capability, not correctness.


## What this architecture intentionally avoids

Kitwork does not attempt to be:

* A general-purpose blockchain
* A traditional microservices framework
* A replacement for all existing runtimes
* A system with implicit trust boundaries

Its scope is intentionally constrained to **safe, mobile execution of logic at scale**.


## Architectural stance

Kitwork’s architecture is not optimized for familiarity.

It is optimized for clarity of responsibility, explicit limits, and long-term scalability under uncertainty.

Every component exists to answer a single question:

**Can this logic exist here, right now, safely?**

Everything else is secondary.

[@huynhnhanquoc](https://github.com/huynhnhanquoc) - 2026.19.01
