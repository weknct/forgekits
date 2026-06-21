# Changelog

All notable changes to the SDLC Forge (Lite) plugin are documented here.
This project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.0] - 2026-06-21

### Added
- Initial public release of the free Lite tier.
- **Forge Guide** agent (`forge-guide`): SDLC orchestrator that performs phase
  detection across the 9-phase SDLC and routes the user to the next action.
- **Phase Detection** skill (`phase-detection`): deterministic, first-match-wins
  detection of the current SDLC phase with the recommended next step.
- **Morning Standup** command (`/morning-standup`): daily standup brief —
  yesterday, today, blockers, and sprint pulse — from the project's trackers.
- Plugin manifest, README, and Lite license.
