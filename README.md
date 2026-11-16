# Whisper Studio · Wizard di installazione

Wizard per **Windows, macOS e Linux**. Installa Whisper Studio, guida alla
scelta fra trascrizione locale ed esterna e configura Codex CLI, Claude Code
oppure Gemini CLI. Include una demo con un file di esempio.

**[Scarica il wizard](https://github.com/LorenzoRusso-eng/whisper-studio-wizard/releases/latest/download/Whisper-Studio-Installer.zip)**

## Installazione

1. Scarica lo ZIP ed estrailo completamente in una cartella locale scrivibile.
2. Apri il launcher del tuo sistema:

| Sistema | Launcher |
| --- | --- |
| Windows | `Installa-Windows.bat` |
| macOS | `Installa-macOS.command` oppure `sh launch.sh setup` |
| Linux | `sh install-linux.sh` |

3. Scegli Whisper locale oppure fornisci una trascrizione già pronta. Con una
   trascrizione esterna entrambi i passaggi audio sono saltati.
4. Scegli un assistente AI e completa l'accesso con il tuo account. Il wizard
   spiega il ruolo delle CLI, installa le dipendenze mancanti e propone la demo.

Serve Python 3.11–3.13 a 64 bit con Tcl/Tk, pip e venv; i launcher aiutano a
installare i prerequisiti. I materiali selezionati per l'organizzazione AI vengono
elaborati online dal fornitore scelto, secondo il tuo account e la tua quota.
Per il PDF finale sono disponibili le indicazioni per installare anche TeX.

## Novità della versione 1.1.0

Nell'editor usa **tasto destro sull'elemento → Elimina** per rimuovere segnaposti,
formule, figure/immagini, NDR e riferimenti. Il menu indica quanti riferimenti
verranno rimossi insieme; il salvataggio e la numerazione si aggiornano.
Riapri la lezione dall'app dopo l'aggiornamento.

## Contenuto della repository

Questa repository contiene **solo il pacchetto del wizard e le guide pubbliche**.
Lo ZIP include i componenti applicativi necessari a installare e usare il sistema.
Non include registrazioni, lezioni personali, progetti di lavoro, output,
ambienti Python, modelli scaricati, configurazioni o credenziali.
Lo ZIP contiene un manifest con gli hash dei file e i launcher dei tre sistemi.
Le licenze degli asset di terzi distribuiti sono conservate nel pacchetto.

- [Guida rapida e requisiti](INIZIA-QUI.md)
- [Installazione e CLI](INSTALLAZIONE.md)
- [Novità](CHANGELOG.md)
- [ZIP nella repository](Whisper-Studio-Installer.zip)
- [Checksum SHA-256](Whisper-Studio-Installer.zip.sha256)

Il collaudo nativo è eseguito su Windows. Per Mac Intel, Apple Silicon e Linux x64
sono stati verificati i launcher e la risoluzione delle dipendenze, senza
equivalerli a un collaudo nativo. Codex è stato provato con una demo reale;
Claude e Gemini richiedono la verifica con i rispettivi account.
