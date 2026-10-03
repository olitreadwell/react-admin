# marmelab/react-admin context
> refreshed 2026-10-03 | upstream default: master @ 47890673cae903b9c5a33898c07a12ea94205b5a

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
- `2026-09-24` trivial cleanup pass (12 doc typos, 10 files) — closed-superseded (fork PR #17 `doc/fix-typos-in-documentation`, 21 files after follow-up fold-ins, body regenerated 2026-09-30). Folded into #20 on 2026-10-01 so a single same-kind docs cleanup stays canonical; do NOT re-fix any word it covered (occured/withing/explicitely + the 21 files in #20).

- `2026-10-01` trivial cleanup pass (broken relative links + in-page anchors) — pr-updated, still OPEN (fork PR #20 `doc/fix-broken-doc-links`). Consolidated 2026-10-03 into a single same-kind docs cleanup: squashed to one commit 9c33c02e58243d6d3c3829b2ec78543b84a9ef8c, now 36 files / +50/-50, and it absorbed the spelling pack from #21 (so both #17's words and #21's 14 fixes are covered here). Do NOT re-fix any word or file it now touches. Original distinct theme (broken relative links + stale anchors): no file overlap with #17 at open time. All targets re-verified present at open time.
- `2026-10-02` trivial cleanup pass (spelling, 14 fixes / 10 files) — closed-superseded (fork PR #21 `doc/fix-spelling-mistakes-in-docs` closed 2026-10-03 and folded into #20 so a single same-kind docs cleanup stays canonical; commit 755b66d, was fork-CI-green). See #20 for the consolidated diff; do not re-fix its words. It covered: `docs/StackedFilters.md` `mutliple` -> `multiple` x3; `docs/TabbedForm.md` `yout` -> `your`, `commponent` -> `component`; `docs/Calendar.md` `convertion` -> `conversion`; `packages/ra-core/src/store/README.md` `componenents` -> `components`, `sort rder` -> `sort order`; `seletedIds` -> `selectedIds` in `useHardDeleteMany.md`, `useSoftDeleteMany.md`, `useRestoreMany.md` (legacy `docs/` + `docs_headless/`).
- `2026-10-03` trivial cleanup pass (spelling, 10 fixes / 10 files, +10/-10) — pr-opened, still OPEN (fork PR #22 `doc/fix-more-spelling-typos`, commit a9e50147, non-draft, base fork `master`, 1 commit). Distinct words from #20/#21 and no file overlap with them; verified against live upstream master @ 47890673 (fork master identical, 0/0). Fixes: `docs/CustomRoutes.md` `anomymous` -> `anonymous`; `docs/useInfiniteGetList.md` `suports` -> `supports`; `docs/withLifecycleCallbacks.md` `wilcard` -> `wildcard`; `docs/useRegisterMutationMiddleware.md` `middlware` -> `middleware` (sample fn name); `docs/Menu.md` `flashs` -> `flashes`; `docs/SelectColumnsButton.md` `dasboard` -> `dashboard`; `docs/Layout.md` `overiding` -> `overriding`; `docs/DateTimeInput.md` `JavasSript` -> `JavaScript`; `docs/Toolbar.md` + `docs/Translation.md` `commponents` -> `components`. Upstream dedupe (`gh search prs` for each word, state open) returned nothing. Local: `typos` clean on the 10 changed files, `git diff --check` clean; fork CI ALL substantive checks green (doc-check Jekyll build, doc-videos-format-check, typecheck, unit-test, e2e-test, simple-example-typecheck, e-commerce, crm; create-react-admin + update-sandbox-repository skipped as conditional/tag-only jobs); mergeable=true, mergeable_state=clean.
- `2026-09-25` issue #10478 (Date-typed values silently lost to strings in optimistic cache via `JSON.parse(JSON.stringify(...))` in create/update hooks) — dropped (duplicate). The exact fix — a `removeUndefined` helper preserving `Date`, wired into `useUpdate` + `useUpdateMany` (+ util/index export, regression spec) — is ALREADY CLAIMED by open upstream PR #11271 `fix: preserve Date values in optimistic updates` (author louzhedong, open since 2026-06-08, mergeable, only Vercel deploy-authorization checks failing). Live code still has the bug (issue #10478 unmerged), but the argo-cd #29148 rule = open PR means work is claimed: do NOT re-pick. `useCreate` shares the same JSON-round-trip root cause but is a derivative slice of the same claimed theme, not an independent gap — left untaken. Lesson: re-run the upstream dedupe search at pick time; the earlier scan missed #11271 because the `gh search prs --state all` flags errored (use `--state open`/`--state closed`, or a bare keyword query).

## Mined gaps (discovered, not yet attempted)
- `2026-09-08` trivial cleanup pass: typos (`occured` x6, `withing` x2, `explicitely` x1) + broken relative links missing `.md` (Breadcrumb x3, Inputs x1, Upgrade x1) + dead `./ColumnsButton.md` link in DataTable.md — status: attempted (pr-opened #14, folded into #17)
- `2026-10-01` self-found BROKEN LINKS/ANCHORS (distinct theme from #17 typos): docs/useGetOne.md malformed link `](./DataTable.md],`; docs_headless Validation.md `../data-fetching/DataProviderWriting.html` (no such path); docs_headless InfiniteListBase.md `./Admin.md#accessdenied` (no Admin.md; siblings use CoreAdmin.md); docs_headless Form.md `#default-values` (heading slug is `#defaultvalues`); docs_headless CoreAdmin.md `#using-react-admin-in-a-sub-path` (heading is "Using Ra-Core In A Sub Path") and `#customizing-the-login-component` (headless heading is "Adding A Login Page"). Verified with a repo-wide relative-link + GitHub-slug anchor checker; none overlap #17's 21 files. — status: attempted (pr-opened #20)
- `2026-10-02` remaining spelling typos — status: attempted (pr-opened #22 for the `docs/` copies). Still unfixed after #22: the `docs_headless/src/content/docs/` duplicates of `anomymous`, `suports`, `wilcard`, `middlware` (4 files), plus `coutries` -> `countries` (`docs/Features.md` + headless copy), `Informations` -> `Information` in the dialog docs (5 files; label strings in samples — check intent first), and a `./ReferenceField.md` link in `docs_headless/src/content/docs/ReferenceFieldBase.md` that has no target (headless has no `ReferenceField.md`). Candidate for a later pass; do not re-fix the 10 words in #22 or anything covered by #20.
