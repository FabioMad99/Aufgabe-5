# Aufgabe 2.1 – Äquivalenzklassenbildung und Grenzwertanalyse

## Äquivalenzklassen

### Fahrradtyp

| Klasse | Gültig |
|----------|----------|
| RACE | Ja |
| SINGLE_SPEED | Ja |
| FIXIE | Ja |
| GRAVEL | Nein |
| EBIKE | Nein |

---

### Bereits vorhandener Auftrag des Kunden

| Klasse | Gültig |
|----------|----------|
| Kunde besitzt keinen offenen Auftrag | Ja |
| Kunde besitzt bereits einen offenen Auftrag | Nein |

Pro Kunde darf sich maximal ein Auftrag gleichzeitig in der Warteschlange befinden.

---

### Anzahl offener Aufträge

| Klasse | Gültig |
|----------|----------|
| 0 bis 4 offene Aufträge | Ja |
| 5 oder mehr offene Aufträge | Nein |

Es dürfen sich maximal fünf offene Aufträge gleichzeitig in der Warteschlange befinden.

---

## Grenzwertanalyse

Für die Anzahl offener Aufträge ergibt sich folgender Grenzwert:

| Offene Aufträge vor dem Einfügen | Erwartetes Ergebnis |
|----------|----------|
| 4 | Auftrag wird angenommen |
| 5 | Auftrag wird abgelehnt |

Bei vier vorhandenen Aufträgen darf noch ein fünfter Auftrag angenommen werden. Bei bereits fünf vorhandenen Aufträgen darf kein weiterer Auftrag mehr angenommen werden.

---

## Testfälle

### Testfall 1 – Gültiger Auftrag

Voraussetzungen:

- Fahrradtyp: RACE
- Kunde besitzt keinen offenen Auftrag
- Keine offenen Aufträge vorhanden

Erwartetes Ergebnis:

- Rückgabewert: true

---

### Testfall 2 – Gravel-Bike

Voraussetzungen:

- Fahrradtyp: GRAVEL
- Kunde besitzt keinen offenen Auftrag
- Keine offenen Aufträge vorhanden

Erwartetes Ergebnis:

- Rückgabewert: false

---

### Testfall 3 – E-Bike

Voraussetzungen:

- Fahrradtyp: EBIKE
- Kunde besitzt keinen offenen Auftrag
- Keine offenen Aufträge vorhanden

Erwartetes Ergebnis:

- Rückgabewert: false

---

### Testfall 4 – Kunde besitzt bereits offenen Auftrag

Voraussetzungen:

- Ein Auftrag des Kunden befindet sich bereits in der Warteschlange
- Neuer Auftrag desselben Kunden

Erwartetes Ergebnis:

- Rückgabewert: false

---

### Testfall 5 – Grenzwert 4 offene Aufträge

Voraussetzungen:

- Vier offene Aufträge vorhanden
- Neuer Auftrag eines anderen Kunden

Erwartetes Ergebnis:

- Rückgabewert: true

---

### Testfall 6 – Grenzwert 5 offene Aufträge

Voraussetzungen:

- Fünf offene Aufträge vorhanden
- Neuer Auftrag eines anderen Kunden

Erwartetes Ergebnis:

- Rückgabewert: false

---

### Begründung MOckito

Die Klasse `Order` ist in der Vorgabe nicht vollständig implementiert. Die Methoden `getBicycleType()` und `getCustomer()` werfen jeweils eine `UnsupportedOperationException`.

Um die Methode `Shop.accept()` testen zu können, werden Mock-Objekte mit Mockito verwendet. Dabei werden die Rückgabewerte der benötigten Methoden simuliert, ohne dass eine vollständige Implementierung der Klasse `Order` erforderlich ist.

Dadurch kann die Methode `Shop.accept()` getestet werden, während gleichzeitig die vorgegebene Implementierung der Methode selbst unverändert genutzt wird.