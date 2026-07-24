# Cleeng docs - Mintlify demo repo

Same content as the Redocly demo, adapted to Mintlify conventions:
docs.json config, .mdx pages, spec at api-reference/openapi.yaml.

## Setup

1. Push this repo to GitHub (main).
2. dashboard.mintlify.com -> create project -> connect this repo
   (installs the Mintlify GitHub App).
3. Deploys on every push to main; PRs get preview deployments.

Local preview: `npx mint dev` in the repo root.
Spec validation: `npx mint openapi-check api-reference/openapi.yaml`

## Structure notes (differences vs Redocly worth observing)

- Tab "API 3.1 (curated)": Concepts are standalone MDX pages placed in
  the SAME tab as the generated endpoints - test whether guides and
  endpoints can interleave (they could not in Redocly).
- Tab "API 3.1 (as-is)": spec loaded directly from
  https://cleeng.com/3.1/docs via URL in docs.json - observe refresh
  behavior (when does Mintlify re-fetch?) for the sync row of the sheet.
- The spec still contains x-tagGroups / x-traitTag / x-displayName from
  the Redocly test - observe which of these Mintlify honors or ignores
  (expected: grouping by plain tags; trait tags may render oddly or
  be dropped - note it either way).

## Tests

- Sync: bump MINTLIFY LANE MARKER in api-reference/openapi.yaml, push, time it
- PR preview: change any .mdx on a branch, open PR, find preview URL
- Failure: break the spec, push - does anything block?
