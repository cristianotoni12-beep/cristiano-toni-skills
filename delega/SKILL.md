---
name: "delega"
description: "Modalità delega per il resto della sessione: tu orchestri, agenti Claude più economici eseguono. Usala solo se l'utente la richiama per nome; «delega off» la spegne."
---

# Modalità delega

Vale fino a fine sessione o a «delega off» (conferma in una riga e torna normale). Senza obiettivo: conferma in una riga e attendi.

Scopo: spendere i tuoi token solo dove fai la differenza. Tu pianifichi, decidi e sintetizzi; il lavoro esecutivo va all'agente meno costoso che lo fa bene. Il criterio è il costo opportunità: a parità di risultato vince il modello più economico.

## Chi fa cosa

Lancia gli agenti con lo strumento per i subagenti (Agent/Task), impostando sempre `model` ed `effort` come da tabella.

| Compito | Modello · sforzo |
|---|---|
| Piano, decisioni, sintesi finale | tu |
| Interfacce da screenshot o mockup | tu |
| Compiti minuscoli (circa 30 righe, senza test) | tu: delegarli costa più che farli |
| Esplorare e leggere il codice, cercare file | haiku · medium |
| Scrivere codice da una direttiva chiara | sonnet · medium |
| Lanciare test e correggere | sonnet · medium |
| Codice difficile: più file, bug ostinati | opus · medium |
| Ricerca web: raccolta di fonti e dati | sonnet · medium |
| Ricerca difficile, ragionamento su fonti | fable · low |
| Documenti e testi | sonnet · high |

Se la sessione non è già a sforzo medio, suggerisci una volta all'utente di impostarlo.

La tabella è il punto di partenza, non un vincolo. Se l'utente indica un modello o uno sforzo diverso (per esempio opus · xhigh), usa quello. Se un compito non rientra nella tabella o vuoi discostarti, scegli con il riferimento qui sotto la combinazione meno costosa che raggiunge il livello che serve.

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
2. **Una consegna per agente**, breve e autosufficiente: obiettivo, file o perimetro, vincoli, come verificare (comandi di test o criterio osservabile), formato del resoconto. L'agente non vede questa conversazione: scrivi quello che gli serve, niente di più.
3. **Parallelo**: decidi tu quanti agenti servono. Lanciali insieme quando i compiti sono indipendenti; mai due agenti sugli stessi file.
4. **Attesa**: dopo il lancio aspetta la fine degli agenti. Nessun controllo di stato, nessuna rilettura di file nel frattempo: ogni turno in più rilegge tutto il tuo contesto.
5. **Resoconto dell'agente**: massimo 10 righe con cosa ha fatto, file toccati, esito dei test, dubbi o punti ambigui. Chiedilo sempre in questa forma.

## Dopo il resoconto

- Test superati e nessun dubbio: avanti, senza aprire il codice.
- Qualcosa non funziona o è ambiguo: verifica tu con letture mirate (`grep -n`, intervalli di righe), poi scegli tra
  - rilanciare il compito un gradino più su, una volta sola: haiku → sonnet → opus → tu;
  - affrontarlo tu direttamente.
- Per decidere tra più sforzo e un modello più grande guarda il riferimento: di solito cambiare modello costa meno che spingere lo sforzo.
- Nessun agente revisore: la verifica, quando serve, la fai tu.

## Fine obiettivo

All'utente 3–5 righe: fatto, verificato, cosa resta. Niente elenco dei passaggi.