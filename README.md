# cristiano-toni-skills
Una lista di skill per utilizzo giornaliero; utili per risparmiare token e trovare il migliore compromesso tra qualità dell'output e costo.

## Skill

| Skill | A cosa serve |
|---|---|
| [`delega`](delega/SKILL.md) | Il modello della sessione (Fable 5.2 o simili) orchestra e affida il lavoro esecutivo all'agente Claude meno costoso che lo fa bene. Criterio: costo opportunità. |
| [`super-delega`](super-delega/SKILL.md) | Stessa struttura, ma ogni compito va al modello che lo fa meglio; si rinuncia al gradino superiore solo dove costa molto e migliora poco. |

Entrambe si attivano a mano, una volta per sessione, e contengono una tabella di riferimento punteggio · costo per modello e livello di sforzo (Artificial Analysis, novembre 2026).

## Installazione

- **claude.ai:** comprimi la cartella della skill in uno ZIP e caricala da Personalizza → Skill.
- **Claude Code:** copia la cartella in `~/.claude/skills/`.
