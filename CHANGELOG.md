# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-01-27

### Changed

- Converted from local skill to Claude Code plugin format
- Moved skill files to `skills/makeover/` directory
- Added `.claude-plugin/plugin.json` manifest

### Added

- Plugin installation via `/plugins add lifofifoX/makeover`
- Auto-update support through Claude Code plugin system
- Pre-flight dependency check for frontend-design plugin
- MIT license
- This changelog

### Migration

If you previously installed this as a local skill:

1. Install the plugin: `/plugins add lifofifoX/makeover`
2. Remove the old skill: `rm -rf ~/.claude/skills/makeover`
3. Your existing `tmp/makeover/` data remains compatible
