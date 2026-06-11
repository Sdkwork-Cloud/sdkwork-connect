# Repository Guidelines

<!-- SDKWORK-AGENTS-GENERATED: v1 -->

## SDKWORK Soul

Read `../sdkwork-specs/SOUL.md` before executing tasks in this root. Follow specs before memory, dictionary before context, stop on ambiguity, and evidence before completion.

## SDKWORK Standards

Canonical SDKWORK specs path from this root:

- `../sdkwork-specs/README.md`
- `../sdkwork-specs/SOUL.md`
- `../sdkwork-specs/AGENTS_SPEC.md`
- `../sdkwork-specs/CODE_STYLE_SPEC.md`
- `../sdkwork-specs/NAMING_SPEC.md`

Do not copy root standard text into this repository. If these relative paths do not resolve, stop and report the broken workspace layout.

## Repository Identity

This repository is the SDKWork Connect repository for platform-level device interconnect and P2P runtime capabilities.

Use the canonical SDKWork domain `device` and capability `connect` unless a later accepted architecture decision changes the boundary.

## Local Dictionary Structure

- `AGENTS.md`: local agent entrypoint and relative SDKWORK spec index.
- `CLAUDE.md`: Claude Code compatibility shim that points to `AGENTS.md` and must not duplicate rules.
- `GEMINI.md`: Gemini CLI compatibility shim that points to `AGENTS.md` and must not duplicate rules.
- `CODEX.md`: Codex compatibility shim that points to `AGENTS.md` and must not duplicate rules.
- `.sdkwork/`: source-controlled local dictionary folder for skills, plugins, manifests, and AI workspace metadata.
- `specs/`: local repository/component contracts and narrowing rules.
- `docs/`: architecture decisions, design specs, runbooks, and release notes.
- Future source directories to inspect first when relevant: `crates/`, `services/`, `packages/`, `apps/`, `sdks/`, `tools/`, `scripts/`.

## Spec Resolution Order

1. Read this `AGENTS.md` and any nearer component-level `AGENTS.md`.
2. Read local `specs/README.md` and `specs/component.spec.json` when present.
3. Read local `.sdkwork/README.md`, `.sdkwork/skills/`, and `.sdkwork/plugins/` when relevant.
4. Read `../sdkwork-specs/README.md` and the task-specific root specs.
5. Inspect implementation files only after the relevant dictionary entries are clear.

## Required Specs By Task Type

- Agent/workflow changes: `../sdkwork-specs/SOUL.md`, `../sdkwork-specs/AGENTS_SPEC.md`, `../sdkwork-specs/SDKWORK_WORKSPACE_SPEC.md`.
- Any code change: `../sdkwork-specs/CODE_STYLE_SPEC.md`, `../sdkwork-specs/NAMING_SPEC.md`, plus only the touched language/framework spec.
- Rust code or Cargo manifests: `../sdkwork-specs/RUST_CODE_SPEC.md`.
- TypeScript/Node code or package manifests: `../sdkwork-specs/TYPESCRIPT_CODE_SPEC.md`.
- Frontend/UI code: `../sdkwork-specs/FRONTEND_CODE_SPEC.md`, `../sdkwork-specs/FRONTEND_SPEC.md`, `../sdkwork-specs/UI_ARCHITECTURE_SPEC.md`, and exactly one detailed UI architecture spec.
- Desktop/Tauri host code: `../sdkwork-specs/DESKTOP_APP_ARCHITECTURE_SPEC.md`.
- Reusable modules: `../sdkwork-specs/MODULE_SPEC.md`, `../sdkwork-specs/COMPONENT_SPEC.md`.
- Runtime config and environment changes: `../sdkwork-specs/CONFIG_SPEC.md`, `../sdkwork-specs/ENVIRONMENT_SPEC.md`, and `../sdkwork-specs/RUNTIME_DIRECTORY_SPEC.md`.
- API, SDK, security, privacy, deployment, release, and dependency changes must follow the task matrix in `../sdkwork-specs/README.md`.

Language-specific specs are on-demand; do not load unrelated language specs.

## Code Style Rules

Read `../sdkwork-specs/CODE_STYLE_SPEC.md` and `../sdkwork-specs/NAMING_SPEC.md` before code changes.

For Rust, keep `src/lib.rs` limited to module declarations, re-exports, light docs, and wiring; move runtime behavior, protocol handlers, services, persistence, DTOs, provider clients, and tests into focused modules.

For TypeScript packages, prefer strict types, explicit package exports, colocated tests, and public package-root imports. Do not expose application pages, routes, or shell behavior from top-level shared packages.

## Planned Repository Boundaries

Top-level `packages/` is reserved for application-neutral TypeScript contracts, clients, and adapters. It must not contain SDKWork Connect PC application pages, routes, shells, or business UI.

SDKWork Connect's own runnable PC management application, when implemented, belongs under `apps/sdkwork-connect-pc/`.

Rust P2P runtime, libp2p integration, local service runtime, IPC, and Tauri integration belong under `crates/` and `services/` according to the accepted design.

## Build, Test, And Verification

Verification commands will be defined when language manifests are introduced. Until then, validate repository dictionary and design documents by reading:

- `AGENTS.md`
- `.sdkwork/README.md`
- `specs/component.spec.json`
- `docs/superpowers/specs/`

When manifests are added, run the narrowest relevant check first, then broader verification when public contracts, SDK generation, runtime, security, or cross-package boundaries change.

## Agent Execution Rules

Use the convention dictionary instead of broad context loading. Do not hand-edit generated SDK output. Do not replace generated SDK integration with raw HTTP. Keep changes scoped to the owning module, package, crate, service, or app root. Record exact verification commands and important outputs before reporting completion.

## Human Review Rules

Request human review before changing public naming, altering security/auth behavior, changing generated SDK ownership, adding relay/bootstrap production dependencies, changing local runtime secret storage, deleting data/files, or publishing release artifacts.
