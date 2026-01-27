# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-01-27

### Changed

- Converted from local skill to Claude Code plugin marketplace format
- Moved skill files to `plugins/makeover/` directory
- Added `.claude-plugin/marketplace.json` manifest

### Added

- Plugin installation via marketplace:
  ```
  /plugin marketplace add https://github.com/lifofifoX/makeover
  /plugin install makeover
  ```
- Auto-update support through Claude Code plugin system
- Pre-flight dependency check for frontend-design plugin
- MIT license
- This changelog

### Migration

If you previously installed this as a local skill:

1. Add marketplace: `/plugin marketplace add https://github.com/lifofifoX/makeover`
2. Install plugin: `/plugin install makeover`
3. Remove old skill: `rm -rf ~/.claude/skills/makeover`
4. Your existing `tmp/makeover/` data remains compatible
