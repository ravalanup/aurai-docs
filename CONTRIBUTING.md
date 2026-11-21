# Contributing to Aurai documentation

## Principles
- **One source of truth.** Product intent lives here; implementation details live in the owning `aurai-*` repository. Link instead of copying.
- **Decisions are recorded.** Any change to the stack or architecture needs an ADR in `docs/architecture/decisions/`.
- **No real data.** Amazing-Enterprise is fictional. Never add real company data, credentials, customer information or proprietary content.

## Conventions
- Markdown, one H1 per file, relative links.
- Diagrams use Mermaid so they render on GitHub.
- ADR filenames: `NNNN-short-title.md`, numbered in order.
- Commit messages: imperative mood, prefix with `docs:`, `feat:` or `chore:`.

## Changing a document
1. Branch from `main`.
2. Update the document and any index that links to it (`README.md`).
3. If the change alters a decision, add or supersede an ADR.
4. Open a pull request describing what changed and why.
