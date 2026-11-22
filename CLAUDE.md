# Rain Ink Tattoo (cartella e repository «rainInk», prima «inkubo»)

Sito statico (HTML, CSS, JavaScript) dello studio di Matteo Quattrini a Montelupone.
Dettagli completi in **LEGGIMI.txt**: leggilo prima di modifiche non banali.

- Online: https://nemesimark.github.io/rainInk/ (GitHub Pages, repo github.com/nemesiMark/rainInk, ramo `main`).
- Prova in locale: `python3 -m http.server 8000` → http://localhost:8000/
- Video: non sono nel repository, stanno nella release «video» (`gh release download video -D video`).

## Regole di lavoro
- Rispondi sempre in italiano; anche LEGGIMI, commenti e messaggi di commit in italiano.
- Ogni modifica va annotata in fondo a LEGGIMI.txt, sezione VERSIONI: numero successivo, data (gg/mm/aaaa), descrizione semplice. Se cambiano `css/style.css` o `js/*.js`, aggiorna il `?v=` nelle pagine.
- Niente commit/push di tua iniziativa: Mark prova prima in locale. Commit e push solo su richiesta o con «g».
- «g» = commit e push: `git pull --rebase --autostash`, poi `python3 scripts/genera_lavori.py` e `python3 scripts/genera_lavori.py --check`, `git add -A`, commit in italiano, `git push`; poi attendi GitHub Actions (`gh run list`) e controlla il sito online.

## Area riservata e contenuti
- Il cliente modifica foto, video e testi dall'area riservata (`area-riservata.html` + Worker Cloudflare in `worker/`), che salva i JSON in `data/` direttamente su GitHub: fai sempre `git pull` prima di lavorare.
- I testi con `data-testo`, le foto con `data-slot` e le gallerie si cambiano nei JSON di `data/` (`testi.json`, `immagini.json`, `lavori.json`, `ruota.json`, `video.json`, `studio-home.json`), **non nell'HTML**: `scripts/genera_lavori.py` riscrive le pagine a ogni pubblicazione.
- Ogni foto/video/testo è indipendente: modificare una sezione non deve mai toccare altre sezioni o pagine (unica eccezione: i sottomenu della navbar).
- Se cambia ciò che la pagina chiede al Worker, pubblica il Worker (`cd worker && wrangler deploy`) prima del push del sito.
- Le schermate della guida stanno in `images/guida/`; i punti `data-punti` si ricalcolano con `riquadri.py` della skill area-ris.

## Dati provvisori
P.IVA, orari, dominio, chiave Web3Forms sono ancora da chiedere al cliente (elenco in LEGGIMI, «DATI DA SOSTITUIRE»).
