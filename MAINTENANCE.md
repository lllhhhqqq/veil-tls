# Veil TLS Maintenance Contract

Last updated: 2026-04-09

## Scope

This repository is the maintained fork for `veil-tls` (`btls`, `btls-sys`, `tokio-btls`).

## Frozen Invariants

1. BoringSSL source of truth is `veil-boringssl` tag `mimic-v1.0`.
2. Submodule pointer `btls-sys/deps/boringssl` must match `btls-sys/boringssl-baseline.txt`.
3. API compatibility is preserved unless explicitly version-bumped.
4. Changes are reviewable and rollback-friendly (small, typed commits).

## Operating Model

1. Update upstream/fork source in `veil-boringssl`.
2. Move submodule pointer in this repo to the approved commit.
3. Apply btls-side adaptation changes.
4. Run CI (`mimic-ci`) before publish.
5. Tag release (`mimic-vX.Y`) only after baseline and tests are green.

## Forbidden Shortcuts

1. Do not bypass baseline check by editing workflow only.
2. Do not change submodule pointer without updating `boringssl-baseline.txt`.
3. Do not mix unrelated refactor with baseline upgrade in one commit.

## Rollback Anchor

Use the previous signed/tagged `mimic-v*` release as rollback baseline.
