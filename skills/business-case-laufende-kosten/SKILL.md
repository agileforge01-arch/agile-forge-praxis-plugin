---
name: business-case-laufende-kosten
description: Rechnet einen einfachen Business Case mit einmaligen Projektkosten, laufenden Kosten pro Jahr und Nutzen pro Jahr, zeigt den Anteil der laufenden Kosten, Amortisation und wie weit die Annahmen danebenliegen dürfen. Nutzen bei "Lohnt sich das?", "Business Case prüfen" oder bei einem Vorhaben, bei dem die Betriebskosten fehlen könnten. Calculates a simple business case with ongoing costs (English input is fine).
---

# Business Case mit den laufenden Kosten rechnen

Der häufigste Fehler in Business Cases ist keine falsche Rechenart, sondern eine fehlende Kostenposition: die laufenden Kosten nach dem Go-live. Dieser Skill stellt drei Zahlen nebeneinander und zeigt, wie weit die Annahmen danebenliegen dürfen, bevor die Rechnung kippt. Antworte in der Sprache der Nutzerin oder des Nutzers.

## Eingaben erfragen

1. **Einmalige Projektkosten** `p` in Euro: alles bis zum Go-live (Entwicklung, Integration, Datenaufbereitung, Einführung, Schulung beim Rollout).
2. **Laufende Kosten pro Jahr** `l`: Hosting, Lizenzen, bei KI-Vorhaben auch API-, Token- und Inferenzkosten, Support, Wartung, Modell- und Versionsupdates, Governance-Aufwand (Stichproben, Audits, Nachweise), anteilige dauerhafte Betreuung. Die Nachschulung neuer Mitarbeitender ab Jahr zwei gehört hierher. Eine Null ist fast immer falsch. Bitte lieber grob schätzen lassen.
3. **Erwarteter Nutzen pro Jahr** `n` im eingeschwungenen Zustand: vermiedene Kosten, Zeitersparnis, zusätzlicher Ertrag. Zeitersparnis zählt nur, soweit entschieden ist, was mit der Zeit passiert (Stelle nicht nachbesetzt, Rückstand abgebaut, zusätzlicher Auftrag angenommen). Zusätzlichen Ertrag konservativ ansetzen.
4. **Zeitraum** `j`: 3 oder 5 Jahre, Voreinstellung 3.

## Rechnung

Ohne Reglerabweichung (a = 1, u = 0):

- Laufende Kosten gesamt = `l × j`
- Gesamtkosten = `p + l × j`
- Gesamtnutzen = `n × j`
- Ergebnis = Gesamtnutzen − Gesamtkosten
- **Anteil laufender Kosten = `l × j` ÷ Gesamtkosten × 100**. Das ist die Leitzahl.
- Überschuss pro Monat = `(n − l) ÷ 12`
- **Amortisation in Monaten = `p` ÷ Überschuss pro Monat**; ist der Überschuss ≤ 0, schreibe "nie". Über 600 Monate sage "über 50 Jahre" und weise darauf hin, dass der Nutzen die laufenden Kosten nur um einen Kleinstbetrag übersteigt.
- ROI = Ergebnis ÷ Gesamtkosten × 100
- **Break-even-Nutzung** `a*` = `(p + l × j)` ÷ `(n × j)`: Anteil des geplanten Nutzens, bei dem das Ergebnis null wird
- **Break-even-Kostenüberschreitung** `u*` = `(n × j − p − l × j)` ÷ `(l × j)`: um wie viel die laufenden Kosten steigen dürfen

Zeige zwei Abweichungen:

- Nutzung nur 70 % des Plans: wirksamer Nutzen = `n × 0,7`, laufende Kosten bleiben (sie hängen meist nicht von der Nutzung ab)
- Laufende Kosten höher um `u`: wirksame laufende Kosten = `l × (1 + u)`, der Nutzen bleibt

Sage dann, welcher Regler voll aufgedreht mehr kostet: Verlust durch geringere Nutzung = `(1 − 0,4) × n × j`, Verlust durch höhere laufende Kosten = `1,0 × l × j`. Der größere gewinnt, nenne ihn nach der Rechnung und nicht vorab.

Zeige die Formeln mit eingesetzten Zahlen. Runde nur die Anzeige und verbinde gerundete Werte mit "≈" statt "=".

## Eingaben ablehnen

- Ein Betrag fehlt, ist nicht numerisch oder negativ: nachfragen
- Projektkosten und laufende Kosten beide 0: ohne Kosten gibt es nichts zu rechnen
- Nutzen = 0: kein Business Case. Bitte grob schätzen, denn eine grobe Zahl ist eine Aussage, eine Null ist keine.
- Betrag über 1 Milliarde Euro: wahrscheinlich Tippfehler
- Laufende Kosten = 0 ist zulässig, aber weise darauf hin, dass dann mit einem Vorhaben gerechnet wird, das nach dem Go-live nichts kostet

## Einordnung

Der Anteil laufender Kosten steuert nur, was du dazu sagst, er bewertet nicht. Nenne **keinen Vergleichswert und keine Faustregel**. Er hängt vom Vorhabentyp ab, und eine erfundene Regel wäre genau der Fehler, den man vermeiden will.

- Unter 25 %: Das Projektbudget dominiert. Das kommt vor, ist aber auch das Muster einer zu knapp geschätzten Betriebsseite. Bitte die Liste der laufenden Kosten noch einmal durchgehen.
- 25 bis 60 %: Ein erheblicher Teil der Kosten entsteht nach dem Go-live. Wer nur die Projektkosten nennt, lässt diese Zahl weg.
- Über 60 %: Das Projekt ist der kleinere Teil der Rechnung. Wer nur die Projektsumme genehmigen lässt, genehmigt weniger als die Hälfte der Entscheidung.
- Liegt der Nutzen nicht über den laufenden Kosten, amortisiert sich das Vorhaben nie, unabhängig von den Projektkosten. Sage das deutlich: Entweder ist der Nutzen zu vorsichtig geschätzt, oder die Rechnung trägt nicht.

Nenne die Grenzen: keine Abzinsung (ein Euro in Jahr drei zählt wie einer heute, den Kalkulationszinssatz setzt das Controlling), konstanter Nutzen ab Go-live ohne Anlaufkurve, Vergleich gegen einen unveränderten Status quo, keine Steuern, Abschreibung oder Aktivierung. Eine Zahl ist noch kein Business Case, das Eigentliche sind die Annahmen darunter.

## Beispiel zur Kontrolle

p = 180.000 €, l = 24.000 €, n = 150.800 €, j = 3: laufende Kosten gesamt 72.000 €, Gesamtkosten 252.000 €, Gesamtnutzen 452.400 €, Ergebnis 200.400 €, Anteil laufender Kosten 28,6 %, Überschuss 10.566,67 € pro Monat, Amortisation 17,0 Monate, ROI 79,5 %. Break-even-Nutzung 55,7 %, Break-even-Kostenüberschreitung +278 %. Bei 70 % Nutzung bleiben 64.680 € Ergebnis, also 32 % des Ausgangsergebnisses.

Hinweis zur Amortisation: Manche Lehrbücher rechnen `(p + l) ÷ n × 12`. Diese Form unterstellt, die laufenden Kosten fielen nur einmal an, und bricht bei hohen laufenden Kosten zusammen. Dieser Skill zieht die laufenden Kosten vom Nutzen ab und tilgt damit nur die Projektinvestition.
