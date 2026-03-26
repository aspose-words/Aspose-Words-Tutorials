---
category: general
date: 2026-03-25
description: Erstellen Sie einen Warnungs‑Callback, um ein Word‑Dokument zu laden
  und fehlende Schriftarten zu erkennen. Erfahren Sie, wie Sie die Schriftarteinstellungen
  in Aspose.Words für .NET konfigurieren.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: de
og_description: Erstellen Sie einen Warnungs‑Callback, um ein Word‑Dokument zu laden
  und fehlende Schriftarten zu erkennen. Dieser Leitfaden zeigt, wie Sie die Schriftarteinstellungen
  in Aspose.Words konfigurieren.
og_title: Warnungs‑Callback erstellen – Word‑Dokument laden & fehlende Schriftarten
  erkennen
tags:
- Aspose.Words
- C#
- Font handling
title: Warn-Callback für das Laden von Word-Dokumenten erstellen – Komplettanleitung
url: /de/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Warnungs‑Callback erstellen – Word‑Dokument laden & fehlende Schriftarten erkennen

Haben Sie jemals einen **Warnungs‑Callback erstellen** müssen, wenn Sie ein Word‑Dokument laden, und sich gefragt, warum manche Schriftarten einfach verschwinden? Sie sind nicht allein. In vielen Unternehmens‑Apps führen fehlende Schriftarten zu Layout‑Desastern, und ohne einen geeigneten Callback bemerken Sie das Problem vielleicht nie.  

Die gute Nachricht? Mit Aspose.Words für .NET können Sie **Word‑Dokument laden**, **fehlende Schriftarten erkennen** und **Schrifteinstellungen konfigurieren** – alles in wenigen übersichtlichen Code‑Zeilen. In diesem Tutorial führen wir Sie durch ein vollständiges, ausführbares Beispiel, erklären, warum jedes Teil wichtig ist, und zeigen Ihnen, wie Sie überprüfen können, dass der Warnungs‑Callback seine Aufgabe erfüllt.

> **Was Sie am Ende haben**  
> * Ein vollständiges C#‑Programm, das ein DOCX lädt, etwaige Schriftart‑Ersetzungen meldet und Ihnen ermöglicht, Schriftart‑Suchpfade anzupassen.  
> * Verständnis der Klassen `FontSettings`, `LoadOptions` und `IWarningCallback`.  
> * Tipps zum Umgang mit Sonderfällen wie eingebetteten Schriftarten oder systemweiten Schriftordnern.

---

## Voraussetzungen

- .NET 6+ (oder .NET Framework 4.7.2+) mit einem C#‑Compiler.  
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`).  
- Eine Beispiel‑Word‑Datei (`input.docx`), die mindestens eine Schriftart verwendet, die nicht auf dem Rechner installiert ist (z. B. *Calibri Light* in einem minimalen Windows‑Container).  
- Grundlegende Erfahrung mit C#‑Konsolen‑Apps.

Keine zusätzlichen Bibliotheken sind erforderlich; alles befindet sich innerhalb von Aspose.Words.

---

## Schritt 1: Warnungs‑Callback erstellen, um fehlende Schriftarten zu erkennen

Das **primäre** Element dieses Puzzles ist eine Klasse, die `IWarningCallback` implementiert. Aspose.Words ruft diesen Callback auf, sobald es auf eine Situation stößt, die eine Warnung rechtfertigt – die Schriftart‑Ersetzung ist dabei die häufigste.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Warum das wichtig ist** – Ohne einen Callback müssten Sie nachträglich die Protokolle durchsuchen. Durch das Echtzeit‑Handling von Warnungen können Sie entscheiden, ob Sie das Laden abbrechen, die fehlende Schriftart durch eine Ersatzschrift ersetzen oder das Problem einfach für eine spätere Überprüfung protokollieren.

---

## Schritt 2: FontSettings für benutzerdefinierte Schriftarten‑Verarbeitung konfigurieren

Bevor wir das Dokument tatsächlich laden, möchten wir Aspose.Words mitteilen, wo nach Schriftarten gesucht werden soll, die nicht im System vorhanden sind. Hier kommt `FontSettings` ins Spiel.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Warum das wichtig ist** – Indem Sie Aspose.Words auf einen Ordner verweisen, der die fehlenden Schriftarten enthält, vermeiden Sie häufig die Ersetzung komplett. Wenn das nicht möglich ist, sorgt ein sinnvoller Standard (wie *Arial*) dafür, dass das Dokument lesbar bleibt.

---

## Schritt 3: Word‑Dokument mit dem konfigurierten Warnungs‑Callback laden

Jetzt verbinden wir alles: Wir erstellen `LoadOptions`, binden unsere `FontSettings` und `FontWarningHandler` ein und laden schließlich das Dokument.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Warum das wichtig ist** – `LoadOptions` ist der zentrale Ort, an dem Sie festlegen, *wie* ein Dokument gelesen wird. Durch die Bereitstellung sowohl der Schriftart‑Konfiguration als auch des Warnungs‑Callbacks stellen Sie sicher, dass jede fehlende Schriftart sowohl an den richtigen Stellen gesucht **als auch** sofort gemeldet wird.

---

## Schritt 4: Ausgabe überprüfen – was sollten Sie sehen?

Führen Sie das Programm in einer Konsole aus. Wenn `input.docx` eine Schriftart verwendet, die nicht installiert und auch nicht in `C:\SharedFonts` vorhanden ist, sehen Sie etwa Folgendes:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Sind alle Schriftarten verfügbar, erscheint die Warnungszeile einfach nie. Dieser unmittelbare Feedback‑Loop ist in automatisierten Dokumenten‑Verarbeitungspipelines, in denen stille Schriftart‑Ersetzungen Markenrichtlinien brechen könnten, von unschätzbarem Wert.

---

## Schritt 5: Häufige Stolperfallen und Best‑Practice‑Tipps

| Stolperfalle | Wie man sie vermeidet |
|--------------|----------------------|
| **`Aspose.Words.Fonts` nicht referenziert** | Stellen Sie sicher, dass Sie `using Aspose.Words.Fonts;` am Anfang haben; sonst meldet der Compiler fehlende Typen. |
| **Pfad zum Schriftarten‑Ordner ist falsch** | Prüfen Sie den Pfad und setzen Sie `recursive: true`, wenn Unterordner vorhanden sind. Nutzen Sie `Path.GetFullPath` zum Debuggen. |
| **Mehrere Warnungs‑Callbacks** | Aspose.Words honoriert nur den zuletzt zugewiesenen `WarningCallback`. Verwenden Sie einen einzigen Handler, der bei Bedarf delegiert. |
| **Ausführung auf einem Server ohne UI** | Konsolenausgaben sind in Ordnung, aber für Web‑Apps sollten Sie stattdessen in eine Datei oder ein Monitoring‑System loggen statt `Console.WriteLine`. |
| **Große Dokumente verursachen Performance‑Einbußen** | Verwenden Sie eine einzige `FontSettings`‑Instanz für mehrere Ladevorgänge; das wiederholte Erzeugen kann teuer sein. |

**Pro‑Tipp:** Wenn Sie Warnungen für eine spätere Analyse *sammeln* möchten, speichern Sie sie in einer `List<string>` innerhalb des Handlers statt sie direkt auszugeben.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Sie können anschließend `handler.Messages` nach dem Laden des Dokuments inspizieren.

---

## Schritt 6: Lösung erweitern – was, wenn ich eine Ersatzschrift einbetten muss?

Manchmal soll die fehlende Schriftart *in* das resultierende PDF eingebettet werden, damit nachgelagerte Viewer das genaue Aussehen zeigen. Nach dem Laden des Dokuments können Sie das Einbetten erzwingen:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Dieses Snippet zeigt, wie derselbe **Schrifteinstellungen‑Konfigurations‑Ansatz** über das reine Laden hinaus erweitert werden kann.

---

## Vollständiges ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in ein neues Konsolen‑App‑Projekt kopieren‑und‑einfügen können. Es enthält alle oben besprochenen Bausteine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Erwartete Ausgabe** (wenn eine fehlende Schriftart vorhanden ist):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Gibt es keine Ersetzung, erscheinen nur die Erfolgsmeldungen.

---

## Fazit

Wir haben gerade **einen Warnungs‑Callback erstellt**, der zuverlässig **fehlende Schriftarten** beim **Laden eines Word‑Dokuments** mit Aspose.Words erkennt, und gezeigt, wie man **Schrifteinstellungen konfiguriert**, um zu steuern, wo die Bibliothek nach Schriftarten sucht und welcher Fallback verwendet wird. Durch das Verknüpfen von `FontSettings` und `LoadOptions` erhalten Sie volle Transparenz bei Schriftart‑Problemen – keine stillen Layout‑Fehler mehr.

Nächste Schritte? Ersetzen Sie den `FontWarningHandler` durch einen Logger, der in eine Datenbank schreibt, oder experimentieren Sie mit **Schriftart‑Ersetzungsregeln**, um bestimmte fehlende Schriftarten auf markenkonforme Alternativen abzubilden. Sie könnten auch **dynamisches Laden von Schriftarten** aus Cloud‑Speichern testen, wenn Ihre Anwendung in einer containerisierten Umgebung läuft.

Haben Sie Fragen zu einem speziellen Sonderfall – etwa dem Umgang mit OpenType‑Features oder verschlüsselten DOCX‑Dateien? Hinterlassen Sie einen Kommentar unten, und happy coding!  

---

![Warnungs‑Callback erstellen Diagramm](https://example.com/images/create-warning-callback.png "Warnungs‑Callback erstellen Diagramm")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}