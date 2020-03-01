# Contributing to Tavern

The following is a set of guidelines for contributing to Tavern and its various sub-projects.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Style Guides](#style-guides)

## Code of Conduct

**TL;DR: Play nice**

Should this project grow and issues arise requiring a more official code of conduct, one will be added.
In short, no flaming, doxxing, or anything else generally frowned upon on the public internet. Take
the time to try to understand someone's point of view. It is okay to appropriately discriminate against
ideas and code, provided proper reasoning and a good-faith attempt to indicate how they can be improved;
otherwise, no discriminating against people for their identity. That said, these repositories and all
issues, discussions, etc. will focus only on Tavern and topics directly related to is and its usage.

## Style Guides

The following style guides outline how things should be written, from code to documentation and otherwise.
Pull requests not following these style guides may be temporarily rejected until they are brought in line
with these style guides.

### Git Commit Messages

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or less
- [Reference issues and pull requests](https://help.github.com/en/github/writing-on-github/autolinked-references-and-urls)
  liberally after the first line. To make understanding commit messages without GitHub easier, provide enough contextual
  information to know which issue or pull request is being referenced.
- When only changing documentation, include `[ci skip]` in the commit title

Example:

```
Add git commit message example

Fixes issue #1 (provide git commit message example).
Supersedes pull request #4.
The example was written to demonstrate how to link to
issues and pull requests, as well as how to explain
the rationale behind a particular implementation detail.
```

### Common Programming Guidelines

- Prefer compile-time errors to runtime whenever possible.
- No "magic numbers": All values (not just numbers) corresponding to a piece of business
  logic should be used via a named constant rather than literal values. It makes the code
  more readable as well as easier to change (see ETC below) if that value ever needs changing.
- Use short but descriptive variable names.
- Separate public interface from private implementation
  - This means that consumers of a public API (including other parts of the same codebase)
    should not need to know how the API is implemented in order to use it. For example, it
    should not matter if a list-like collection is implemented using fixed-length arrays,
    dynamically-sized arrays, or singly- or doubly-linked lists; the API should remain the
    same if the implementation is replaced.
  - This may also mean writing wrapper functions around the implementation-specific version.
    For a list-like collection, this would mean a custom `at()` method that calls the
    array/linked list `at` method.
- Follow DRY, ETC, and YAGNI principles:
  - DRY (Don't Repeat Yourself): a particular piece of business logic should only be written
    in one place and referenced eleswhere.
    - The same lines of code in the same place, if their applications are completely different
      and one could be changed without requiring the other to be changed, are not violations
      of DRY.
  - ETC (Easy To Change): Everything (code, data, etc.) should be written to make it easy to
    change. DRY applies here, as well as good modularization and decoupling between modules.
    Generally speaking, the fewer things that need to be changed if any one thing changes,
    the better.
  - YAGNI (You Aren't Gonna Need It): No implementing "cool things we might use later." If
    it's not on the plan/task list, don't worry about implementing it. If you think it
    should be added to the plan/task list, open a discussion about it. Then, once it is
    added, feel free to put it into code.

### Common Comment/Documentation Guidelines

- Non-documentation comments should explain *why* the code was written a particular way, not
  *how* it was written. If the steps of what is happening are not understandable, the code
  should probably be rewritten.
- Documentation comments should provide a thorough explanation of the general behavior of
  the thing being documented, will minimal reference to private implementation details. A `sort()`
  function does not need to share which algorithm is used, only that it sorts the collection.

### C++

- Avoid compiler-specific features whenever possible (use of a compiler-specific feature
  must be accompanied by a explanation for why it was used).
  - This also means using the `#ifndef` [header guard](https://www.learncpp.com/cpp-tutorial/header-guards/)
    rather than `#pragma once`
- Do not rely on implementation-specific/undefined behavior.
- Provide appropriate error checking and recovery for all possible errors.
- Use appropriate custom types to group related data (structs, classes, etc.).
  - e.g. use a `Point` struct instead of two `int`s.
- Contributed code should not cause any compiler warnings.
- Naming guidelines:
  - Custom types (enums, classes, etc.): `UpperCamelCase`
  - variables, functions: `lowerCamelCase`
  - constants: `SCREAMING_SNAKE_CASE`
- For projects with a `.clang-format` file, submitted pull requests should match the provided format.
  Please report any discrepancies between a `.clang-format` file and the above requirements.

### Rust

- Try to minimize the number of dependency crates by enabling only the features required for each
  dependency.
- For projects with a `.rustfmt.toml` file, submitted pull requests should match the provided format.
  Please report any discrepancies between a `.rustfmt.toml` file and the above requirements.
- **TBD**

### Qt

**TBD**
