# Use Typescript instead of JsonSchemas

## Status

Accepted

## Context

There are difficulties involved with maintaining a json-schema and typescript typing separately.

One of the difficulties is the need to rebuild validation and parsing logic whenever dealing with ingestion of data.

While working on validating the data that is ingested by other tools, there was a need to reimplement the schema in other technologies, and [zod](https://zod.dev/) was chosen as the easiest approach.

Since this new approach requires typescript modules to be written, contributing with completely new schemas will be more difficult for the less technically-inclined.
Hopefully, on this matter, open-source and clearly documented projects will help others create their own schemas with relative ease.

In terms of distribution, the difficulty to dynamically import the typescript types and perform validation with them makes it hard to distribute and integrate modules.
For the time being, this means most changes will be up-streamed and treated as part of the 'core'.

This decisions should eventually be reevaluated to address the needs of users looking to publish modules without the need to integrate with any central repository.

## Decision

The JsonSchema approach will be replaced by zod validators plus Typescript types (generated from the zod validators).

## Consequences

- JsonSchema will be deprecated.
- Content created with jsonschema in mind will have to be migrated to support the new approach
  - Or the current tooling will be extended to support the new schemas
- New schemas will have to be up-streamed in order to work seamlessly with the tooling (until an new approach can be considered)