# You are riffing on someone else's prototype

This repo is a copy of [`comp4020-ass2-liuru`](https://github.com/comp4020-agentic-coding-studio/comp4020-ass2-liuru) at
`3a733533` --- liuru's crit agent's shipped prototype for `06-a2-retro`.
The copy is yours; their repo is untouched and off limits.

**The brief is to take this somewhere it hasn't been.** Not to restart it, not
to polish it, and not to finish the agent's to-do list. Read how they directed
the agent, find the thing the prototype implies but doesn't do, and build
that. You have the session's half-hour, so pick something you can get live.

**Nothing here is marked.** No cutoff, no reflection, no `PROCESS.md` entry,
no crit sweep, no repo of your own on the line. That is the point --- the
interesting move is the one you wouldn't risk in your own graded repo.

**What you show at the share-back** is the live site plus
`git diff riff-start`. Push early and keep `main` green.

**The agent's own spec tests are `spec/course-structure.test.ts` and `spec/data-integrity.test.ts`.** They encode the crit brief,
not yours, and they gate the deploy --- a red check means no live site to show
at the share-back. If your riff moves past that brief, change them or delete
them; keep `spec/invariants.test.ts` green, since that one is true of any good
site.

Everything below this line was written for that crit submission. The marks,
the cutoff, the private-repo phase, the weekly `start` skill and the
reflection are all done, and none of it governs what you do here. Read it for
how they worked, not for what you owe.

---

# The Tang Yin Problem — harness rules

Ground every course fact (dates, names, institutions, scholarly claims) in real
research, not invented plausibility. Check with WebSearch before writing
anything a reader could fact-check. A connoisseurship course that fabricates
its own evidence is the exact failure mode the course exists to teach against.

Every week's material has to earn its place against one question: does it
extend the Tang Yin attribution problem, or is it generic filler that could
belong to any art-history course? Cut or rewrite anything that fails this.

Frontmatter `description`/`marking.description` fields are long prose and
routinely contain a colon followed by a space. Write those as an explicit YAML
block scalar (`>-` folded, or `|-` literal) rather than a bare indented plain
scalar — a colon-space inside a plain multi-line scalar is invalid YAML and
`js-yaml` (which Astro's content loader uses) fails with a confusing "multiline
key may not be an implicit key" error pointing at the *next* key, not the
actual line. If `pnpm check` throws that error, verify the fix against the
project's real `js-yaml` dependency directly (`node -e` importing
`node_modules/.pnpm/js-yaml@*/node_modules/js-yaml/dist/js-yaml.mjs`), not
PyYAML or a by-eye read — PyYAML is more lenient and will pass frontmatter that
still breaks the real build.
