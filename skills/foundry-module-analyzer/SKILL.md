---
name: foundry-module-analyzer
description: Analyze an existing Foundry Virtual Tabletop module repository, especially modules targeting v14. Explain architecture, every file's purpose and content, dependencies among files/classes/hooks, v14 compliance, and verified execution flows. Generate a structured Markdown analysis report with Mermaid diagrams in the module root. Use foundry-vtt-v14 and javascript-foundry-vtt-v14 when available, and explicitly mark uncertainty instead of guessing.
user-invocable: true
---

# Foundry Module Analyzer

## Mission

Analyze a downloaded Foundry Virtual Tabletop module repository as an evidence-based technical investigation. Produce a well-structured Markdown report in the module's root directory. The report must help a maintainer understand how the module works, what each file contributes, how components depend on one another, and which v14 compatibility risks require attention.

This skill is complementary to `foundry-vtt-v14` and `javascript-foundry-vtt-v14`. Use those skills when available, but do not treat either skill as proof of a module-specific fact.

## Non-negotiable accuracy rules

- Inspect the repository; do not infer file contents from filenames alone.
- Never claim that a class, hook, dependency, manifest field, lifecycle behavior, or API is present unless it is evidenced by source, configuration, documentation, generated output, or a verified v14 reference.
- Do not silently apply Foundry v13 or older behavior to v14.
- Distinguish **Observed**, **Inferred**, **Unverified**, and **Not applicable** findings.
- If a conclusion cannot be verified, write: **"Unclear — insufficient evidence in the analyzed repository or authoritative v14 sources."**
- Do not invent missing files, runtime behavior, dependency versions, execution order, security properties, or compatibility status.
- Treat generated, vendored, minified, binary, and lock files appropriately; identify them and explain whether they were summarized or excluded from detailed analysis.
- Do not modify module source files while analyzing. The only automatic output permitted is the analysis report, unless the user explicitly requests otherwise.
- Do not include secrets, tokens, private URLs, or personal data copied from the repository in the report. Redact them.

## Inputs and scope

Before analysis, establish:

- Module root directory and repository revision or commit, when available.
- Foundry version targeted by the module and exact v14 build, if known.
- System and module versions from manifests and package metadata.
- Whether the repository contains source, build output, tests, documentation, or multiple packages.
- Whether the user wants all files analyzed or binary/vendor/generated files summarized only.

If the target version is missing, analyze the repository as observed and clearly state that v14 compliance cannot be fully determined.

## Required investigation workflow

1. Confirm the module root and collect a file inventory.
2. Read manifests and package metadata first, including `module.json`, `system.json` if present, `package.json`, lockfiles, build configuration, and README files.
3. Identify entry points from manifest fields, scripts, styles, templates, languages, packs, assets, and build output.
4. Trace imports, exports, class definitions, hook registrations, event listeners, settings, document operations, sockets, templates, and stylesheet relationships.
5. Inspect source files and summarize each relevant file without copying large copyrighted sections.
6. Identify external dependencies and distinguish runtime dependencies, build-time dependencies, optional dependencies, peer dependencies, and system/module relationships.
7. Trace lifecycle and user flows from initialization through registration, rendering, interaction, updates, and cleanup where evidence permits.
8. Compare observed patterns with verified Foundry v14 documentation and migration guidance.
9. Check JavaScript, HTML/template, CSS, JSON, security, accessibility, packaging, and maintainability concerns.
10. Generate and save the Markdown report at the module root.
11. Validate that the report exists, references the analyzed revision, and labels uncertainty.

## File-by-file analysis requirements

For every relevant text file, include:

- Relative path.
- File type and approximate role.
- Main purpose.
- Concise content summary.
- Public exports or important declarations.
- Imports and files/components consumed.
- Files/components that depend on it, where traceable.
- Hooks, events, settings, documents, templates, styles, or assets referenced.
- Runtime/build status: source, generated, test, configuration, documentation, or unknown.
- Findings, risks, and uncertainty.

For very large or generated files, provide a bounded summary, size/format note, and reason for not expanding every line. Do not pretend that a minified bundle provides the same traceability as source code.

## Dependency and relationship analysis

Build evidence-based dependency tables covering, when applicable:

- File-to-file imports and exports.
- Entry points to lifecycle registrations.
- Classes to methods and consumers.
- Hooks to registering files and callback effects.
- Templates to renderers and data providers.
- Stylesheets to templates or UI classes.
- Settings, documents, sockets, and compendium references.
- External packages and their use sites.

Mark dynamic imports, string-based references, reflection, global lookups, and unresolved paths as potentially incomplete. Separate static evidence from runtime observations.

## Foundry v14 compliance review

Review, only where evidence supports it:

- Manifest validity and compatibility declarations.
- Entry-point and asset paths.
- Initialization/readiness timing and hook usage.
- ApplicationV2 versus legacy Application APIs.
- Document/data model access, embedded documents, UUIDs, permissions, and ownership.
- Settings, localization, compendia, sockets, and multiplayer behavior.
- Canvas and rendering lifecycle.
- HTML safety, sanitization, permissions, and user-controlled data.
- Deprecated or undocumented APIs.
- Packaging, build output, release metadata, and declared dependencies.
- JavaScript runtime compatibility, template correctness, CSS isolation, and strict JSON validity.

Use statuses such as **Compliant**, **Potential issue**, **Not verified**, **Not applicable**, and **Unclear**. For every potential issue, cite file paths and line ranges when possible, explain the evidence, and avoid asserting a defect without sufficient proof.

## Flowcharts and diagrams

Where relationships or execution paths are traceable, include Mermaid diagrams in fenced `mermaid` blocks. Prefer diagrams such as:

- Module load and lifecycle flow.
- Entry point to hook/class/template flow.
- File and package dependency graph.
- User interaction to document update flow.
- Socket or client/server flow.

Keep diagrams readable. Do not add arrows for relationships that are merely presumed. If a relation is incomplete, label it `unclear`, `dynamic`, or `unresolved`.

## Required report structure

Save a report such as `FOUNDRY-MODULE-ANALYSIS.md` in the module root. If that file already exists, preserve it unless the user explicitly requested replacement; use a timestamped or clearly named alternative report instead.

Use this structure:

1. **Title and analysis metadata** — module name, repository path, revision, date, analyzer, target Foundry version, and scope.
2. **Executive summary** — main purpose, architecture style, entry points, major dependencies, and highest-priority findings.
3. **Evidence and confidence policy** — explain observed/inferred/unverified labels and limitations.
4. **Repository inventory** — directories, file counts, source/build/test/vendor categories.
5. **Architecture overview** — components, boundaries, lifecycle, and Mermaid diagrams.
6. **Entry points and lifecycle** — manifest-defined and discovered execution paths.
7. **File-by-file analysis** — complete relevant-file table and detailed summaries.
8. **Dependency analysis** — tables and diagrams for static and runtime relationships.
9. **Foundry v14 compliance review** — status, evidence, line references, risks, and unknowns.
10. **JavaScript/HTML/CSS/JSON review** — correctness, maintainability, accessibility, and security observations.
11. **Build, packaging, and release review** — scripts, artifacts, paths, versions, and reproducibility.
12. **Findings prioritized by confidence and impact** — do not overstate severity.
13. **Unresolved questions and recommended next investigations**.
14. **Appendix** — commands/tools used, excluded files, assumptions, and references.

## Report quality controls

Before finishing, verify that:

- The report is in the module root and uses valid Markdown.
- The analyzed revision and scope are recorded.
- Every relevant file is accounted for or explicitly excluded with a reason.
- Claims have file paths, line ranges, source references, or an uncertainty label.
- Dependency diagrams do not present guesses as facts.
- Foundry v14 findings distinguish verified compliance from items requiring manual testing.
- Secrets and sensitive data are redacted.
- The report does not claim to execute code or test runtime behavior unless it actually did.
