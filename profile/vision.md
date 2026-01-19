# Kitwork Engine and Living Logic

## When logic escapes static form and the Internet becomes an execution space

Software today appears flexible, but that flexibility ends at build time.

Once compiled and deployed, logic becomes fixed. JavaScript stays inside the browser. Go, Rust, and C remain locked in data centers. Communication between these isolated logics is forced through rigid interfaces: APIs, RPCs, schemas, versions. We call this architecture, but it is largely a workaround for immobility.

Kitwork begins from a simple but uncomfortable question:

**Why must logic stay in one place?**

## Logic separated from place

Kitwork is built on the idea that logic should not be bound to a specific process, server, or deployment unit.

Instead of sending requests that describe *what to do*, a system can send the *logic itself*—captured, constrained, and executable elsewhere. Logic becomes mobile. Execution becomes contextual.

This separation of logic and place is the core principle of Kitwork.

## Logic Capsules

In Kitwork, logic is packaged as a **Logic Capsule**.

A Logic Capsule is not source code. It is a snapshot of intent, serialized into bytecode, accompanied by explicit permissions and resource limits. It carries no assumptions about language, runtime, or location.

From the system’s perspective, a capsule is simply bytes. From an architectural perspective, it is a portable unit of computation.

Every capsule is evaluated before execution. Nothing runs by trust. Nothing runs by default.

## A developer-facing abstraction

Kitwork does not require developers to think in bytecode.

Through a DX-oriented SDK, logic can be written declaratively and captured transparently:

```javascript
const connect = await kitwork.connect({
  server: "asia",
  appId: "webapp",
  token: GuestToken
})

const logic = await connect(() => {
  return from("users")
    .where(u => u.active === true)
    .limit(10)
})

const bytecode = logic.serialize()

const res = await fetch("/kitwork/run", {
  method: "POST",
  headers: {
    "Content-Type": "application/octet-stream",
    "Authorization": "Bearer " + token
  },
  body: bytecode
})

const users = await res.json()
renderUsers(users)
```

Here, the client does not query a database.
The client defines *intent*.
Execution happens where it is allowed, affordable, and valid.

## Zero trust by construction

Kitwork assumes no actor is trustworthy—not the client, not the server, not even the execution node.

Before execution, every Logic Capsule is pre-evaluated. Capabilities define what the logic may do. Gas defines how long it may exist. When either boundary is crossed, execution stops.

There are no implicit admin privileges.
There is no unlimited execution.
There is no invisible authority.

Every action leaves a trace.

## Beyond microservices

Kitwork does not embed databases into clients, nor does it push runtimes to the edge by default.

Instead, it allows logic to **move toward the data**, execute within constrained zones, and relocate when conditions change.

This represents a shift in architectural evolution:

Monolith
Microservices
Serverless
Edge Computing
**Logic Mobility**

At this stage, the concept of a fixed backend becomes less meaningful.

## Zones, consensus, and deliberate execution

Logic Capsules do not execute immediately upon arrival.

They pass through a regional command layer where leaders and followers validate signatures, capabilities, and resource constraints using consensus mechanisms. No single node decides alone.

Gateways operate under zero-trust assumptions. Failure of a node does not imply failure of the system. Execution authority is distributed by design.

## Gas as a physical limit

Gas is not currency.
Gas is energy.

Each operation consumes gas. Logic cannot run indefinitely. When gas is depleted, execution ends. This limitation is not a restriction—it is what makes the system stable.

Zones under heavy load become expensive. Logic migrates naturally. Load balancing emerges without central coordination.

The system behaves less like infrastructure and more like an ecosystem.

## Living logic

At runtime, Kitwork applies observation and JIT compilation. Logic begins interpreted, then becomes native when it proves valuable.

Logic is mobile, but not slow.
Dynamic, but not uncontrolled.

At this point, software is no longer static. It has identity, permission, lifespan, and cost. Engineers no longer only write code. They design logical entities and define how they live.

## An open ending

Kitwork is not a finished product.
It is a different way of thinking about computation.

When logic is no longer bound to place, the Internet stops being merely a transport layer. It becomes an execution space.

Every shift in computing history has begun at such a boundary.

This project stands at one of them.

[@huynhnhanquoc](https://github.com/huynhnhanquoc) - 2026.19.01
