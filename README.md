# golang-dist mirror automation

This branch exists only to run GitHub Actions for the Gentoo Go vendor
distribution mirror.

It is intentionally separate from `main`. Do not sync this branch with upstream
or merge `main` into it. The mirror workflow checks upstream tags from
`storj/uplink-c`, rewrites each mirrored tag with a generated release workflow,
and publishes vendor/dependency tarballs for those tags.

## Workflows

- `.github/workflows/mirror.yml` periodically runs
  `projg2/golang-dist-mirror-action` to discover new upstream tags and create
  matching mirrored tags in this repository.
- `.github/workflows/sync-release-notes.yml` copies the release title and notes
  from matching releases in `storj/uplink-c` so the generated releases do not
  keep the placeholder `Replace workflows` text.

## Maintenance

Keep this branch minimal. It should contain only this README and the workflow
files needed to maintain the mirror.

If this branch is protected, temporarily bypass or disable the protection only
when updating the mirror automation, then restore the protection afterward.
