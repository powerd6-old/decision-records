# Use Typescript instead of JsonSchemas

## Status

Accepted

## Context

There are difficulties involved with maintaining a json-schema and typescript typing separately.

One of the difficulties is the need to rebuild validation and parsing logic whenever dealing with ingestion of data.

While working on validating the data that is ingested by other tools, there was a need to reimplement the schema in other technologies, and [zod](https://zod.dev/) was chosen as the easiest approach.

## Decision

The JsonSchema approach will be replaced by zod validators plus Typescript types (generated from the zod validators).

## Consequences

- JsonSchema will be deprecated.
- Content created with jsonschema in mind will have to be migrated to support the new approach
  - Or the current tooling will be extended to support the new schemas