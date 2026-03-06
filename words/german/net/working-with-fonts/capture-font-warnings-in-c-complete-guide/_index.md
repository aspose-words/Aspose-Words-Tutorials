---
category: general
date: 2026-03-06
description: Erfasse Schriftartwarnungen beim Laden eines Word-Dokuments in C#. Lerne,
  fehlende Schriftarten zu erkennen, die Schriftarten im Dokument zu prüfen und fehlende
  Schriftarten effizient zu behandeln.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: de
og_description: Erfasse Schriftartwarnungen beim Laden eines Word-Dokuments in C#.
  Dieses Tutorial zeigt, wie man fehlende Schriftarten erkennt, die Schriftarten im
  Dokument überprüft und fehlende Schriftarten behandelt.
og_title: Font-Warnungen in C# erfassen – Vollständige Anleitung
tags:
- Aspose.Words
- C#
- Font Management
title: Schriftart‑Warnungen in C# erfassen – Vollständiger Leitfaden
url: /de/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schriftwarnungen in C# erfassen – Komplett‑Anleitung

Haben Sie schon einmal **Schriftwarnungen erfassen** müssen, wenn Sie ein Word‑Dokument verarbeiten? Das Erfassen von Schriftwarnungen ist entscheidend, um **fehlende Schriften** zu erkennen und sicherzustellen, dass die endgültige Ausgabe exakt so aussieht, wie Sie es beabsichtigt haben.  

In diesem Tutorial führen wir Sie durch ein praktisches, durchgängiges Beispiel, das eine `.docx`‑Datei lädt, den Ladevorgang überwacht und alle Schrift‑Substitutionen meldet. Am Ende wissen Sie, wie Sie **Word‑Dokumente** sicher **laden**, **Dokumentschriften prüfen** und **fehlende Schriften** ohne überraschende Laufzeitfehler **handhaben** können.

## Was Sie lernen werden

- Wie Sie einen Warn‑Collector an ein Aspose.Words `Document` anhängen.
- Welche Warn‑Typen auf eine fehlende oder substituierte Schrift hinweisen.
- Möglichkeiten, diese Warnungen in einer produktionsreifen Anwendung zu protokollieren oder darauf zu reagieren.
- Tipps zur Konfiguration benutzerdefinierter Schriftquellen, falls Sie **fehlende Schriften** elegant **handhaben** möchten.

> **Voraussetzung:** Sie besitzen eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder nutzen die kostenlose Testversion) und eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder VS Code). Keine weiteren Bibliotheken sind erforderlich.

---

## Schriftwarnungen erfassen – Schritt für Schritt

Unten finden Sie den vollständigen, ausführbaren Code. Jeder Abschnitt ist in einen eigenen Schritt unterteilt, sodass Sie ihn kopieren, experimentieren und erweitern können.

![Capture font warnings diagram](image.png "Diagramm, das die Warnsammlung zeigt"){: alt="Diagramm zur Erfassung von Schriftwarnungen"}

### Schritt 1: Das Word‑Dokument laden

Zunächst müssen wir **Word‑Dokumente** laden, die Schriften enthalten können, die auf dem aktuellen Rechner nicht installiert sind. Der `Document`‑Konstruktor übernimmt die schwere Arbeit, aber wir halten den Aufruf isoliert, damit Sie später bei Bedarf einen Stream oder ein Byte‑Array einsetzen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Warum das wichtig ist:** Wird ein Dokument ohne Warn‑Handler geladen, wird jede Schrift‑Substitution stillschweigend ignoriert. Durch das Setzen von `WarningCallback` *vor* dem Laden stellen wir sicher, dass wir jede `FontSubstitution`‑Warnung sehen.

### Schritt 2: Einen Warn‑Collector anhängen

Die Klasse `WarningInfoCollector` ist eine integrierte Implementierung von `IWarningCallback`. Sie speichert jede Warnung einfach in einer Liste, die wir später inspizieren können.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Pro‑Tipp:** Wenn Sie **fehlende Schriften** aggressiver **handhaben** wollen (z. B. den Ladevorgang abbrechen oder durch eine bestimmte Ersatzschrift ersetzen), können Sie das `Console.WriteLine` durch eigene Logik ersetzen – eine Ausnahme werfen, in eine Datei schreiben oder sogar eine benutzerdefinierte Schriftquelle hinzufügen.

### Schritt 3: Die Ausgabe prüfen

Führen Sie das Programm in einer Konsole aus. Wenn Ihr `input.docx` eine Schrift verwendet, die nicht installiert ist, sehen Sie Zeilen wie:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Erscheint keine Ausgabe, hat das Dokument entweder nur bereits verfügbare Schriften verwendet **oder** Aspose.Words hat eine passende Schrift in seiner integrierten Ersatzsammlung gefunden. In jedem Fall haben Sie **Dokumentschriften geprüft**.

---

## Fehlende Schriften ohne Lizenz erkennen (Kostenlose Testversion)

Selbst wenn Sie die 30‑Tage‑Testversion nutzen, funktioniert der Warn‑Mechanismus exakt gleich. Der einzige Unterschied ist, dass die Testversion ein Wasserzeichen zur erzeugten Ausgabe hinzufügt, was **keinen Einfluss** auf die Warn‑Erfassung hat. So können Sie **fehlende Schriften** sicher erkennen, bevor Sie sich für den Kauf einer Voll‑Lizenz entscheiden.

---

## Fehlende Schriften handhaben – Erweiterte Optionen

Manchmal möchten Sie eigene Schriftdateien bereitstellen (z. B. Unternehmens‑Brand‑Fonts), damit die Substitution nie stattfindet. Aspose.Words ermöglicht das Registrieren benutzerdefinierter Schriftordner:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Platzieren Sie den obigen Code **vor** dem Laden des Dokuments, wenn Sie möchten, dass der Loader diese Schriften bereits während der ersten Parsing‑Phase berücksichtigt. Das ist der zuverlässigste Weg, **fehlende Schriften** zu **handhaben**, ohne sich auf die Standardsystemschriften zu verlassen.

---

## Häufige Stolperfallen & wie man sie vermeidet

| Stolperfalle | Warum sie auftritt | Lösung |
|--------------|--------------------|--------|
| **Warn‑Collector nach dem Laden angehängt** | Das Dokument ist bereits geparst, daher werden keine Warnungen erfasst. | `WarningCallback` **vor** `new Document(path)` setzen. |
| **Nur generische Warnungen erscheinen** | Es wurde nach dem falschen `WarningType` gefiltert. | `WarningType.FontSubstitution` verwenden, um sich auf Schrift‑Probleme zu konzentrieren. |
| **Keine Ausgabe trotz fehlender Schriften** | Aspose.Words hat einen integrierten Ersatz gefunden (z. B. Arial). | Eingebaute Ersatzschriften über `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` deaktivieren. |
| **Leistungsabfall bei großen Dokumenten** | Das Sammeln jeder Warnung kann teuer sein. | Sammlung auf `FontSubstitution` beschränken oder Warnungen stapelweise verarbeiten. |

---

## Vollständiges Beispiel (Kopier‑fertig)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Erwartete Konsolenausgabe** (bei zwei fehlenden Schriften):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Bleibt die Konsole still, abgesehen von „Document loaded successfully“, haben Sie **Dokumentschriften geprüft** und keine fehlenden Schriften gefunden.

---

## Fazit

Wir haben gezeigt, wie Sie **Schriftwarnungen** in C# mit Aspose.Words erfassen, um **fehlende Schriften** zu **erkennen**, **Word‑Dokumente** sicher zu **laden**, **Dokumentschriften** zu **prüfen** und **fehlende Schriften** über benutzerdefinierte Schriftquellen zu **handhaben**.  

Mit diesem Muster können Sie die Schrift‑Validierung in jede Automatisierungspipeline integrieren – sei es beim Erzeugen von PDFs, Konvertieren nach HTML oder einfach beim Archivieren von Word‑Dateien.

### Was kommt als Nächstes?

- Erkunden Sie die **FontSettings.SubstitutionSettings**‑API, um eigene Ersatzregeln zu definieren.
- Kombinieren Sie die Warn‑Erfassung mit einem Logging‑Framework (Serilog, NLog) für die Produktionsüberwachung.
- Nutzen Sie denselben Ansatz, um andere Warn‑Typen zu erfassen, etwa Bildauflösung oder nicht unterstützte Features.

Haben Sie weitere Fragen zur Schrift‑Handhabung oder zu Aspose.Words im Allgemeinen? Hinterlassen Sie einen Kommentar oder besuchen Sie die Aspose‑Community‑Foren. Viel Spaß beim Coden, und mögen Ihre Dokumente stets mit den erwarteten Schriften dargestellt werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}