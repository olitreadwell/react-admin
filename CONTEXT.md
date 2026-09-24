# marmelab/react-admin context
> refreshed 2026-09-24 | upstream default: master @ 6aeb9edc9

## Identity & policies
- upstream: marmelab/react-admin, default branch `master`, primary language TypeScript, English-first (yes — all docs/UI in English)
- CLA/DCO: none (policy passport: cla_required false, dco_required false)
- AI-assisted PR policy: unstated (bans_ai false, ai_disclosure_required false)
- signed commits required: no
- PR template: `.github/pull_request_template.md` (Problem / Solution / How To Test / Additional Checks)
- external tracker: github

## Conventions (verified from merged PRs)
- branch naming: `fix/<desc>`, `doc/<desc>`, `feat/<desc>`, `dependabot/...` (dominant human patterns: `fix/`, `doc/`)
- commit style: Conventional-ish imperative ("[Chore] Fix release script on MacOS", "Merge pull request #N")
- test command: `yarn test-unit` (jest); lint: `yarn lint` (eslint); typecheck: `yarn typecheck`
- CI checks that gate merge: lint, typecheck, unit tests, e2e (cypress)
- how outside PRs get merged: responsive; small doc/link/typo PRs are welcome (CONTRIBUTING: "keep your pull requests small")

## Maintainer picture
- active maintainers: marmelab core team (faster-than-average response on small PRs)
- areas actively worked: ra-core-ee docs, dependabot bumps, DataTable/DataTableInput, headless docs site (`docs_headless/`)

## Issue-area health
- docs/ is the primary docs site (Jekyll); `docs_headless/` is a newer Astro/Starlight experimental site
- trivial doc/link/typo fixes are low-risk and welcome

## Gap ledger (dedupe — READ FIRST, never re-pick)
- `2026-08-05` issue #11303 (InPlaceEditor blur) — pr-opened-green (fork PR #2)
- `2026-08-05` self-found a11y (DataTable aria-sort) — pr-opened-green (fork PR #3)
- `2026-08-26` audit gate sweep — pr-updated (fork PR #2 body)
- `2026-09-08/09` trivial cleanup pass (typos + broken links) — pr-opened then pr-updated (fork PR #14, extended with story-file `occured` typos; CI green, mergeable clean)
- `2026-09-24` trivial cleanup pass (12 doc typos, 10 files) — pr-opened (fork PR #17, doc-check/unit/typecheck/e2e green, mergeable clean)

- `2026-09-25` issue #10478 (Date-typed values silently lost to strings in optimistic cache via `JSON.parse(JSON.stringify(...))` in create/update hooks) — dropped (duplicate). The exact fix — a `removeUndefined` helper preserving `Date`, wired into `useUpdate` + `useUpdateMany` (+ util/index export, regression spec) — is ALREADY CLAIMED by open upstream PR #11271 `fix: preserve Date values in optimistic updates` (author louzhedong, open since 2026-06-08, mergeable, only Vercel deploy-authorization checks failing). Live code still has the bug (issue #10478 unmerged), but the argo-cd #29148 rule = open PR means work is claimed: do NOT re-pick. `useCreate` shares the same JSON-round-trip root cause but is a derivative slice of the same claimed theme, not an independent gap — left untaken. Lesson: re-run the upstream dedupe search at pick time; the earlier scan missed #11271 because the `gh search prs --state all` flags errored (use `--state open`/`--state closed`, or a bare keyword query).

## Mined gaps (discovered, not yet attempted)
- `2026-09-08` trivial cleanup pass: typos (`occured` x6, `withing` x2, `explicitely` x1) + broken relative links missing `.md` (Breadcrumb x3, Inputs x1, Upgrade x1) + dead `./ColumnsButton.md` link in DataTable.md — status: attempted (pr-opened #14)
