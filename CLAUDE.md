# base-image

Base container images used across Arkestro services. Two flavors: `python/`
(Python runtime bases) and `ubuntu/` (generic Ubuntu base).

## Layout

- `python/` — Python base images (Dockerfiles + build assets)
- `ubuntu/` — Ubuntu base images
- `README.md`

## Commands

```bash
# From either python/ or ubuntu/:
docker build -t arkestro-base-<flavor> .
```

## Conventions & Gotchas

- **These images are foundational.** Every downstream service `FROM`s one
  of them — a bad tag can break every CI build.
- **Pin versions in the Dockerfile.** Do not use rolling tags like `latest`
  or bare `python` — always pin to a digest or explicit version.
- **CVE updates should be coordinated** — bumping a base image kicks off
  rebuilds across the org.
- Cross-cutting patterns: see the team
  [CLAUDE.md baseline](https://github.com/bid-ops-development/proposals-and-planning/tree/main/proposals/claude-md-baseline).
