# Verlosung

A raffle at an event. Drawn tickets are shown on a beamer so the whole room can read them.

## Language

**Los**:
A raffle ticket, identified by its Losnummer together with its Losfarbe (if it has one). A green 666 and a blue 666 are different Lose.
_Avoid_: Ticket, Nummer (alone)

**Losnummer**:
The printed number of a Los, a three-digit string where leading zeros matter (`007` is not `7`), usually 001–999.
_Avoid_: ID, Zahl

**Losfarbe**:
The optional colour of a Los. Not every year uses colours.
_Avoid_: Serie, Kategorie

**Ziehung**:
One drawn Los, entered into the list in order of drawing. The most recent Ziehung is the aktuelle Ziehung.
_Avoid_: Eintrag, Draw

**Aktuelle Ziehung**:
The most recently drawn Los, shown large on the Anzeige. If it is Abgeholt, the big slot stays empty until the next Ziehung.

**Frühere Ziehungen**:
The Ziehungen before the aktuelle Ziehung that are not Abgeholt, shown small, newest first.
_Avoid_: Historie, alte Nummern

**Abgeholt**:
A Los whose prize has been collected. Its Ziehung disappears from the Anzeige but stays in the Bediener's list and can be restored.
_Avoid_: Gelöscht (that is a real deletion, for typos)

**Sofort abgeholt**:
A mark set when entering a Ziehung whose winner takes the prize right away. The Los stays the aktuelle Ziehung as usual; when the next Ziehung displaces it, it becomes Abgeholt instead of moving to Frühere Ziehungen.
_Avoid_: Direkt weg, Sofort-Los

**Bediener**:
The person who enters Ziehungen in the form.
_Avoid_: Admin, User

**Anzeige**:
The window shown on the beamer, read-only, showing the aktuelle Ziehung and Frühere Ziehungen.
_Avoid_: Display, Beamer-Fenster
