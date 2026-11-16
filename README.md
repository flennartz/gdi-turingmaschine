# Turingmaschinen-Simulator

Ein interaktiver Simulator für deterministische Turingmaschinen im Browser. Er entstand für die Lehrveranstaltung
**Grundlagen der Informatik (GdI)**. Die Maschine wird über ihre Übergangstabelle festgelegt und läuft auf einem
frei wählbaren Band. Dabei sieht man Band, Zustandsdiagramm und Konfigurationsfolge zugleich.

**Direkt ausprobieren:** `https://<github-name>.github.io/<repository>/`

## Funktionen

- **Übergangstabelle bearbeiten:** Die Spalten sind aktueller Zustand, Eingabe, neuer Zustand, Ausgabe und Laufrichtung (`R`, `L`, `-`).
  Zeilen lassen sich hinzufügen und löschen. Fehler werden sofort gemeldet, z. B. fehlende Felder oder doppelte Übergänge.
- **Sonderzeichen:** Querstrich (ā) und Punkt (ȧ) setzt man per Knopf. LaTeX wie `\overline{a}`, `\dot{a}` oder `\#`
  wird automatisch umgewandelt.
- **Zustandsdiagramm:** Es wird automatisch aus der Tabelle erzeugt. Der aktuelle Zustand pulsiert bei jedem Schritt,
  der nächste Übergang ist farbig markiert.
- **Animiertes Band:** Der Schreib-/Lesekopf zeigt den aktuellen Zustand. Ablauf schrittweise, rückwärts, automatisch mit
  einstellbarem Tempo oder sofort bis zum Ende.
- **Ergebnis:** Die Seite zeigt, ob die Eingabe akzeptiert wird (Halt im Endzustand) oder nicht (kein passender Übergang),
  und den Bandinhalt. Nach 10.000 Schritten kommt ein Hinweis auf eine mögliche Endlosschleife.
- **Protokoll:** Es listet die vollständige Folge der Konfigurationen.
- **Import und Export:** Tabellen lassen sich als Markdown mit LaTeX-Notation einfügen und ausgeben.
- **Beispiele mit Testeingaben:**
  - a verdoppeln
  - Wörter der Form aⁱbⁱ erkennen
  - Bits invertieren
  - Binärzahl um 1 erhöhen
  - Unärzahlen addieren

## Konventionen

| Regel | Bedeutung |
| --- | --- |
| Startzustand | immer `s0` |
| Kopfposition zu Beginn | erstes Zeichen der Eingabe |
| `#` | leeres Feld; das Band ist links und rechts damit gefüllt |
| Zeile mit `STOP` als Eingabe | markiert einen Endzustand |
| Kein passender Übergang | Die Maschine hält, die Eingabe gilt als nicht akzeptiert. |

## Tabellenformat für den Import

```markdown
| aktueller Zustand | Eingabe | neuer Zustand | Ausgabe | Laufrichtung |
| ------ | ------ | ------ | ------ | ------ |
| $`s_0`$ | a | $`s_1`$ | $`\overline{a}`$ | R |
| $`s_1`$ | a | $`s_1`$ | a | R |
| $`s_0`$ | $`\#`$ | $`s_e`$ | $`\#`$ | - |
| $`s_e`$ | STOP |  |  |  |
```

Ohne senkrechte Striche genügt eine Zeile je Übergang, z. B. `s0 a s1 ā R` oder `se STOP`.

## Technik

- Eine einzige Datei `index.html` mit HTML, CSS und JavaScript, ohne externe Bibliotheken und ohne Build-Schritt
- Läuft vollständig im Browser; es werden keine Daten gespeichert oder übertragen

## In Moodle einbinden

- **Link oder eingebettet:** Aktivität **URL** mit der GitHub-Pages-Adresse anlegen. Unter „Darstellung“
  „In neuem Fenster“ oder „Einbetten“ wählen.
- **Als iframe** in einer Textseite (HTML-Quellcode-Ansicht):

  ```html
  <iframe src="https://<github-name>.github.io/<repository>/" width="100%" height="1400" style="border:0"></iframe>
  ```
