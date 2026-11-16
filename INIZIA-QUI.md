# Whisper Studio — installa, prova, condividi

1. Estrai **tutto** lo ZIP in una cartella locale scrivibile. Non avviare i file dentro lo ZIP.
2. Avvia il wizard per il tuo sistema:

| Sistema | Installazione | Avvio normale | Demo |
| --- | --- | --- | --- |
| Windows | `Installa-Windows.bat` | `Avvia-Windows.bat` | `Demo-Windows.bat` |
| macOS | `Installa-macOS.command` | `Avvia-macOS.command` | `Demo-macOS.command` |
| Linux | `sh install-linux.sh` | `sh start-linux.sh` | `sh demo-linux.sh` |

Su macOS, se l'estrattore non conserva i permessi di esecuzione, apri Terminale
nella cartella estratta ed esegui `sh launch.sh setup`. Non occorre disattivare le
protezioni del sistema. Il pacchetto contiene script sorgenti: non è un'app firmata
o un installer nativo `.exe`/`.dmg`/`.deb`.

Il wizard chiede **prima di tutto** se vuoi Whisper locale o una trascrizione
già pronta. Nel secondo caso scegli il tuo TXT, MD, SRT o JSON, oppure il file
di esempio. Non viene contattato un servizio di trascrizione esterno: devi
esportarne il testo. Whisper e il secondo passaggio audio vengono saltati.

Scegli poi **un** assistente: Codex CLI, Claude Code (comando `claude`) o Gemini
CLI. Il wizard spiega il loro ruolo e installa quello mancante nella cartella
`.tools`, con Node.js LTS se necessario. Se uno è già disponibile, lo riutilizza.
Completa l'accesso con il pulsante finale; ogni persona usa il proprio account.
La disponibilità del servizio e i costi dipendono dall'account, dal piano e dalla
quota. Gli appunti e i materiali scelti vengono elaborati online dal fornitore AI.
La trascrizione con Whisper avviene sul computer. L'app non conserva credenziali
nei progetti e non le include nel pacchetto di distribuzione.

## Requisiti di sistema

- Python **3.11–3.13 a 64 bit**, con pip, venv e Tcl/Tk.
  Windows propone l'installazione Python tramite winget se manca.
  Mac propone Homebrew se è già presente; in alternativa installa Python da
  [python.org](https://www.python.org/downloads/).
  Linux propone i pacchetti apt/dnf; su distribuzioni con Python precedente a
  3.11 serve una versione supportata separata. Debian/Ubuntu richiedono
  `python3-tk` e `python3-venv`; le versioni devono corrispondere all'interprete.
- Una sessione grafica per il programma desktop. `python setup_wizard.py --console`
  offre le scelte nel terminale, ma l'app desktop richiede comunque Tk e un display.
- Internet per installazione, accesso all'assistente, generazione AI e primo
  download dei modelli Whisper. La demo locale funziona offline dopo il setup.
- Windows x64, macOS 14+ (Intel o Apple Silicon), Linux x64; Linux ARM64 nei limiti dei wheel
  binari disponibili per le versioni fissate. Il setup rileva gli errori di pip.
  Non viene promesso supporto a ogni distribuzione Linux o a Windows ARM64.
  Gemini CLI consiglia macOS 15+ e Windows 11 24H2+. Su Mac Intel il lock usa
  ONNX Runtime 1.23.2, ultima versione di questa serie con wheel compatibili.
- Whisper funziona su CPU; su Mac **non** usa Metal con faster-whisper.
  CUDA è facoltativo e richiede NVIDIA, Windows/Linux x64 e driver CUDA 12.
  Scegliendo CPU non vengono installate librerie NVIDIA. Con `auto` viene usata
  la CPU se CUDA non è disponibile; per installare le librerie GPU scegli `cuda`.
- Per il **PDF finale** serve anche TeX (MiKTeX, MacTeX o TeX Live) e, per
  convertire figure SVG in PDF, Chrome/Chromium/Edge. Il wizard controlla gli
  strumenti e propone l'installazione TeX nel terminale. Può richiedere password
  di amministratore e diversi GB. Senza TeX si conserva l'esportazione parziale
  con i sorgenti; l'app non dichiara un PDF completato se manca.

## La prima demo

Apri **Demo** e premi **Avvia dimostrazione**. Vedrai l'importazione del file
`examples/first-lesson/transcript.txt`, i passaggi audio saltati e la creazione
di due sezioni, formule e una figura sulla legge di Ohm. Premi **Apri e modifica
la lezione**, cambia una frase o una didascalia e salva nell'editor.

La modalità iniziale usa un **risultato precompilato**, chiaramente indicato.
Importazione, verifica dei segmenti, pubblicazione e salvataggio sono reali;
non viene simulata una chiamata AI. Per provare anche l'organizzazione generativa,
seleziona **Elaborazione AI reale** dopo l'accesso all'assistente. Ogni esecuzione
crea una nuova cartella `demo-output/`, conservando le correzioni precedenti.

## Dopo l'installazione

Nell'app scegli cartella, trascrizione/audio e materiali; premi **Elabora lezione**.
In alto puoi cambiare `whisper`/`external` e `codex`/`claude`/`gemini`.
Con `external` è obbligatorio selezionare un testo; anche se rimane un vecchio
percorso audio, non viene usato per trascrizione o controllo audio.
**Strumenti → Installazione e assistente AI** riapre il wizard.

Nell'editor, fai **tasto destro sull'elemento → Elimina** per rimuovere un
segnaposto, una formula inline/display, una figura/immagine, una NDR o un
riferimento. Se elimini un elemento richiamato nel testo, il comando indica
quanti riferimenti verranno rimossi insieme. Numerazione e salvataggio si
aggiornano; gli asset originali e la revisione precedente restano conservati.
Eliminare un singolo riferimento lascia il suo elemento di destinazione.
Dopo un aggiornamento riapri la lezione dall'app per usare il nuovo editor.

Le dipendenze Python sono in `.venv`, le CLI locali in `.tools`, le scelte in
`.state/installation.json` e i dettagli del setup in `.logs/install.log`.
Non copiare questi ambienti tra computer: ogni destinatario esegue il wizard.

## Preparare un nuovo ZIP da mandare

Esegui `python build_release.py` oppure usa il Python del virtualenv.
Ottieni `release/Whisper-Studio-Installer.zip`, con un manifest SHA-256.
La selezione è esplicita: non contiene le tue registrazioni, lezioni, output,
configurazioni, cache, account o modelli. Condividi questo ZIP; non l'intera
cartella di lavoro.

Per dettagli e documentazione ufficiale delle CLI consulta [INSTALLAZIONE.md](INSTALLAZIONE.md).
