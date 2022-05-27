# Technology and stack

## Status

accepted

## Context

Before starting development, choosing a technology stack will allow us to study and prepare before we touch any lines of code.

While there are multiple paradigms and implementation possible, the most popular and well-known to us are going to be considered, rather than an exhaustive list.

To make this analysis possible we will start by slicing the project in parts:

- Models
- Content
- Behaviour

### Models

Models are specifying the structure of the data we have, and their relationships.

The contenders are:

- JSON schema
- Protocol Buffers
- programming language "class"
- database schema
- free-form text specification (like an RFC)

### Content

Content is the fulfilment of the models, with information that makes those models represent things.

The contenders are somewhat related to the choices in models, but there is some flexibility:

- JSON
- YAML
- xml
- other structured text formats
- programming language "static object"
- database entries

### Behaviour

Behaviours define how models interact with themselves and other models. They closely resemble the concept of rules, but can also be more removed from the gameplay than that, like, application code, validation, tools, etc.

The contenders are all programming languages, or abstractions of the same built on top of other formats (like [JSONlogic](https://JSONlogic.com/), for example).

### Programming languages

A lot of the slices proposed before have options that refer to programming languages, as such, considering which ones to use is also relevant.

Once again, there are myriads of possibilities, so the ones considered are based on personal taste.

Here are the contenders, together with apparent pros and cons:

- JavaScript
  - pros:
    - web-native
    - popular
    - full-stack
  - cons:
    - poor typing (fixed by tools like Typescript)
    - very sharp hard edges
    - slower than other languages in this list
- jvm languages (java, kotlin, etc)
  - pros:
    - well-structured
    - somewhat popular with older generation of developers
    - better at back-end than front-end (except on Android, or using other languages in-jvm)
  - cons:
    - not very liked
    - not as flexible as other options
- dart (& flutter)
  - pros:
    - comfortable language features
    - can be used to write native applications in all platforms
  - cons:
    - repetitive when dealing with structured formats
    - not as popular, and therefore with a smaller ecosystem
- go
  - pros:
    - lightweight
    - performant
  - cons:
    - weak language feature (simplicity at a cost)

### Examples

Each scenario will have a more detailed section below this table, exploring some possible options that came up during brainstorming.

| Scenario                              | Models                       | Content          | Behaviour                | Programming Languages    |
| ------------------------------------- | ---------------------------- | ---------------- | ------------------------ | ------------------------ |
| JSON + JavaScript                     | JSON-schema                  | JSON             | JavaScript               | JavaScript               |
| YAML + JavaScript                     | JSON-schema?                 | YAML             | JavaScript               | JavaScript               |
| database + programming language       | database schema              | database entries | Any programming language | Any programming language |
| static objects + programming language | programming language classes | static objects   | Any programming language | Any programming language |

#### JSON + JavaScript

This seems to be a natural combination. These technologies interact well together and have a robust ecosystem.

The weaknesses that could come up are:

- JSON is not capable of referencing other elements without extensions
- JSON is not ideal for binary formats like images, files, etc
- JavaScript is weakly typed

Some remediation measures that could be put in place are:

- use appropriate JSON extensions to enrich JSON behaviour
- create a standard for storing binary data with filepath referencing
- use an appropriate JSON extension to encode binary data into JSON-friendly formats
- use typescript to enforce strong-typing in JavaScript source code

#### YAML + JavaScript

Similar to the scenario above, with similar limitations about binary formats on content.

In theory YAML is capable of cross-referencing and making somewhat dynamic objects, but most implementations don´t leverage this power.

Also, YAML is a super-set of JSON, so it could be used on top of existing JSON if such evolution was necessary at another point in time.

#### database + programming language

Using a database to store data sounds like a good strategy at first.

Regardless of the chosen programming language, some effort can be expected to map and connect to such database.

The weaknesses that could come up are:

- centralized databases would make extending content harder
- decentralized databases would require a high-complexity of integrations
- most interfaces between databases and programming languages are complicated to understand for non-programmers
- there may be infrastructure costs associated with such a solution

#### static objects + programming language

Using a single programming language to reflect all aspects might sound simple at first.

The limitations are that contributors would need to learn it, and choosing the wrong language would have massive impact, as there would be low or none data portability.

Most programming languages are not great at dealing with constant instances of their objects, making them feel second-class and not a good fit to represent such things.

## Decision

- Use Protocol Buffer for modelling objects
  - Optionally export the protobuf objects to JSON-schema if more convenient
- Use JSON for the content creation (data)
  - Leverage markdown for text-processing inside the content data.
- Use Typescript for behaviour and tooling
- Consider using "code-generation" tools to create language-specific implementations if necessary.

## Consequences

- A template for typescript projects should be created, with all relevant tooling and standards integrated on them.
- Work on modelling objects with Protocol Buffers
- Creating content will have to use JSON and markdown, with a strict model.