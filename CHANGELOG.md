# Changelog

Changes to the skill that users receive. The version is the one in
`.claude-plugin/plugin.json`; plugin installs only update when it changes.

## [0.3.0] - 2026-11-18

### Added

- Review mode grades the integration against Home Assistant's integration
  quality scale and ends with a per-tier summary: how many Bronze, Silver,
  Gold and Platinum rules it meets, which do not apply, and which are open,
  each with the code that shows it. Custom integrations have no official
  tier, and the report says so.
- New `references/quality-scale.md`: all 54 rules read for a custom
  integration, with where to look for each in your code.
- Each section of `references/ha-best-practices.md` links the live
  contributor-docs pages for that topic, and Build and Review read them
  before writing code or reporting a finding. When the docs site is blocked
  (common in sandboxes) the skill reads the same pages from their GitHub
  source.
- A table for reading core-only docs as a custom integration:
  `translations/en.json` instead of `strings.json`, the `brand/` folder,
  test imports, coverage paths, and what not to add.

### Changed

- The skill is now aimed first at writing good integration code; publishing
  to the Marketplace catalog is the second half. The description it is
  picked by mentions the quality scale, refactoring and reviews for bugs, so
  it loads for everyday integration work, not only for publishing.
- Build mode aims at the Silver rules for new work unless you set another
  target, and its checklist checks that no rule the integration already met
  was broken.

### Removed

- The short quality-scale checklist in `ha-best-practices.md`, replaced by
  `references/quality-scale.md`.
## [0.2.3] - 2026-11-14

### Added

- Two code problems a Marketplace reviewer has flagged, in
  `references/common-pr-feedback.md`, `references/ha-best-practices.md` and
  the Build checklist:
  - Options read once in `async_setup_entry` and reused later, so changes
    do not apply until a reload. Read them when used, or reload the entry
    from an update listener.
  - Bulk enabling or unhiding of entities that also overrides entities the
    user disabled or hid. Only touch entries whose `disabled_by` or
    `hidden_by` is `INTEGRATION`.

## [0.2.2] - 2026-11-12

### Added

- Create mode works out the integration's type before any code is written:
  local or cloud, polling or push, how the user signs in, Bluetooth,
  discovery, device, hub or service, and whether it needs subentries.
- Build mode ends with a checklist to run before a change is called done.
- `references/ha-best-practices.md` has new sections, from the Home Assistant
  developer docs, on OAuth 2.0 with application credentials, config
  subentries, and Bluetooth devices, plus rules on timezone-aware times and
  JSON-serialisable attributes.

## [0.2.1] - 2026-11-12

### Added

- `references/ha-best-practices.md` now carries the rules from Home
  Assistant core's own agent guidance (`ha-integration-knowledge` and
  `AGENTS.md`) that apply to custom integrations: config-flow error logging,
  entity availability and lifecycle, action enums and admin-only actions,
  exception handling and validation, repair issue content and severity,
  testing practice, and the legacy device tracker removal in 2027.5.

### Changed

- `SKILL.md` explains that core's guidance only loads inside a core checkout
  and which parts of it do not apply to custom integrations.

## [0.2.0] - 2026-11-12

### Changed

- Renamed the skill to `marketplace-integration` and updated it for the Home
  Assistant Marketplace (formerly HACS). The command is now
  `/marketplace-integration`.

## [0.1.2] - 2026-11-12

### Fixed

- Gaps found in a test run of the Create workflow.

## [0.1.1] - 2026-11-11

### Changed

- The integration blueprint is mandatory in the Create workflow.

## [0.1.0] - 2026-11-11

### Added

- Plugin and marketplace manifests for installing with `/plugin`.
- Tests and CI for the pre-flight script.
