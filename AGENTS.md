# AGENTS.md — Carve Studio – awesome-shadcn

## Build/Test Commands
- **Install deps**: `bun install` (or `bun i`) — never npm/yarn/pnpm, always from repository root
- **Run unit tests**: `bun test`
- **Formatting**: `bun run format`
- **Type checking**: `bun run check-types`

## Tools
- **Use Bun over Node.js**: `bun <file>` instead of `node <file>`
- **Built-in APIs**: Use `Bun.file` over `node:fs`, `WebSocket` over `ws`
- **Environment**: Bun auto-loads .env, don't use dotenv
- **Code search & refactoring**: Use `ast-grep` CLI for pattern search and large-scale refactoring
- **Website content as Markdown**: If you need a website's content in Markdown, use `https://r.jina.ai/[website-url]` (e.g. `https://r.jina.ai/impeccable.style` or `https://r.jina.ai/https://kentcdodds.com/`)
- **Always install new packages with `@latest`**: e.g. `bun add <package>@latest` — never specify a version number manually
- **Always use Context7 for library/API documentation, code generation, setup or configuration** — do not rely on training data for library usage. Search for library id with `bunx ctx7 library "[library name]"` and search docs with `bunx ctx7 docs "[library]" "[docs search query]"`

## Modus Operandi
- Think before coding: don't assume, surface tradeoffs, and ask when confused
- State assumptions explicitly and present multiple interpretations when ambiguity exists
- Push back when a simpler approach solves the problem
- Simplicity first: write the minimum code that solves the problem
- No speculative features or "future-proofing" that wasn't requested
- No over-complicated abstractions
- Make surgical changes: touch only what is necessary and clean up only your own mess
- Don't refactor or "improve" adjacent code, comments, or formatting unless it is required for the task
- Match the existing style, even if it differs from your preference
- Work goal-first: define clear success criteria and loop until verified
- Use TDD: think about what tests make sense → write them → implement the code
- When fixing bugs, prefer creating a test that reproduces the bug first, then make it pass
- For multi-step tasks, use explicit steps and verification
- Always leave the codebase in a better state than you found it (quality, test coverage, simplicity, readability)

---

## Contributing Shadcn Resources
- Only add resources that we actually use, trust, or would confidently use in client or internal projects
- Prefer quality over quantity: this repo is curated, not exhaustive
- Every new resource must have a clear practical reason to exist in the list
- Keep the README structure consistent: update the table of contents when you add a new top-level section or registry
- Group resources under the right section, such as `Official` or `Registries`
- For every top-level resource or registry, add a short summary and a `Use when` explanation
- When adding a registry, always extract all available components from that registry and list them with direct links
- For every linked resource entry, include a concise `Use when` description that explains the real project use case
- Prefer direct links to the most useful page, such as the actual component, docs, or registry page
- Verify that links are live before adding them
- Match the current README writing style: short, practical, curated, and team-oriented
- Do not add filler descriptions, marketing copy, or vague recommendations
- Do not add duplicate resources or near-duplicates unless there is a strong reason and the distinction is explained
- When removing a resource, also remove stale table-of-contents entries and surrounding copy that no longer fits

---

## General Styleguide
- Write everything in English
- Writing tone should be IKEA-style
- German UI translations: use informal `du` (never formal `Sie`), warm, simple, and concise (IKEA-style)
- You are rewarded for simplifying code
- Prefer functional patterns (map over forEach, pure functions), never write classes
- Write clear, speaking variable and method names
- Always create a single source of truth and reduce duplication
- Think like shadcn: modularity, composition, simplicity
