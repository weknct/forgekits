# Changelog

All notable changes to the Process Decomposition (Lite) plugin are documented here.
This project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.0] - 2026-06-21

### Added
- Initial free release.
- **`process-decomposer`** orchestrator agent (Lite edition) covering Bootstrap
  and Process Decomposition.
- **`phase-1-bootstrap`** skill — stands up the `{process-slug}/` decomposition
  workspace, with bundled folder-structure, file-header, and registry-header templates.
- **`phase-3-process-decomposition`** skill — event storm, event classification,
  decision gates, and error-compounding analysis, with bundled event-storm,
  error-compounding, and decomposition-heuristics templates.
- Plugin manifest, README, free-use (no-resale) license.
