# Verlosung

Small web page for running a raffle (Verlosung) at an event. The Bediener enters each drawn Los in a form on the laptop, and a second window on the beamer shows the numbers large, so everyone in the room can read them even when the acoustics are bad.

Scope: one HTML file, no server, no dependencies, no internet.

Note: the user interface is in German.

## Features

- Form for entering drawn Lose (Losnummer, plus an optional Losfarbe)
- Anzeige window for the beamer: large aktuelle Ziehung, smaller Frühere Ziehungen, newest first
- Live preview of the Anzeige in the operator window, with a connection status
- Duplicate and range warnings (with an explicit "trotzdem eintragen")
- Every Ziehung can be edited, marked as Abgeholt (hidden on the Anzeige, reversible) or deleted
- State is saved in the browser, so a reload or an accidentally closed window loses nothing
- Single-colour mode when the Lose have no colours

## Requirements

- A current desktop browser (Firefox is the target; Chrome works too, see Limitations)
- Both windows must be opened in the **same browser on the same laptop**
- No installation and no internet connection

## Getting started

1. Get `verlosung.html` (clone this repo or download the file).
2. Open it in the browser: this is the operator window.
3. Click **Anzeige öffnen (Beamer)**. A second, tab-less window opens.
4. Drag the second window to the beamer screen, then click in it or press any key for fullscreen (F11 also works).
5. Check that the operator window shows "● Anzeige verbunden".

## Usage on the evening

1. Type the Losnummer (digits only; `7` becomes `007`).
2. In multi-colour mode, tap the Losfarbe button, or "Ohne Farbe". The tap enters the Ziehung. In single-colour mode, press **Enter**.
3. The Ziehung appears on the Anzeige right away.
4. If a warning appears (already drawn, or outside the allowed range), read it, then choose **Trotzdem eintragen** or **Abbrechen**.

In the list "Gezogene Lose" below the form:

| Button | Effect |
| --- | --- |
| Bearbeiten | Change Losnummer or Losfarbe |
| Abgeholt | Prize collected: hides the Los on the Anzeige, stays in the list (struck through) |
| Wieder aktiv | Undoes Abgeholt |
| Löschen | Removes the Ziehung for good (asks first), for typos |

If the aktuelle Ziehung is marked Abgeholt, the big slot on the Anzeige stays empty until the next draw.

## Settings

Collapsed under "Einstellungen" in the operator window. The defaults work out of the box.

| Setting | Default |
| --- | --- |
| Einfarbig-Modus (no colour buttons) | off |
| Farben | grün, blau, rot, gelb |
| Höchste Losnummer | 999 |
| Stellen der Losnummer | 3 |
| Frühere Lose anzeigen | 10 |
| Farbe aktuelle / frühere Nummern | white / pale yellow |

"Alles zurücksetzen" deletes all Ziehungen after two confirmations. Settings are kept.

## How it works

The operator window is the only one that writes. It stores the state in the browser's `localStorage`. The Anzeige (`verlosung.html?anzeige`) is read-only and re-renders when storage changes, with a one-second re-check as a safety net. See [ADR 0001](docs/adr/0001-zwei-fenster-localstorage-ohne-server.md) for why there is no server.

## Limitations

- Both windows must be in the same browser on the same machine. The Anzeige can't run on a second device.
- Clearing the browser's site data deletes the saved Ziehungen.
- If the beamer window is fully covered or minimised, the status may show "nicht verbunden" although the Anzeige is still updating.
- Changing "Stellen der Losnummer" does not re-pad Ziehungen that were already entered.
- Tested in Firefox on a real laptop with a beamer. Still do a dry run on your own setup before the event, and check that the colours are readable in a bright room.

## Project layout

```
verlosung.html   the whole application (operator and Anzeige)
GLOSSARY.md      domain terms (Los, Ziehung, Abgeholt, …)
docs/adr/        architecture decisions
docs/agents/     setup for the AI agent skills
CLAUDE.md        agent instructions
```

## Contributing

Issues are tracked in GitHub Issues (`pbarbenheim/verlosung`). Use the terms from `GLOSSARY.md`. Keep it small: one file, no build step, no dependencies.

## License

Licensed under the [GNU General Public License v3.0](LICENSE).
