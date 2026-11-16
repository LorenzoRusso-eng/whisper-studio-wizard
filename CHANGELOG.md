# Changelog

## 1.2.0 — 2026-11-16

- English throughout the installation wizard, desktop lesson/transcription
  interfaces, editor, figure comparison, CLI help, errors, progress, and demo.
- English operational prompts, generated compilation instructions, public
  guides, and template documentation. Newly generated reports and assistant
  status messages are requested in English.
- English launcher names: `Install-Windows.bat`, `Start-Windows.bat`,
  `Install-macOS.command`, and `Start-macOS.command`. Terminal confirmations
  now use y/N, including the corresponding acceptance logic.
- English guide filenames: `QUICKSTART.md`, `INSTALLATION.md`, and the shared
  template's `README.md`. The organization prompt is
  `PROMPT_LECTURE_ORGANIZATION.md`; exports create `README-compilation.md`.
- Source language codes, project formats, element IDs, and multilingual
  source-filename recognition remain compatible. Existing user lessons,
  transcripts, recordings, notes, and archived output are preserved.

## 1.1.0 — 2026-11-16

- Right-click **Delete** for every placeholder type, inline/display formulas,
  generated figures, imported images, editorial notes, and references.
- The command shows how many linked references will be removed with a target.
  Other figures and references remain valid, and numbering updates.
- Saving synchronizes HTML, Markdown, figure metadata, and the LaTeX handoff.
  Deletions persist after reopening and through exported JSON project import.
- Previous revisions and original assets are retained. Structural validation
  still rejects inconsistent figure slots and dangling references.
- The Windows/macOS/Linux installer includes the updated editor.

After updating, reopen the lesson from the app. An older running editor server
must be replaced before it can save structured deletions.
