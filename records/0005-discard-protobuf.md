# Discard Protobuf

## Status

accepted, complements [0004-technology-and-stack.md](./0004-technology-and-stack.md)

## Context

After trying to use Protocol Buffers to standardise how models are defined and built, several limitations and difficulties were faced.

## Decision

With the inconveniences that protobuf brings, it's theoretical value is no longer enough to justify the hardships.

Protocol Buffers will be replaced by their simpler JSON schema format.

## Consequences

- JSON Schemas will be the default way of defining models.
