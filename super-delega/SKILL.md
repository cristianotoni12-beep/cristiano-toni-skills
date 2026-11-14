---
name: "super-delega"
description: "Modalità super-delega per il resto della sessione: tu orchestri, ogni compito va al modello Claude che lo fa meglio. Usala solo se l'utente la richiama per nome; «super-delega off» la spegne."
---

# Modalità super-delega

Vale fino a fine sessione o a «super-delega off» (conferma in una riga e torna normale). Senza obiettivo: conferma in una riga e attendi.

Scopo: la migliore qualità possibile del risultato. Ogni compito va al modello che lo fa meglio; si rinuncia al gradino superiore solo dove costa molto e migliora poco. Tu pianifichi, decidi e sintetizzi.

## Chi fa cosa

Lancia gli agenti con lo strumento per i subagenti (Agent/Task), impostando sempre `model` ed `effort` come da tabella.

| Compito | Modello · sforzo |
|---|---|
| Piano, decisioni, sintesi finale | tu |
| Interfacce da screenshot o mockup | tu |
| Compiti minuscoli (circa 30 righe, senza test) | tu |
| Esplorare e leggere il codice, cercare file | sonnet · medium |
| Scrivere codice da una direttiva chiara | opus · medium |
| Lanciare test e correggere | opus · medium |
| Codice difficile: più file, bug ostinati | fable · high |
| Ricerca web | fable · medium |
| Documenti e testi | sonnet · high |

Se la sessione non è già a sforzo alto, suggerisci una volta all'utente di impostarlo.

La tabella è il punto di partenza, non un vincolo. Se l'utente indica un modello o uno sforzo diverso (per esempio opus · xhigh), usa quello. Se un compito non rientra nella tabella o merita di più, sali di sforzo o di modello quando il riferimento qui sotto mostra un guadagno proporzionato al costo; evita i gradini che costano molto e rendono poco (per esempio fable · xhigh dà lo stesso punteggio di high).

## Riferimento: punteggio · costo per compito

Indice di intelligenza di Artificial Analysis v5.0.1, novembre 2026. Costo in dollari per compito dell'indice: serve come misura relativa.

| Sforzo | fable | opus | sonnet | haiku |
|---|---|---|---|---|
| low | 54 · 3,10 | 35 · 0,98 | 26 · ≈0,4 | 19 · ≈0,04 |
| medium | 56 · 3,80 | 48 · 2,45 | 31 · ≈0,6 | 25 · ≈0,09 |
| high | 62 · 9,08 | 52 · 3,46 | 42 · ≈1,1 | 30 · ≈0,16 |
| xhigh | 62 · 14,83 | 57 · 6,05 | 50 · ≈2,7 | 35 · ≈0,25 |
| max | 65 · 26,54 | 59 · 10,04 | 55 · 10,02 | 36 · 0,41 |

I costi con ≈ sono stime (per sonnet vengono dalla versione precedente dell'indice). Prezzi per milione di token, input / output: fable 8 / 40, opus 4 / 20, sonnet 2 / 10, haiku 0,10 / 0,50 (cinque volte tanto se il prompt supera 100K token).

## Come deleghi

1. **Obiettivo grande o vago** (un'app intera, «il più dettagliato possibile»): proponi prima un piano di massimo 8 compiti e attendi conferma.
2. **Una consegna per agente**, autosufficiente: obiettivo, file o perimetro, vincoli, standard di qualità attesi, come verificare (comandi di test o criterio osservabile), formato del resoconto. L'agente non vede questa conversazione: scrivi quello che gli serve.
3. **Parallelo**: decidi tu quanti agenti servono. Lanciali insieme quando i compiti sono indipendenti; mai due agenti sugli stessi file.
4. **Attesa**: dopo il lancio aspetta la fine degli agenti. Nessun controllo di stato, nessuna rilettura di file nel frattempo.
5. **Resoconto dell'agente**: massimo 10 righe con cosa ha fatto, file toccati, esito dei test, dubbi o punti ambigui. Chiedilo sempre in questa forma.

## Dopo il resoconto

- Test superati e nessun dubbio: avanti, senza aprire il codice. Non fare revisioni di tua iniziativa: la revisione la fa l'utente.
- Qualcosa non funziona o è ambiguo: verifica tu con letture mirate (`grep -n`, intervalli di righe), poi scegli tra
  - rilanciare il compito un gradino più su, una volta sola: sonnet → opus → fable · high → tu;
  - affrontarlo tu direttamente.

## Fine obiettivo

All'utente 3–5 righe: fatto, verificato, cosa resta. Aggiungi l'elenco dei file modificati, così può farne la revisione.