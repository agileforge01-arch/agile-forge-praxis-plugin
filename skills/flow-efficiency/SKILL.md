---
name: flow-efficiency
description: Berechnet die Flow Efficiency eines Vorgangs aus Durchlaufzeit und aktiver Bearbeitungszeit, zeigt Wartezeit und zwei Hebel mit eingesetzten Zahlen. Nutzen bei Fragen wie "Wie hoch ist unsere Flow Efficiency?", "Wie viel davon ist Warten?" oder wenn jemand Lead Time und Touch Time nennt. Calculates flow efficiency from lead time and touch time (English input is fine).
---

# Flow Efficiency berechnen

Flow Efficiency ist der Anteil der Durchlaufzeit, in dem tatsächlich an einem Vorgang gearbeitet wird. Antworte in der Sprache der Nutzerin oder des Nutzers.

## Eingaben erfragen

Frage nur nach dem, was fehlt:

1. **Durchlaufzeit** in Tagen: vom Auslöser (erste Anfrage, nicht erster Arbeitsschritt) bis zum nutzbaren Ergebnis beim Anforderer. Frage, ob es **Arbeitstage** oder **Kalendertage** sind.
2. **Bearbeitungszeit** in Stunden: Zeit, in der jemand aktiv am Vorgang arbeitet, einschließlich tatsächlich durchgeführter Prüfungen und Freigaben. Liegezeiten (Postfach, Queue, Batch-Fenster, Warten auf Termine oder Release-Slots) zählen nicht.
3. Optional: **Vorgänge pro Jahr** für die Hochrechnung.

Frage nach, wenn unklar ist, was als aktive Arbeit zählt. Automatisierte Bearbeitung ohne menschlichen Eingriff ist keine Liegezeit, wenn sie wirklich läuft.

## Rechnung

Mit `d` = Tage, `h` = Stunden Bearbeitung, `n` = Vorgänge pro Jahr. Ein Arbeitstag hat 8 Stunden.

- Arbeitstage = `d` bei Arbeitstagen, `d × 5/7` bei Kalendertagen (Näherung, Feiertage bleiben unberücksichtigt)
- Durchlaufzeit in Stunden = Arbeitstage × 8
- Wartezeit in Stunden = Durchlaufzeit − `h`
- **Flow Efficiency = `h` ÷ Durchlaufzeit in Stunden × 100**
- Jahres-Hochrechnung = Wartetage pro Vorgang × `n`. Das ist eine Summe von Vorgangs-Tagen und keine Kalenderzeit, weil viele Vorgänge parallel warten. Beschrifte sie so.

Zwei Hebel, jeder verändert nur seine eigene Komponente:

- **Hebel A, Bearbeitung schneller um Faktor f** (Beispiel f = 2): neue Durchlaufzeit = Wartezeit + `h` ÷ f
- **Hebel B, Wartezeit sinkt um Anteil r** (Beispiel r = 0,5): neue Durchlaufzeit = Wartezeit × (1 − r) + `h`

Rechne beide Hebel durch, nenne die Einsparung in Tagen und sage, welcher größer ist. Das kippt bei etwa 50 % Flow Efficiency, dann ist die Bearbeitungszeit der größere Hebel. Zeige die Formeln mit eingesetzten Zahlen, damit man nachrechnen kann. Runde nur die Anzeige und verbinde gerundete Werte mit "≈" statt "=".

## Eingaben ablehnen

- Tage oder Stunden leer, nicht numerisch oder ≤ 0: nachfragen
- Stunden größer als Arbeitstage × 8: das passt nicht, nenne die Kapazitätsrechnung und frage nach
- Tage > 5000: wahrscheinlich Tippfehler
- Vorgänge pro Jahr < 0 oder > 100 000: nachfragen; 0 gilt als "nicht angegeben"

## Einordnung

- Die Zahl beschreibt das Verhältnis von Arbeiten und Warten, sie bewertet nicht. **Nenne keinen Normalwert und keine Faustregel wie "5 bis 15 % ist typisch".** Dafür gibt es keine belastbare Quelle. Die einzige größere veröffentlichte Messung (Nick Brown, ASOS Tech Blog, 27.07.2023, 63 Teams über zwölf Monate) fand 9 bis 68 % bei einem Mittel von 35 %, und sie stammt aus einem einzigen Unternehmen. Sie ist kein Branchenvergleich. Der tragfähige Vergleich ist der eigene Prozess, in einigen Wochen erneut gemessen.
- Ist das Ergebnis unter 5 %, bitte prüfen: Deckt die Schätzung der Bearbeitungszeit wirklich jede Minute ab? Wurde automatisierte Arbeit als Warten gezählt?
- Ist das Ergebnis genau 100 %, gibt es keine Wartezeit. Das hält selten, prüfe gemeinsam, wo die Uhr gestartet und gestoppt wurde.
- Weise auf die Grenzen hin: (1) Ein einzelner Vorgang ist eine Größenordnung, keine Prozessaussage. Erst mehrere Vorgänge und ihre Streuung tragen Schlüsse. (2) Die Kennzahl sagt, wie schnell etwas fließt, nicht, ob das Richtige fließt. (3) Sie diagnostiziert das System und eignet sich nicht zur Bewertung von Personen oder Teams.

## Beispiel zur Kontrolle

3 Arbeitstage, 20 Stunden Bearbeitung: Durchlaufzeit 24 h, Wartezeit 4 h, Flow Efficiency 83,3 %.

42 Kalendertage, 16 Stunden Bearbeitung: 42 × 5/7 = 30 Arbeitstage = 240 h, Wartezeit 224 h (28 Tage), Flow Efficiency 6,7 %. Hebel A mit f = 2: 224 + 8 = 232 h, also 29 Tage (1 Tag gespart). Hebel B mit r = 0,5: 112 + 16 = 128 h, also 16 Tage (14 Tage gespart). Hier ist die Wartezeit der klar größere Hebel.
