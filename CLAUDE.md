# How to use and maintain this wiki

This repo is Coach Bronson's knowledge wiki for **MetabolicHQ** (the platform), **MPT** (Metabolic Performance
Training, his coaching program and app space) and his **coaching business** (coachbronson.com, content, books).
It follows Andrej Karpathy's "LLM Wiki" pattern: raw sources stay where they live, the LLM compiles them into
interlinked pages here, and this file is the rulebook for keeping them right.

**Read `index.md` first in every session** that touches MetabolicHQ, MPT or the coaching business. Open the pages it
points to before asking Bronson something the wiki may already answer.

## The wiki is a starting point, not the limit

The wiki is where to start, not the only thing to go on. Claude still uses its memory, the conversation, connected
apps and the source repos to do the work. When Claude finds something the wiki doesn't have (a decision, a file, a
fact from another source) or that the wiki has wrong, it adds a short line to [`inbox.md`](inbox.md): what it is,
where it came from (or a link or reference to it), and the date. The nightly update files those lines into the wiki.
Don't stop work to edit wiki pages mid-task; drop a line in the inbox and keep going.

## Layers

1. **Sources** (not copied here; listed in `sources/README.md`): the code and CHANGELOG in `coachbronson/mac-app`,
   the site in `coachbronson/coachbronson-site`, GitHub issues (the backlog), Claude's memory notes, Google Drive.
2. **Wiki** (`wiki/`): one page per subject. Pages state the current truth, then the decisions behind it.
3. **Schema** (this file) plus `index.md` (catalog of every page) and `log.md` (what changed in the wiki, when).

## Page rules

- Frontmatter on every page: `title`, `summary` (one line), `updated` (YYYY-MM-DD), `sources` (list).
- **Current truth first.** When something changes, rewrite the line to the new truth and keep the old one as
  "(previously …)" only when the history matters for future decisions. Never leave two conflicting statements.
- **Cite where it came from**: an issue (`#517`), a CHANGELOG date (`CHANGELOG 2026-11-08`), a version (`v6.0`),
  a repo file path, or `notes` (a decision Bronson stated in chat). Unsourced lines don't go in.
- **Decisions are Bronson's.** Record what he decided, not what Claude suggested. Claude's proposals that he didn't
  pick stay out.
- Link related pages with relative Markdown links (`[MPT Coach](../metabolichq/mpt-coach.md)`) so they work on GitHub
  and in Obsidian.
- One subject per page. A new subject gets a new page and a line in `index.md`. Keep pages under ~400 lines; split
  when they grow.
- Don't copy the backlog. Pages link issues; `wiki/metabolichq/roadmap-and-backlog.md` holds only the shape of it.

## Never put in this wiki

His home or mailing address, business ID numbers (D-U-N-S, EIN), anyone's email address or phone number, API keys,
secrets, tokens, passwords, payment or account numbers, client health data, and anything about his personal health.
The repo is private, but treat it as shareable.

## Writing rules (his standing preferences)

- His coaching business is never a "practice" (he isn't an MD).
- Food is nutrition, never "fuel"/"fueling"; "fuel" only for real energy substrates (glucose, fatty acids, ketones),
  as in his book's "fuel and function".
- Plain words, short sentences.

## Operations

- **Ingest** (new source or decision): update every page it touches, add/adjust `index.md`, append to `log.md`.
- **Query**: answer from the wiki, citing pages; if the answer came from a source the wiki lacks, file it back.
- **Lint** (nightly): look for contradictions between pages, stale lines the CHANGELOG or closed issues have
  superseded, pages missing from `index.md`, broken links, orphan pages, and facts with no source. Also flag, under "Open questions", any CHANGELOG entry or closed issue
  that changed security, components, operations, configuration or resources while the matching system document's
  "Last reviewed" date (wiki/metabolichq/system-documentation.md) is older than it. Fix what is clear;
  list the rest under "Open questions" at the top of `log.md` for Bronson.

## Nightly update (scheduled task, about 4:41 AM Eastern)

1. Read `log.md` for the last update date.
2. In `coachbronson/mac-app`: CHANGELOG entries since then, issues closed since then (read each "How this was
   resolved" comment), issues opened or re-prioritized since then. Same for `coachbronson/coachbronson-site` commits.
3. Process [`inbox.md`](inbox.md): file each line into the right page (with its source) or, if it only points to
   something, add the reference to `sources/README.md` or the page it belongs on. Remove each line once filed; leave
   anything unclear under "Open questions" in `log.md`.
4. Fold changes into the pages (current truth first), then lint.
5. Commit straight to `main` with message `Nightly update YYYY-MM-DD`, and append a dated entry to `log.md` listing the
   pages changed. If nothing changed, commit nothing.
6. Never change the app or site repos from this task. It only reads them.
