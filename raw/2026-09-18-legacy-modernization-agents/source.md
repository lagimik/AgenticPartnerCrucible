# Legacy Modernization Agents Source Capture

Captured: 2026-09-18

## Provenance

- Repository: https://github.com/Azure-Samples/Legacy-Modernization-Agents
- Reviewed snapshot: https://github.com/Azure-Samples/Legacy-Modernization-Agents/commit/1b52c83d9b33c0d568bc0cc852347b89f458bade
- Snapshot date: 2026-09-17
- Source type: Public Microsoft sample repository

## Direct Source Summary

Legacy Modernization Agents is an evolving Azure Samples accelerator for analyzing COBOL estates, extracting business knowledge, mapping dependencies, and generating Java with Quarkus or C#/.NET code. The workflow separates structural analysis, business-logic extraction, dependency mapping, and conversion rather than treating modernization as a single prompt.

The sample persists analysis in SQLite and can use Neo4j for dependency visualization. It handles large source files with semantic chunking around COBOL divisions, sections, and paragraphs. Deterministic controls classify parse fidelity, retain unresolved dependencies, and compare expected structural identifiers with generated output.

Structural parity is not behavioral correctness. Production modernization still requires subject-matter review, compilation, characterization and regression testing, data reconciliation, performance validation, security review, and target-state architecture decisions.

## Evidence Notes

- The documented targets are Java/Quarkus and C#/.NET.
- Reverse engineering can produce business-purpose, use-case, rule, and glossary material before conversion.
- Dependency analysis covers calls, copybooks, performed procedures, executable blocks, file operations, JCL relationships, and unresolved references.
- Only the strongest parser states are presented as candidates for unattended conversion.
- The parity validator is deterministic but explicitly does not prove correct behavior.
- The implementation includes Azure OpenAI, GitHub Copilot SDK, Microsoft.Extensions.AI, SQLite, and Neo4j dependencies.

## Interpretation

Partners can use the sample inside a governed estate-assessment and migration-factory method. The strongest initial offers are dependency and readiness discovery, business-knowledge preservation, migration-wave planning, target-stack selection, and evidence-based conversion assurance.

