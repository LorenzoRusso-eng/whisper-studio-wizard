# Installation and validation

The installation wizard uses the Python standard library. The same five
English screens run on Windows, macOS, and Linux. Platform launchers resolve
paths from the extracted application folder, independently of the terminal's
working directory. Terminal confirmations use **y/N**.

## Dependency profiles

`requirements-base.txt` installs the editor, PDF input support, and figure
tools. Whisper adds `requirements-whisper.txt` and the CPU lock. CUDA also
adds `requirements-nvidia.txt`. The historical Windows lock remains available
for `setup.ps1`.

Setup checks every command's exit status and runs `pip check` before saving
configuration. A failure or cancellation does not mark installation complete.
Intel Mac uses ONNX Runtime 1.23.2 because the 1.24.4 pin used elsewhere does
not publish an Intel Mac wheel. Binary resolution has been checked separately
for Intel Mac, Apple Silicon, and Linux x64 with Python 3.13. This does not
replace native execution on those platforms.

The installer reuses Node.js 22+ when npm is available. Otherwise it downloads
official Node 24 LTS from `nodejs.org`, verifies its SHA-256 against
`SHASUMS256.txt`, and extracts internal archive paths without symbolic links.
It adds `.tools` only to Whisper Studio's process environment; it does not
change the system PATH. CLIs are installed at the available stable version,
so their evolving interfaces may require adapter updates.

## Assistant adapters

| Assistant | Execution | Result handling |
| --- | --- | --- |
| Codex CLI | `codex exec`, stdin, JSONL events, workspace-write sandbox | Native output schema plus editor validation |
| Claude Code | `claude -p`, stdin, stream-json, JSON Schema | structured_output plus local/editor validation |
| Gemini CLI | `gemini --prompt`, stdin, stream-json, auto_edit | JSON requested in the prompt, validated locally before publication |

The selected assistant is used for both lesson organization and LaTeX export.
Gemini supports automation, but its JSON transport does not enforce the
lesson's schema; the adapter validates the full application contract and
rejects incomplete output. Every provider path checks transcript-segment
coverage. Authentication failures, exhausted quotas, denied tools, and
cancellation preserve inputs and do not become successful results.

CLI jobs receive the effective prompt and selected context without inheriting
the current chat. Permissions differ between providers. Codex uses its
workspace sandbox; Claude and Gemini use their own permission mechanisms.
The app requests file and shell tools for figures, checks, and compilation.
A denied operation must be reported as a limitation rather than claimed as
verified.

Codex and Claude provide a local authentication-status check. Gemini's initial
check verifies CLI startup only; the first live job checks authentication and
quota. Sign-in opens an interactive terminal for the user. The app does not
copy, export, or manage provider tokens.

## English UI and existing data

The wizard, desktop app, web editor, CLI help, status/error messages, example,
operational prompts, launchers, and guides use English. Recognized source
language codes and technical identifiers remain stable. Source-filename
discovery retains multilingual aliases so existing user materials still work.
Previously created transcripts, projects, notes, recordings, and archived
outputs are preserved in their original language.

The main public entry points are `Install-Windows.bat`,
`Install-macOS.command`, and `install-linux.sh`. Guides are `QUICKSTART.md`
and `INSTALLATION.md`; lesson organization uses
`PROMPT_LECTURE_ORGANIZATION.md`. LaTeX exports write
`README-compilation.md`. Existing lesson JSON schemas and stable element IDs
are preserved across the language change.

## Validation

Python regression tests cover the pipelines, editor save validation, optional
ASR installation, providers, metadata, queues, and release contents. GUI tests
require a desktop; HTTP editor tests need localhost. Browser tests operate on
isolated generated lessons and exercise insertion, right-click deletion,
references, saving/reloading, and exported-project import.

The distribution uses an explicit allowlist. Its manifest records component
hashes, version, supported platforms, and the quick-start entry point. The ZIP
excludes personal source materials, settings, credentials, installed
environments, model caches, and generated lessons.

Native testing has been performed on Windows. Mac/Linux dependency and
launcher checks are documented separately. Codex has been exercised with a
live demo; local Claude/Gemini adapter tests do not establish successful
account-based end-to-end execution.

## Official references

- [Codex CLI](https://developers.openai.com/codex/cli/)
- [Codex non-interactive mode](https://developers.openai.com/codex/noninteractive/)
- [Claude Code setup](https://code.claude.com/docs/en/setup)
- [Claude Code programmatic use](https://code.claude.com/docs/en/headless)
- [Claude Code CLI reference](https://code.claude.com/docs/en/cli-reference)
- [Gemini CLI installation](https://geminicli.com/docs/get-started/installation/)
- [Gemini CLI headless mode](https://geminicli.com/docs/cli/headless/)
- [Gemini CLI options](https://geminicli.com/docs/cli/cli-reference/)
