# Contributing

This list is curated, not exhaustive. Every entry is something we use, trust, or would put in a client project tomorrow. A pull request that adds a resource is a claim that it clears that bar.

## What belongs here

A resource qualifies when all of these are true:

- **It is standalone.** It installs into any shadcn project — a registry URL, a `shadcn add`, or an npm package — and works with Tailwind plus the shadcn primitives alone. A library that only runs inside a specific CMS, backend, auth provider, or app framework is out.
- **It has a real reason to exist.** It does something the resources already listed do not, or does it clearly better. Near-duplicates need the distinction spelled out in the entry.
- **It is alive.** Links resolve, the registry serves, the docs are current. Verify every link before opening the PR.
- **It is ours to recommend.** We have used it, or we would.

One exception is already on the list: [Supabase UI](README.md#supabase-ui) ships components wired to a backend. It stays because the coupling *is* the value and the entry says so in its "Reach elsewhere when" line. A backend-coupled or framework-coupled proposal needs the same treatment — name the coupling and name what to use instead when the project does not have it.

## Two hard requirements

A PR without either of these is not ready:

1. **A banner** at `assets/banners/<slug>.png` — see [Banner](#banner).
2. **A component list** — every component the resource offers, in a table, each with a direct link. See [Component table](#component-table).

Partial lists are worse than no entry: an agent reading a short table concludes the missing component does not exist.

## Entry format

Copy this shape. Section headings (`## Components`, `## Loaders`, …) already exist — add your entry inside one, or open a new section and add it to the table of contents.

```markdown
### [Name](https://link-to-the-most-useful-page)

![Name](assets/banners/name.png)

One or two sentences on the character of the thing. What it actually is, not what its landing page says.

**Reach for it when** the concrete situation that makes this the right pick — a task, not a feature list.

**Reach elsewhere when** the neighbouring entry that wins instead, linked, and why.

<details>
<summary><strong>N components</strong></summary>

| Component | Use when |
| --- | --- |
| [Component](https://direct-link-to-the-component) | The situation that should trigger this component. |

</details>
```

Rules that keep the file consistent:

- Link the heading to the most useful page: the registry, the docs index, the component itself — not a marketing home page.
- `Reach elsewhere when` must point at another entry in this list with an anchor link. If nothing here competes, say what kind of resource wins instead.
- Anything unusual about installing or theming goes as a plain paragraph after the three lines — see [Thinking Orbs](README.md#thinking-orbs) for the pattern.
- Components and Loaders are alphabetical. Insert, do not append.
- Update the table of contents in the same commit.

## Component table

Extract *all* components from the registry, not the featured ones. The registry JSON is usually the fastest source of truth.

- One row per component, in the order the registry lists them.
- Link each row to the component's own page or its registry JSON — whichever the resource actually offers.
- Count in the `<summary>`: `12 components`, `36 transitions and 2 Pro transitions`, `15 components and 6 blocks`. Say what the numbers are when they are not all components.
- The `Use when` cell names the situation, not the API. Write the trigger an agent can match a task against.

Good: `The agent is about to do something irreversible and must stop and ask.`
Not: `A card with confirm and cancel buttons.`

## Banner

Every entry carries a 16:9 banner under its heading.

- **File**: `assets/banners/<slug>.png`, PNG, exactly 1600 × 900. Slug is kebab-case of the name.
- **Content**: a grid of real screenshots from the resource's own site — the registry page plus three of its component pages — with the logo and name centered on top, and a kicker naming the section and the component count.
- **Capture**: headless Chromium, dark colour scheme, so tiles match across entries.
- **Contrast**: chip colour and tile brightness derive from the logo and the screenshots, so white logo marks stay readable in light-mode docs.

No mockups, no stock art, no hand-made collages. The tiles show the components the entry is about.

## Removing a resource

Dead link, abandoned registry, or superseded by a better entry: remove it, and remove everything that pointed at it — the table-of-contents line, the banner file, and any `Reach elsewhere when` line in another entry that linked to it. A dangling anchor is a broken entry.

## Before you open the PR

- [ ] Every link opens, including each row in the component table.
- [ ] Component table is complete and the count in `<summary>` matches the rows.
- [ ] Banner exists, is 1600 × 900, and is referenced with the right path.
- [ ] Table of contents updated.
- [ ] Entry sits in the right section, in the right position.
- [ ] `Reach elsewhere when` links to a real anchor.
- [ ] Written in English, short and practical. No marketing copy.
