# Note di installazione e verifica

Il wizard è implementato con la libreria standard Python. Le stesse cinque
schermate sono usate su Windows, macOS e Linux. I launcher risolvono i percorsi
in base alla cartella estratta, senza dipendere dalla directory del terminale.

Le dipendenze dell'editor sono in `requirements-base.txt`. Il profilo Whisper
aggiunge `requirements-whisper.txt` e il lock CPU; il profilo CUDA aggiunge
`requirements-nvidia.txt`. Il lock storico Windows rimane per `setup.ps1`.
L'installazione usa pip e controlla gli exit code e `pip check` prima di salvare
la configurazione. Un errore o un annullamento non marca il setup come completato.
Su Mac Intel è fissato ONNX Runtime 1.23.2: il pin 1.24.4 usato sugli altri
sistemi non fornisce un wheel Intel Mac. La risoluzione binaria è stata verificata
separatamente per Mac Apple Silicon, Mac Intel e Linux x64 con Python 3.13.

Node.js viene riutilizzato se è almeno 22 e npm è disponibile. Se serve, il
wizard scarica Node 24 LTS da `nodejs.org`, confronta il SHA-256 con il file
ufficiale `SHASUMS256.txt`, ed estrae solo percorsi interni all'archivio senza
link simbolici. Non modifica il PATH del sistema: `.tools` è aggiunto soltanto
all'ambiente dei processi di Whisper Studio. Le CLI sono installate alla versione
stabile disponibile; la loro evoluzione richiede di mantenere gli adattatori.

| Assistente | Esecuzione | Risultato |
| --- | --- | --- |
| Codex CLI | `codex exec`, stdin, eventi JSONL, sandbox workspace-write | Schema nativo e verifica editor |
| Claude Code | `claude -p`, stdin, stream-json, JSON Schema | structured_output e verifica editor |
| Gemini CLI | `gemini --prompt`, stdin, stream-json, auto_edit | JSON richiesto nel prompt, validazione locale completa e verifica editor |

La stessa scelta si applica a lezioni e LaTeX. Gemini **è integrabile**, ma il
suo output JSON di trasporto non garantisce lo schema della lezione: l'adattatore
lo verifica localmente e rifiuta risultati incompleti. Tutti i percorsi mantengono
il controllo della copertura dei segmenti. Errori, quota esaurita e rifiuti di
permessi conservano gli input e non diventano successi. Le CLI non ereditano
questa conversazione. Claude e Gemini seguono il proprio sistema di permessi;
non hanno automaticamente la stessa sandbox di Codex. L'app richiede file e shell
per figure, verifiche e compilazione; eventuali dinieghi sono riportati come limiti.

Codex e Claude hanno un controllo locale dell'accesso. Per Gemini si controlla
solo l'avvio; l'account e la quota sono verificati dal primo lavoro reale. Il
wizard apre il login interattivo nel terminale e lascia all'utente l'autenticazione.
Non copia, esporta o gestisce token del fornitore.

Fonti ufficiali consultate per questa integrazione:

- [Codex CLI](https://developers.openai.com/codex/cli/)
- [Codex non interattivo](https://developers.openai.com/codex/noninteractive/)
- [Claude Code: installazione](https://code.claude.com/docs/en/setup)
- [Claude Code: esecuzione programmatica](https://code.claude.com/docs/en/headless)
- [Claude Code: riferimento CLI](https://code.claude.com/docs/en/cli-reference)
- [Gemini CLI: installazione](https://geminicli.com/docs/get-started/installation/)
- [Gemini CLI: modalità headless](https://geminicli.com/docs/cli/headless/)
- [Gemini CLI: opzioni](https://geminicli.com/docs/cli/cli-reference/)

La verifica automatica del pacchetto controlla che l'archivio contenga tutti gli
asset dell'editor e i template, ed esclude cartelle personali e file di stato.
I test degli adattatori usano processi locali controllati: non provano da soli
accesso e generazione reali con account Claude o Gemini. Il collaudo eseguito su
Windows non equivale a una prova nativa su macOS o Linux.
