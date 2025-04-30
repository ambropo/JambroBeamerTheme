# Changelog

All notable changes to this project will be documented in this file.

## Version 1.1 — *2022-04-30*

### Added
- **New Commands**:
  - `\lapis[color]{text}`: Underlines text using TikZ in the specified color. Defaults to *baseline gold* if no color is provided.
  - `\stabilo[color]{text}`: Highlights text using TikZ in the specified color. Defaults to *baseline gold* if no color is provided.

- **New Options**:
  - `shownotes`: Compiles detailed speaker notes alongside slides — useful for rehearsals or presentation printouts.
  - `handout`: Produces handouts with a 2×1 slide-per-page layout (portrait orientation). Can be combined with `shownotes` for annotated handouts.

### Changed
- The `\hlight` command for text highlighting has been replaced by `\stabilo`.

---

## Version 1.0 — *2022-11-15*

### Added
- Initial release of the Jambro Beamer Theme.

