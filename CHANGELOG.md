# Changelog

All notable changes to Build Better OS are documented here.

This file follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) conventions. Versions follow [Semantic Versioning](https://semver.org/).

---

## [Unreleased]

### Added
- Initial repository structure and project foundation
- Root documentation: README, ARCHITECTURE, CONTRIBUTING, ROADMAP, PROJECT_STRUCTURE
- Folder structure for `apps/`, `services/`, `platform/`, `packages/`, `infra/`, `docs/`, `scripts/`
- Architecture Decision Record structure under `docs/adr/`
- GitHub configuration: PR template, issue templates, workflows directory, CODEOWNERS
- `CLAUDE.md` — structured AI context file for AI coding assistants
- `SECURITY.md` — vulnerability reporting policy
- `.github/CODEOWNERS` — PR ownership and review routing
- `docs/adr/0001-monorepo-structure.md` — first architecture decision record
- Naming conventions section in `CONTRIBUTING.md`

### Changed
- `ARCHITECTURE.md` — added authoritative dependency rules section, consolidated AI-native design principles, added data flow event contract references, added docs/architecture scope rule
- `PROJECT_STRUCTURE.md` — removed incorrect `infra/` code dependency arrow; dependency and naming rules now reference their authoritative locations
- `platform/integrations/README.md` — added explicit shared-only rule for what belongs here
- `platform/core/README.md` — AI-native notes now reference authoritative definition in ARCHITECTURE.md
- `platform/runtime/README.md` — AI-native notes now reference authoritative definition in ARCHITECTURE.md
- `infra/README.md` — renamed proposed `infra/services/` to `infra/deployments/` to avoid collision with top-level `services/`

---

<!-- Releases will be added below this line in the format:

## [0.1.0] - YYYY-MM-DD
### Added
### Changed
### Fixed
### Removed
### Security

-->
