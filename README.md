# Testable Java corpus — `JV_V17_MAVEN_TP6152_SLIM`

Slim branch derived from `JV_V17_MAVEN_THINJAR_MONO` for **Java-only** Testable whitebox runs (e.g. TP-6152, Java rows in the derivation sheet).

## What was removed

The parent branch ships four large trees used to certify tools in isolation:

- `Tool Clean (Synthetic Data)/`
- `Tool Invalid (Synthetic Data)/`
- `Tool Triggering (Synthetic Data)/`
- `Tool Triggering (Tool Github Test data)/`

Those folders contain hundreds of nested `package.json`, Python, and multi-language fixtures. Testable language detection treats them as extra analysis units, which drives **~100+ tasks** per run and long dev admission queues.

This branch keeps **only** the real Maven monolith:

- `pom.xml` (Java 17, JUnit, JaCoCo, PIT, OWASP dependency-check, PMD, Checkstyle, SpotBugs, …)
- `src/main/java` and `src/test/java`
- `dataset.json` answer key

After stripping: **one** `pom.xml`, **no** `package.json` / `pyproject.toml`.

## When to use

| Branch | Use |
|--------|-----|
| `JV_V17_MAVEN_THINJAR_MONO` | Full corpus / per-tool synthetic certification |
| **`JV_V17_MAVEN_TP6152_SLIM`** | Faster Java whitebox on dev; sheet primary tools on the domain app |

## Project (unchanged from parent)

Grid cell `MVN-THIN-M` — Java **17**, Maven, thin jar, monolith. See `dataset.json` for pins and answer key.

## Primary Java tools (pom + platform catalog)

Aligned with the Java derivation sheet and `pom.xml` plugins:

`checkstyle`, `cpd`, `jacoco`, `pitest`, `pmd`, `spotbugs`, `owasp-depcheck`, `lizard`, `coverage_delta`, `def_use`, `ck`, `maven-versions`, `maven-checksum`, `java-perf-dependency`, plus repo-level tools the platform may still schedule (`pydriller`, `semgrep`, `presidio`, `detect-secrets`, …) — but **not** a full JS/Python tool matrix from synthetic trees.
