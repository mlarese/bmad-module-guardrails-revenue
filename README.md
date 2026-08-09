# Guardrails Revenue (`grv`)

Rhea e tre workflow per audit read-only dei dati, scenari di pricing e preflight PMS/Channel Manager. Usa il modello QuoProfit/RevD come conoscenza interna, ricerca di dominio verificabile e calcoli deterministici; nessuna pubblicazione verso sistemi esterni senza un gate esplicito, dry-run, approvazione e rollback.

Modulo BMad. È una porzione del bundle [Guardrails](https://github.com/mlarese/bmad-module-guardrails):
stesse figure, stesso comportamento, solo l'area revenue.

> **Generato.** Questo repository è prodotto da `tools/build_modules.py` nel
> repository [bmad-module-guardrails](https://github.com/mlarese/bmad-module-guardrails).
> Le modifiche si fanno lì e poi si rigenera: qui vengono sovrascritte.

## Figure

| Figura | Ruolo | Skill | Cosa presidia |
| ------ | ----- | ----- | ------------- |
| 📈 Rhea | Revenue Management Strategist | `grl-agent-revenue` | Consulenza e calcoli di revenue management alberghiero con conoscenza QuoProfit/RevD, KPI, pricing, forecasting e integrazioni PMS/Channel Manager. |

## Skill e workflow

| Skill | Comando | Cosa fa |
| ----- | ------- | ------- |
| `grv-profile` | Profila il progetto | Raccoglie in pochi minuti gli otto campi che danno contesto a tutte le figure, criticità inclusa. |
| `grv-profile` | Aggiorna il profilo | Riallinea il profilo quando il progetto cambia, e dice se il cambiamento invalida rischi già accettati. |
| `grv-board` | Convoca il collegio | Fa leggere lo stesso artefatto alle sole figure pertinenti e restituisce un riepilogo unico, conflitti compresi. |
| `grv-board` | Rischi già accettati | Mostra, raggruppato per figura, quello che il progetto ha consapevolmente scelto di accettare. |
| `grv-board` | Gate di rilascio | Verifica una release identificata e restituisce GO, GO_CON_CONDIZIONI, NO_GO o EVIDENZA_INSUFFICIENTE. |
| `grl-revenue-audit` | Audita dati e prezzi revenue | Produce un audit read-only di export, qualità dati, KPI, domanda e floor economico, con fonti, formule, blocker e dati mancanti. |
| `grl-revenue-plan` | Prepara un piano revenue | Costruisce scenari di pricing, domanda e profitto separando floor, mercato e forecast, con trigger di monitoraggio e senza pubblicare tariffe. |
| `grl-revenue-preflight` | Preflight PMS e Channel Manager | Verifica contratto, mapping, semantica per-data/LOS, dry-run, response, riconciliazione, idempotenza e rollback prima dell'invio. |
| `grl-automation` | Instrada un'automazione | Classifica lo scenario, sceglie agenti e workflow BMad e dichiara capability mancanti, scope e approvazioni, includendo social/content e creative video. |
| `grl-automation` | Prepara un piano eseguibile | Costruisce passi idempotenti con input, output, precondizioni, rischio, approvazione e rollback. |
| `grl-automation` | Esegui controlli read-only | Raccoglie evidenze e confronti riproducibili senza modificare sistemi esterni. |
| `grl-automation` | Prepara un dry-run | Genera e valida diff o payload senza spendere, pubblicare o applicare side effect. |
| `grl-automation` | Esegui dopo approvazione | Applica solo lo scope approvato, registra prima/dopo e osserva il risultato; in caso di errore attiva il rollback. |
| `grl-automation` | Riprendi un'automazione | Riprende un run esistente dal primo passo non concluso senza duplicare scritture o side effect. |

## Installazione

```
bmad install grv
```

Poi, come primo passo, `grv-profile`: raccoglie il profilo di progetto — settore,
dati trattati, mercato, stack, criticità — e da lì ogni figura deriva quanto essere
severa. Senza profilo il default resta `normal` e le figure partono senza contesto.

## Memoria condivisa

Il profilo vive in `{project-root}/_bmad/memory/grl-shared/project-profile.md`, insieme
a `decisions.md` e `accepted-risks.md`. Il percorso è lo stesso per tutti i moduli
Guardrails: installandone due, il profilo resta uno solo e si compila una volta.

## Convivenza con il bundle

Questo modulo installa skill con **lo stesso nome** del bundle `grl` — `grl-agent-revenue`
sta identica in entrambi. Bundle e moduli tematici non vanno installati insieme nello
stesso progetto: si sceglie il bundle completo, oppure i moduli delle aree che servono.

## Licenza

MIT.
