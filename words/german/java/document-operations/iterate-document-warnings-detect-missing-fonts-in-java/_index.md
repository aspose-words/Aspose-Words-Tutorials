---
category: general
date: 2026-04-28
description: Iterieren Sie die Dokumentwarnungen in einer Word-Datei, um fehlende
  Schriftarten zu erkennen, rufen Sie die Namen der fehlenden Schriftarten ab und
  geben Sie die Details der fehlenden Schriftarten mit Aspose.Words für Java aus.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: de
og_description: Durchlaufen Sie Dokumentwarnungen, um fehlende Schriften zu finden,
  rufen Sie die Namen fehlender Schriften ab und geben Sie die Details fehlender Schriften
  mit einem vollständigen Java‑Beispiel aus.
og_title: 'Iteriere Dokumentwarnungen: Fehlende Schriftarten in Java erkennen'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Dokumentwarnungen durchlaufen: Fehlende Schriftarten in Java erkennen'
url: /de/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentwarnungen iterieren – Fehlende Schriftarten in Java erkennen

Haben Sie jemals **Dokumentwarnungen iterieren** müssen, wenn Sie eine Word‑Datei öffnen, und sich gefragt, welche Schriftarten fehlen? Sie sind nicht allein. Fehlende Schriftarten können das Aussehen eines Berichts zerstören, und ohne eine Möglichkeit, sie zu erkennen, könnten Sie ein Dokument ausliefern, das überhaupt nicht dem Original entspricht.  

In diesem Tutorial zeigen wir Ihnen, wie Sie **fehlende Schriftarten erkennen** können, indem Sie ein Word‑Dokument laden, seine Warnungen iterieren, die fehlenden Schriftartnamen abrufen und schließlich die Informationen zu fehlenden Schriftarten ausgeben – alles mit Aspose.Words für Java.  

Wir decken alles vom allerersten Code‑Zeile bis zur erwarteten Konsolenausgabe ab, sodass Sie die funktionierende Lösung jetzt sofort in Ihr Projekt kopieren‑und‑einfügen können. Keine zusätzlichen Dokumente erforderlich.

## Voraussetzungen

- Java 8 oder neuer installiert.
- Aspose.Words für Java Bibliothek (die neueste Version vom 2026‑04‑28).
- Eine Word‑Datei, die potenziell Schriftarten enthält, die nicht auf Ihrem Rechner installiert sind (z. B. `doc-with-missing-font.docx`).

Wenn Sie das bereits haben, großartig – Sie sind bereit, das **Word‑Dokument zu laden** und mit dem Iterieren zu beginnen.

## Schritt 1 – Word‑Dokument mit Standardoptionen laden

Bevor wir **Dokumentwarnungen iterieren** können, muss die Datei in den Speicher geladen werden. Aspose.Words ermöglicht dies mit einem einzigen Konstruktoraufruf. Die Verwendung der Standard‑`LoadOptions` reicht normalerweise aus, aber wir zeigen die explizite Erstellung zur Verdeutlichung.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Warum das wichtig ist:**  
> Das Laden des Dokuments veranlasst Aspose.Words, die Datei nach Ressourcen zu durchsuchen, die nicht aufgelöst werden können, wie z. B. nicht lokal installierte Schriftarten. Diese Probleme werden als **Warnungen** gespeichert, die wir im nächsten Schritt **Dokumentwarnungen iterieren** werden.

## Schritt 2 – Dokumentwarnungen iterieren, um Schriftart‑Probleme zu finden

Jetzt kommt das Herzstück der Lösung: Wir durchlaufen jede Warnung, die die Bibliothek beim Laden gesammelt hat. Die `WarningInfo`‑Objekte sagen uns, was schiefgelaufen ist, und wir können nach `FontSubstitutionWarning` filtern, um **fehlende Schriftarten zu erkennen**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Pro‑Tipp:** Die `instanceof`‑Prüfung stellt sicher, dass wir nur schriftbezogene Warnungen behandeln und andere wie Bild‑Lade‑Probleme ignorieren. Das macht die Schleife effizient und hält die Ausgabe auf die Schriftarten fokussiert, für die Sie **fehlende Schriftart**‑Informationen **abrufen** müssen.

### Erwartete Konsolenausgabe

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Enthält das Dokument keine fehlenden Schriftarten, beendet sich die Schleife einfach stillschweigend – nichts zum **fehlende Schriftart drucken**.

## Schritt 3 – Warum nicht einfach eine Ausnahme abfangen?

Sie fragen sich vielleicht: „Warum nicht den Aufruf `new Document(...)` in ein try‑catch packen und nach einer Ausnahme suchen?“ Die Antwort ist zweifach:

1. **Granulare Informationen:** Ausnahmen sagen nur, dass etwas fehlgeschlagen ist. Warnungen geben den genauen Schriftartnamen und den Fallback an, den Aspose.Words gewählt hat.
2. **Nicht‑kritische Probleme:** Fehlende Schriftarten sind in der Regel nicht fatal; das Dokument wird trotzdem geladen, aber die visuelle Treue leidet. Durch **Dokumentwarnungen iterieren** behalten Sie die Möglichkeit, den Rest der Datei zu verarbeiten.

## Schritt 4 – Beispiel erweitern: Fehlende Schriftarten in einer Liste sammeln

Manchmal benötigen Sie die fehlenden Schriftarten für weitere Verarbeitung – etwa zum Einbetten oder um den Benutzer über die UI zu informieren. Hier ein kurzer Patch, der die Namen in ein `Set<String>` sammelt.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Jetzt haben Sie eine saubere Methode, um **fehlende Schriftart**‑Daten programmgesteuert **abzurufen**, die Sie in ein Reporting‑Modul oder einen Schrift‑Installations‑Assistenten einspeisen können.

## Schritt 5 – Praktische Überlegungen

- **Mehrfache Substitutionen:** Eine fehlende Schriftart kann an verschiedenen Stellen des Dokuments durch unterschiedliche Schriftarten ersetzt werden. Die Warnungsliste enthält jeden Auftritt, sodass Sie doppelte Einträge sehen können.
- **Performance:** Das Laden sehr großer Dokumente kann tausende Warnungen erzeugen. Wenn Sie nur an Schriftarten interessiert sind, filtern Sie früh, wie oben gezeigt, um die Schleife schnell zu halten.
- **Plattformübergreifende Schriftarten:** Unter Linux ist die Standard‑Substitutionsschriftart häufig *Liberation Sans*. Unter Windows kann es *Arial* sein. Das Wissen um den Fallback hilft Ihnen zu entscheiden, ob Sie benutzerdefinierte Schriftarten mit Ihrer Anwendung ausliefern müssen.

## Schritt 6 – Visuelle Hilfe

Unten sehen Sie einen Screenshot der Konsolenausgabe (Alt‑Text enthält das Haupt‑Keyword für SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt‑Text:* *Beispiel für das Iterieren von Dokumentwarnungen, das fehlende Schriftartnamen und Substitutionsdetails anzeigt.*

## Fazit

Sie haben gerade gelernt, wie man **Dokumentwarnungen iteriert** in Aspose.Words für Java, **fehlende Schriftarten erkennt**, **Word‑Dokument sicher lädt**, **fehlende Schriftart**‑Informationen **abrufen** und **fehlende Schriftart**‑Details in der Konsole **ausgibt**. Der komplette Code‑Abschnitt läuft sofort, und Sie können ihn anpassen, um in eine Datei zu protokollieren, einen UI‑Dialog anzuzeigen oder die fehlenden Schriftarten automatisch einzubetten.

Als Nächstes könnten Sie erkunden, wie man das **Word‑Dokument lädt** mit benutzerdefinierten Schriftquellen (z. B. einem Ordner mit Unternehmensschriftarten) oder wie man fehlende Schriftarten direkt in die Datei einbettet, um das Layout auf allen Rechnern zu erhalten. Beide Themen bauen natürlich auf dem hier behandelten auf.

Viel Spaß beim Coden, und mögen Ihre PDFs immer exakt so aussehen, wie Sie es beabsichtigen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}