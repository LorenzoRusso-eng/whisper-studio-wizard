# Whisper Studio — install, try, and share

1. Extract the **entire ZIP** into a writable local folder. Run the files from
   that folder, not from inside the archive.
2. Start the wizard for your operating system:

| System | Install | Start the app | Demo |
| --- | --- | --- | --- |
| Windows | `Install-Windows.bat` | `Start-Windows.bat` | `Demo-Windows.bat` |
| macOS | `Install-macOS.command` | `Start-macOS.command` | `Demo-macOS.command` |
| Linux | `sh install-linux.sh` | `sh start-linux.sh` | `sh demo-linux.sh` |

If executable permissions were lost on macOS, open Terminal in the extracted
folder and run `sh launch.sh setup`. This is a source ZIP with platform
launchers. The wizard, app, editor, CLI help, prompts, and guides use English.

## 1. Choose where the transcript comes from

The wizard asks this question first:

- **Local Whisper:** start from audio/video. Recognition and the second audio
  review pass run on your computer. Models download on first use.
- **External service:** provide an existing TXT, Markdown, SRT, or JSON file,
  or use the included sample transcript. Both audio passes are skipped. The
  app imports the exported text; it does not contact a transcription service.

JSON transcripts must contain a nonempty `segments` list of objects with
`text`. SRT/JSON timestamps are preserved when present. TXT/Markdown paragraphs
become source segments without invented timecodes.

## 2. Choose an AI assistant

Choose **one** of Codex CLI, Claude Code (`claude`), or Gemini CLI. The assistant
organizes text with your slides, prepares figures, and later converts your
approved notes to LaTeX. Whisper handles audio recognition only.

The wizard explains the role of the CLI, reuses an available installation, or
installs it in `.tools`. If necessary it downloads official Node.js LTS and
verifies its SHA-256 checksum. Complete sign-in using the final-page button;
each recipient uses their own account and quota. Selected text and context
are processed online by the chosen AI provider. The app does not request or
copy passwords or API keys into projects or distribution packages.

## Requirements

- **64-bit Python 3.11–3.13**, including pip, venv, and Tcl/Tk. Windows offers
  installation through winget when Python is absent. Mac offers Homebrew when
  it is already available; the complete [python.org installer](https://www.python.org/downloads/)
  is another option. Linux offers apt/dnf packages. A distribution with older
  Python requires a separate supported interpreter.
- On Debian/Ubuntu, install `python3-tk` and `python3-venv`; their versions must
  match the selected interpreter. On Mac with Homebrew, install the matching
  `python-tk@3.13` package when using Python 3.13.
- A graphical desktop for the app. `python setup_wizard.py --console` provides
  terminal choices, but the desktop app still requires Tk and a display.
- Internet for setup, assistant sign-in and generation, and the first Whisper
  model download. The local prepared demo works offline after installation.
- Windows x64, macOS 14+ on Intel or Apple Silicon, and Linux x64. Linux ARM64
  depends on binary wheel availability. Support for every Linux distribution
  or Windows ARM64 is not guaranteed. Gemini CLI recommends macOS 15+ and
  Windows 11 24H2+. Intel Mac uses ONNX Runtime 1.23.2 in the pinned profile.
- CPU mode works on all supported systems. Mac faster-whisper uses CPU,
  including on Apple Silicon; it does not use Metal. CUDA is optional and
  requires a compatible NVIDIA GPU/driver on Windows/Linux x64. Choose `cuda`
  to install the GPU libraries. `auto` uses CPU when CUDA is unavailable.
- For a **compiled PDF**, install a TeX distribution (MiKTeX, MacTeX, or
  TeX Live). SVG-to-PDF figures also need Chrome/Chromium/Edge. The wizard
  checks these tools and offers TeX installation commands. TeX may require
  administrator authentication and several GB. Without these tools, the app
  can preserve sources as an explicitly partial export.

## Your first demo

Run your system's **Demo** launcher and click **Start demo**. The app imports
`examples/first-lesson/transcript.txt`, shows both audio passes being skipped,
and creates an editable lesson about Ohm's law with two sections, formulas,
and a figure. Click **Open and edit the lesson**, change a sentence or caption,
and save in the local editor.

The initial mode uses a clearly labeled **prepared result**. Importing,
coverage validation, publication, and saving use the real app. No live AI
response or audio recognition is simulated. To test generation as well,
select **Live AI processing** after signing in. It sends the sample text to
the selected provider and consumes the account's allowance. Every run creates
a new `demo-output/` folder, preserving edits from earlier runs.

## Use your own materials

Choose a project folder, audio/transcript, and optional slides or notes, then
click **Process lesson**. The project bar selects `whisper`/`external` and
`codex`/`claude`/`gemini`. In external mode a transcript is required; an old
audio selection is ignored for both recognition and review.

Right-click an element and choose **Delete** to remove any placeholder,
inline/display formula, figure/image, editorial note, or reference. If a
target has linked references, the menu shows how many will be removed with
it. Numbering and saving update automatically. Original asset bytes and the
previous revision are kept. Deleting one reference leaves its target intact.
After an update, reopen the lesson from the app to load the latest editor.

Use **Tools → Installation and AI assistant** to reopen setup. Save approved
editor corrections before starting **LaTeX and PDF**. **Prepare prompt** freezes
inputs without a generative call; **Generate LaTeX** creates a new export.

Dependencies live in `.venv`, local CLIs in `.tools`, settings in
`.state/installation.json`, and installation details in `.logs/install.log`.
Recreate these environments on each computer rather than copying them.

## Share a new installer

Run `python build_release.py` with the project's virtualenv. It creates
`release/Whisper-Studio-Installer.zip` and a SHA-256 checksum. Only explicitly
listed program files are included. Personal recordings, lessons, output,
settings, caches, accounts, and downloaded models are excluded. Share this
ZIP instead of your full workspace.

See [INSTALLATION.md](INSTALLATION.md) for technical details and official CLI
references, or [README.md](README.md) for the complete workflow.
