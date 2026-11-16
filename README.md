# Whisper Studio · Installation Wizard

A guided installer for **Windows, macOS, and Linux**. Choose local Whisper
transcription or import an existing transcript, then connect **Codex CLI,
Claude Code, or Gemini CLI**. The wizard explains each assistant's role and
includes an interactive demonstration with a sample lesson.

**[Download the wizard](https://github.com/LorenzoRusso-eng/whisper-studio-wizard/releases/latest/download/Whisper-Studio-Installer.zip)**

## Installation

1. Download the ZIP and extract it completely into a writable local folder.
2. Run the launcher for your operating system:

| Operating system | Launcher |
| --- | --- |
| Windows | `Install-Windows.bat` |
| macOS | `Install-macOS.command` or `sh launch.sh setup` |
| Linux | `sh install-linux.sh` |

3. First choose **local Whisper** or **an existing transcript**. Importing a
   TXT, Markdown, SRT, or supported JSON transcript skips both audio passes
   and installs only the dependencies needed for the text workflow.
4. Choose one AI assistant, complete installation, and sign in with your own
   account. The app uses the CLI to organize lessons, reconstruct figures,
   and prepare LaTeX/PDF after your edits.
5. Run the guided demo. The local version uses the included prepared result.
   The optional live version sends the sample text to your selected provider
   after you confirm it in the demo.

All application interfaces, guides, launchers, operational prompts, and
generated application messages are in **English**. Source transcripts can
use other supported languages; source language codes are preserved.

You need **64-bit Python 3.11–3.13** with Tcl/Tk, pip, and venv. The launchers
help install these prerequisites. Selected materials are processed online
by your chosen AI provider, using your account and its usage allowance.
TeX and a supported browser are additional requirements for final PDF output.

## Version 1.2.0

- English throughout the wizard, desktop interfaces, HTML editor, figure
  comparison, demo, CLI messages, guides, and LaTeX workflow.
- English launcher and guide filenames, with working **y/N** confirmations.
- Right-click **Delete** for placeholders, formulas, figures/images, editorial
  notes, and references. Linked-reference counts, numbering, and saved projects
  remain consistent after deletion.

When updating, extract the new package into its own folder and reopen the
lesson from the updated app. The package preserves compatibility with existing
project formats and source language codes.

## Repository contents

This repository distributes **the installer ZIP and public guides**. The ZIP
contains the application components needed to install and use the system,
an example lesson, a file-hash manifest, and bundled third-party licenses.
Personal recordings, lecture notes, work projects, generated output, Python
environments, downloaded models, settings, and credentials are excluded.

- [Quick start and requirements](QUICKSTART.md)
- [Installation and CLI details](INSTALLATION.md)
- [Changelog](CHANGELOG.md)
- [ZIP in this repository](Whisper-Studio-Installer.zip)
- [SHA-256 checksum](Whisper-Studio-Installer.zip.sha256)

## Validation status

Native testing has been performed on Windows, including the English wizard
and real browser editing, saving, and deletion workflows. Launchers and binary
dependency resolution have also been checked for Intel Macs, Apple Silicon,
and Linux x64; native testing on those platforms remains pending.

Codex has been tested with a live demo. Claude and Gemini have local integration
tests; end-to-end verification with their respective accounts remains pending.
