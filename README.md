# Whisper Studio · Installation Wizard

A guided installer for **Windows, macOS, and Linux**. Set up Whisper Studio,
choose between local speech recognition and an existing transcript, and configure
Codex CLI, Claude Code, or Gemini CLI. An interactive demo with a sample file is
included.

**[Download the wizard](https://github.com/LorenzoRusso-eng/whisper-studio-wizard/releases/latest/download/Whisper-Studio-Installer.zip)**

## Installation

1. Download the ZIP and extract it completely into a writable local folder.
2. Run the launcher for your operating system:

| Operating system | Launcher |
| --- | --- |
| Windows | `Installa-Windows.bat` |
| macOS | `Installa-macOS.command` or `sh launch.sh setup` |
| Linux | `sh install-linux.sh` |

3. Choose local Whisper transcription or provide a transcript you have already
   created. Importing an external transcript skips both audio processing passes.
4. Select an AI assistant and sign in with your own account. The wizard explains
   how the CLIs are used, installs missing dependencies, and offers a guided demo.

You need **64-bit Python 3.11–3.13** with Tcl/Tk, pip, and venv. The launchers help
install these prerequisites. Materials selected for AI organization are processed
online by your chosen provider, using your account and its usage allowance.
Instructions for installing TeX are available if you want to generate a PDF.

The wizard interface and the linked guides are currently in Italian.

## What's new in version 1.1.0

In the editor, **right-click an element → Elimina (Delete)** to remove
placeholders, formulas, figures/images, editorial notes (NDR), or references.
The menu shows how many linked references will be removed with the element.
Saving and numbering update accordingly. Reopen the lesson from the app after
updating.

## Repository contents

This repository contains **the installer package and public guides**. The ZIP
includes the application components needed to install and use the system.
Personal recordings, lecture notes, work projects, generated output, Python
environments, downloaded models, settings, and credentials are excluded.

The ZIP contains launchers for all three operating systems and a manifest with
file hashes. Licenses for bundled third-party assets are included in the package.

- [Quick start and requirements (Italian)](INIZIA-QUI.md)
- [Installation and CLI details (Italian)](INSTALLAZIONE.md)
- [Changelog (Italian)](CHANGELOG.md)
- [ZIP in this repository](Whisper-Studio-Installer.zip)
- [SHA-256 checksum](Whisper-Studio-Installer.zip.sha256)

## Validation status

Native testing has been performed on Windows. Launchers and binary dependency
resolution have also been checked for Intel Macs, Apple Silicon, and Linux x64;
native testing on those platforms remains pending.

Codex has been tested with a live demo. Claude and Gemini have local integration
tests; end-to-end verification with their respective accounts remains pending.
