---
name: solid
description: SOLID, TDD, clean code and OO design reference for object-oriented codebases.
disable-model-invocation: true
---

# Solid

Reference for writing and reviewing object-oriented TypeScript. Nine files, one concept each. This file routes; the references hold the material.

## Everything here is a smell

A **smell** is a question, not a verdict. Every threshold in these files — 10-line methods, 50-line classes, two instance variables — marks a place worth *looking*.

Cross one and ask why. Change the code when the answer names a concrete cost: a test you can't write, a change that touches six files, a bug the shape invited. No cost, no edit — leave working code alone.

This binds hardest when the user asked for something else. Fix what was asked, note the smell, move on.

## Where the material lives

**Running the loop**

| Reach for | When |
|---|---|
| [tdd.md](references/tdd.md) | Driving red-green-refactor: what to fake, when to triangulate, how far a transformation may jump |
| [testing.md](references/testing.md) | Shaping a test: which pyramid level, which double, contract tests, builders, what to name it |

**Writing the code**

| Reach for | When |
|---|---|
| [clean-code.md](references/clean-code.md) | Naming, parameter counts, function size, guards over nesting, the nine object-calisthenics rules |
| [code-smells.md](references/code-smells.md) | You can name what's wrong and want the refactoring that answers it |
| [solid-principles.md](references/solid-principles.md) | Applying SRP, OCP, LSP, ISP or DIP to a class or module |

**Designing the shape**

| Reach for | When |
|---|---|
| [object-design.md](references/object-design.md) | Deciding what an object owns: stereotypes, Tell-Don't-Ask, value objects vs entities, aggregates, Law of Demeter |
| [complexity.md](references/complexity.md) | Judging complexity as essential or accidental: YAGNI, KISS, DRY, the Rule of Three |
| [architecture.md](references/architecture.md) | Placing code across features and layers: the dependency rule, vertical slicing, hexagonal and clean layouts |
| [design-patterns.md](references/design-patterns.md) | Naming a pattern already emerging from a refactor |

## One owner per concept

A concept is defined in exactly one file. Follow the mention to its owner rather than working from the mention:

| Concept | Owner |
|---|---|
| Value objects, Tell-Don't-Ask, Law of Demeter, polymorphism over switch | `object-design.md` |
| YAGNI, KISS, DRY, Rule of Three, simple design | `complexity.md` |
| Object calisthenics, naming, function size | `clean-code.md` |
| The dependency rule | `architecture.md` |
| Arrange-Act-Assert, test naming | `testing.md` |

## Scope

Any object-oriented codebase. Examples are TypeScript because one language had to be picked; the principles are language-agnostic.

Two things outrank these rules. **Framework convention**: types a framework reads or constructs — request/response objects, ORM models, serialised config — follow that framework's shape, and the calisthenics rules in `clean-code.md` yield to it. **The host language's idiom**: what reads as natural in the language wins over a rule imported from another one.
