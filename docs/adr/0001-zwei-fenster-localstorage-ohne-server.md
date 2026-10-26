# Two windows in one browser, synced via localStorage, no server

The Bediener form and the Anzeige are two windows of the same `verlosung.html` on one laptop (the beamer is an extended screen). The Bediener window is the only writer and keeps the state in `localStorage`; the Anzeige is read-only and re-renders on the `storage` event, with a 1-second re-check as safety net. We rejected a local server or websockets: no install, no network and nothing that can fail to start matters more than supporting a separate display machine.

Consequence: both windows must be opened in the same browser on the same machine. A second device cannot show the Anzeige.
