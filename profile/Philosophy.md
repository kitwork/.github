# Philosophy

## On the separation of logic and place

Software has long been shaped by a quiet assumption:
that logic belongs to the place where it was deployed.

We compile code, place it inside a process, bind it to a server, and then spend most of our architectural effort building ways to *reach* it. APIs, gateways, protocols, retries, versions. These are not features of logic itself, but compensations for its immobility.

Kitwork begins by rejecting that assumption.

Logic does not inherently belong to a machine, a process, or a region.
Those are conveniences of implementation, not truths of computation.

## Logic as intent, not location

In most systems, a request describes *what should happen*, but execution remains trapped behind a fixed boundary. Logic is static. Only data moves.

Kitwork treats logic as intent that can be captured, constrained, and moved. Execution is not predefined by deployment, but negotiated at runtime.

This distinction matters.

When logic is mobile, the question is no longer “Where is my backend?”
The question becomes “Where should this logic exist *right now*?”

## Distrust as a first principle

Trust is fragile at scale.

Modern systems often rely on implicit trust: trusted servers, trusted admins, trusted internal networks. These assumptions work until they don’t.

Kitwork assumes distrust by default.

No logic is trusted because of where it comes from.
No execution is allowed because of who sends it.
No authority is unlimited.

Instead, every unit of logic carries explicit capability and explicit limits. What it may do and how long it may exist are part of the logic itself, not an external promise.

Security emerges from constraint, not permission.

## Gas as a boundary of existence

Every living system is defined by its limits.

In Kitwork, gas represents the physical boundary of logic. It is not a token of value, but a measure of existence. When gas is exhausted, logic ends. No exception, no override.

This limit is not punitive. It is stabilizing.

Unbounded execution is a myth that collapses systems. Bounded execution creates ecosystems.

## Decentralization without mythology

Kitwork does not attempt to replace infrastructure with ideology.

Consensus exists where authority must be shared. Centralization exists where coordination is cheaper. Distribution is used deliberately, not universally.

There is no promise of utopia, only an insistence on clarity.

Decentralization is a tool, not a belief.

## From programs to entities

Traditional software is static. It is deployed, executed, and forgotten.

In Kitwork, logic behaves more like an entity. It has identity, permission, cost, and lifespan. It can appear, move, execute, and disappear.

The role of the engineer shifts accordingly.

No longer only writing functions, but shaping behavior.
No longer deploying systems, but defining conditions for existence.

## An unfinished stance

This philosophy is not complete.

It is not a manifesto, nor a conclusion. It is a position taken at the edge of existing systems, where familiar abstractions begin to fail.

Kitwork does not claim to be the future.
It claims only that the present assumptions are insufficient.

Everything else remains open.

--- 
[@huynhnhanquoc](https://github.com/huynhnhanquoc) - 2026.19.01
