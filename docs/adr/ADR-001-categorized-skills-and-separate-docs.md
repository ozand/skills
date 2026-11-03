# ADR-001: Categorize skills and separate reader documentation

**Status**: Proposed  
**Date**: 2026-11-03  
**Authors**: Pi assistant  
**Supersedes**: None  
**Related**: Issue #10

## Context

The owner requested a navigable collection grouped by purpose, separate human-facing documentation, and translations under `docs/readme/`. The published single-skill layout has existing links and may have been copied by users. Skill installation and discovery vary by host.

## Decision

Place skills at `skills/<category>/<name>/` and human documentation at `docs/<category>/<name>.md`; preserve the Russian skill page at `docs/<category>/<name>.ru.md` with reciprocal language links. Place translated root README files in `docs/readme/`. For the first skill use category `communication`. Keep `SKILL.md`, its referenced files and MIT notice together for standalone copying. Root README remains the collection entry point.

Retain short human-readable pointers at old documentation paths where feasible, but do not retain a second discoverable `SKILL.md`: duplicate names can cause ambiguous agent discovery. An old direct URL to `SKILL.md` cannot transparently remain without retaining that duplicate, so document the new path and limitation rather than claim a redirect exists. Existing installations are not modified or migrated.

## Alternatives considered

- Keep flat skill folders and embedded human READMEs: simpler for one skill, but conflicts with the owner's agreed categorization and separation.
- Duplicate the skill at both paths: rejected because agents may discover two definitions with the same name.
- Redirect old paths using hosting-specific machinery: not selected without an existing supported mechanism; simple links keep the collection static.

## Consequences

### What gets easier

Humans navigate by category without reading agent instructions first; adding skills follows one understandable layout.

### What gets harder

Previously published direct file URLs may break; documentation links and installation paths must be updated. The local-only old skill directory pointer does not redirect a historical direct file URL.

### What does not change

Skill instructions, attribution, license terms, existing installations and host-specific activation remain unchanged.

## Test contract

| Claim | Check |
|---|---|
| Skill and license preserved | Compare moved files to original Git blob identities |
| No duplicate skill | Enumerate `SKILL.md` and parse new skill |
| Human links and translations resolve | Check both language pages, reciprocal links, relative Markdown links and old-path pointer files |
| Individual installation remains possible | Copy to a temporary directory and check all referenced files and license |

## Rollback

Revert the migration commit without deleting user installations. Preserve later user work and any published links; no existing runtime reload is implied.

## References

- Issue #10
- https://agentskills.io/specification
