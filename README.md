# Solid

A code-quality reference for object-oriented code, packaged as a skill your agent reads on request.

**It is user-invoked.** The agent will never pull it in on its own — someone has to type `/solid`. That is deliberate: an always-on code-quality skill fires on every edit and starts rewriting code nobody asked it to touch. The cost of that choice is that the skill is invisible until you remember it. This page is how you remember.

---

## When to type `/solid`

Reach for it when the **shape** of the code is the question:

| Say something like | And you get |
|---|---|
| "`/solid` — review this service" | The class read against SRP, cohesion, and the smell catalogue |
| "`/solid` — refactor this to use value objects" | Domain primitives wrapped, with the validation moved inside them |
| "`/solid` — where should this module sit?" | Layer and feature placement, dependency direction checked |
| "`/solid` — this switch keeps growing" | The polymorphic replacement, or a reason to leave it |
| "`/solid` — help me test-drive this" | Red-green-refactor with the loop's rules applied |

## When not to

Skip it for anything where the shape isn't the point — a one-line fix, a config change, a dependency bump, chasing a bug. Typing `/solid` there loads 3,000 lines of design reference to answer a question that isn't about design.

Examples are written in TypeScript because one language had to be picked. Nothing here is framework-specific, and the principles carry to any object-oriented codebase.

---

## What it will and won't do

The whole skill runs on one rule, stated at the top of `SKILL.md`:

> A **smell** is a question, not a verdict.

Every threshold in these files — 10-line methods, 50-line classes, two instance variables per class — marks a place worth looking, not a licence to rewrite. The agent should cross a threshold, ask why, and change the code **only when it can name a concrete cost**: a test it can't write, a change that touches six files, a bug the shape invited.

So you should expect it to:

- **Fix what you asked for**, and mention the smells it passed rather than acting on them
- **Leave framework code alone** — types your framework reads or constructs (request/response objects, ORM models, serialised config) follow its shape, and these rules yield to it
- **Justify a refactor by cost**, not by a line count

If it starts splitting a perfectly good 15-line function into four three-line ones, it has broken that rule. Say so, and it should back out.

---

## What's in it

`SKILL.md` is a router — about 60 lines. It holds the smell rule and points at nine reference files, each owning one concept.

**Running the loop**

- `tdd.md` — red-green-refactor: what to fake, when to triangulate, how far a transformation may jump
- `testing.md` — shaping a test: pyramid level, which double, contract tests, builders, naming

**Writing the code**

- `clean-code.md` — naming, parameter counts, function size, guards over nesting, the nine object-calisthenics rules
- `code-smells.md` — the catalogue, and the refactoring that answers each one
- `solid-principles.md` — SRP, OCP, LSP, ISP, DIP applied to a class or module

**Designing the shape**

- `object-design.md` — what an object owns: stereotypes, Tell-Don't-Ask, value objects vs entities, aggregates, Law of Demeter
- `complexity.md` — essential vs accidental: YAGNI, KISS, DRY, the Rule of Three
- `architecture.md` — placing code across features and layers: dependency rule, vertical slicing, hexagonal and clean
- `design-patterns.md` — naming a pattern already emerging from a refactor

### One owner per concept

Concepts are defined once and cross-referenced, so there is no second, drifting copy to read:

| Concept | Lives in |
|---|---|
| Value objects, Tell-Don't-Ask, Law of Demeter, polymorphism over switch | `object-design.md` |
| YAGNI, KISS, DRY, Rule of Three | `complexity.md` |
| Object calisthenics, naming, function size | `clean-code.md` |
| The dependency rule | `architecture.md` |
| Arrange-Act-Assert, test naming | `testing.md` |

---

## Install

Copy the skill folder so `SKILL.md` sits at the skill root:

```bash
cp -r skills/solid <your-repo>/.claude/skills/solid
```

Commit `.claude/skills/solid/` and every teammate gets `/solid` on checkout. Confirm with `/solid` — if nothing fires, `SKILL.md` is nested too deep.

## Contributing

The reference files are the source of truth; `SKILL.md` routes and must not restate them. When you add a concept, give it **one** owner file and cross-link the mentions.

## Credits

Clean code practices in `clean-code.md` include concepts from the **"Clean Code" course summary** by [Academind GmbH / Maximilian Schwarzmuller](https://academind.com) (c) 2020.

## License

MIT
