# ADR-002: Remove legacy pointers and keep the MIT license at the root

**Status**: Proposed
**Date**: 2026-11-03
**Authors**: Pi assistant
**Supersedes**: ADR-001, only its legacy-pointer and bundled-license choices
**Related**: Issue #12

## Context

After the categorized migration, the owner requested removing the old skill directory and the duplicate license inside the new skill folder. ADR-001 chose to keep both; its other layout and discovery decisions remain unchanged.

## Decision

Remove the old `skills/explain-clearly/` documentation pointers and the duplicate `skills/communication/explain-clearly/LICENSE`. Keep the existing MIT `LICENSE` at the repository root. Update both English and Russian documentation, including the Pi copy example, to copy the root license into a standalone skill destination and to link to the root license. Verify the documented copy includes it. Do not modify existing user installations.

Old directory and direct-file URLs referring to the current tree will no longer resolve; historical revision URLs may remain accessible. This is an explicit owner-directed compatibility trade-off, not a redirect. No change to the license terms or skill content is authorized.

## Alternatives considered

- Keep pointers and a duplicate license: preserves old URLs and self-contained copying, but the owner requested the simpler layout.
- Add server-side redirects or an installer: unnecessary infrastructure for this repository.

## Consequences

### What gets easier

The repository has one license file and one skill directory.

### What gets harder

Old URLs break, and standalone copying requires including the root license.

### What does not change

MIT terms, the skill's instructions and references, category layout, and existing installed copies remain unchanged.

## Test contract

| Claim | Check |
|---|---|
| Root license and skill content preserved | Compare hashes against the base revision |
| Standalone copy retains notice | Execute documented copy in a temporary home, check LICENSE bytes |
| References are valid | Check local Markdown links and absence of stale paths |

## Rollback

Revert the change in Git, preserving any subsequent work. Do not modify installed copies.

## References

- Issue #12
- ADR-001
