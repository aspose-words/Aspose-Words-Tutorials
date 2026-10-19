---
category: general
date: 2026-06-08
description: Erfahren Sie, wie Sie LoadOptions in Aspose.Words verwenden, um fehlende
  Schriftarten beim Dokumentimport zu erkennen. Schritt‑für‑Schritt‑Anleitung mit
  Code, Erklärungen und bewährten Methoden.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: de
og_description: Wie man LoadOptions in Aspose.Words verwendet und fehlende Schriftarten
  beim Laden eines Dokuments erkennt. Vollständige Anleitung mit Code und praktischen
  Tipps.
og_title: Wie man LoadOptions verwendet, um fehlende Schriftarten zu erkennen
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Wie man LoadOptions verwendet, um fehlende Schriftarten zu erkennen
url: /de/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man LoadOptions verwendet, um fehlende Schriftarten zu erkennen

Haben Sie sich jemals gefragt, **wie man LoadOptions** beim Laden eines Word-Dokuments mit Aspose.Words verwendet? In diesem Tutorial zeigen wir Ihnen genau **wie man LoadOptions** einsetzt, um **fehlende Schriftarten** zu **erkennen** und sie elegant zu behandeln. Egal, ob Sie einen Dokumentkonvertierungsservice oder eine Reporting-Engine bauen, fehlende Schriftarten können Layout‑Überraschungen verursachen, daher ist es ein Muss, sie frühzeitig zu erfassen.

Wir gehen jeden Schritt durch – vom Einbinden eines Warn‑Callbacks bis zur Interpretation der Ergebnisse – sodass Sie am Ende ein vollständig funktionierendes C#‑Beispiel haben, das Sie in jedes .NET‑Projekt einbinden können. Keine externen Dokumente, nur eine eigenständige Lösung. Am Ende wissen Sie, warum das Warnsystem existiert, wie man es aktiviert und was zu tun ist, wenn der Callback ausgelöst wird.

## Voraussetzungen

- **Aspose.Words for .NET** (jede aktuelle Version; die API, die wir verwenden, ist seit 2022 stabil).
- Eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder VS Code mit der C#‑Erweiterung).
- Eine Beispiel‑Word‑Datei (`input.docx`), die eine Schriftart referenziert, die Sie *nicht* auf dem Rechner installiert haben.

Das war's – keine zusätzlichen NuGet‑Pakete außer Aspose.Words.

## Wie man LoadOptions mit Aspose.Words verwendet

Die Klasse **LoadOptions** ist das Tor zur Anpassung der Art und Weise, wie ein Dokument gelesen wird. Indem Sie einen Warn‑Callback einbinden, können Sie **fehlende Schriftarten** sofort erkennen, sobald Aspose.Words die Datei parst. Lassen Sie uns das aufschlüsseln.

### Schritt 1: Einen Warn‑Handler erstellen

Aspose.Words verwendet das Interface `IWarningCallback`, um Sie über nicht kritische Probleme zu informieren, wie z. B. Schriftart‑Ersetzungen. Implementieren Sie das Interface und entscheiden Sie, was bei einer Warnung geschehen soll.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Warum das wichtig ist:**  
Ohne einen Callback tauscht Aspose.Words fehlende Schriftarten stillschweigend gegen eine Standardschriftart aus (in der Regel Arial). Durch das Abfangen der `FontSubstitution`‑Warnung können Sie das Problem protokollieren, den Benutzer benachrichtigen oder sogar die fehlende Schriftart durch eine benutzerdefinierte Alternative ersetzen.

### Schritt 2: Den Handler an LoadOptions anhängen

Jetzt erstellen wir eine Instanz von `LoadOptions` und weisen ihr unseren `FontWarningHandler` zu. Hier kommt **wie man LoadOptions verwendet** wirklich zum Tragen.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Warum das wichtig ist:**  
`LoadOptions` ist ein All‑in‑One‑Ort für viele Import‑Einstellungen (Kodierung, Passwort usw.). Durch das Setzen von `WarningCallback` aktivieren Sie einen leichten, ereignisgesteuerten Mechanismus, der für jedes Dokument funktioniert, das Sie mit diesen Optionen laden.

### Schritt 3: Das Dokument mit den konfigurierten Optionen laden

Schließlich übergeben wir die `LoadOptions` dem `Document`‑Konstruktor. Wenn die Quelldatei eine Schriftart referenziert, die nicht installiert ist, löst Aspose.Words die Warnung aus und Ihr Handler gibt eine Meldung aus.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Was Sie sehen werden:**  
Angenommen, `input.docx` verwendet eine Schriftart namens *„MyCustomFont“*, die nicht auf dem Rechner vorhanden ist, dann sieht die Konsolenausgabe folgendermaßen aus:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Wenn alle Schriftarten vorhanden sind, bleibt der Callback still – keine Ausgabe, keine Leistungseinbußen.

## Fehlende Schriftarten mit einem Warn‑Callback erkennen (Sekundäres Schlüsselwort in Aktion)

Der Ausdruck **detect missing fonts** erscheint natürlich in der obigen Überschrift und verstärkt das sekundäre Schlüsselwort. Lassen Sie uns einige Varianten untersuchen, denen Sie in realen Projekten begegnen könnten.

### Mehrere Dokumente in einer Schleife

Oft verarbeiten Sie einen Stapel von Dateien. Die gleiche `LoadOptions`‑Instanz kann wiederverwendet werden, aber denken Sie daran, dass der `WarningCallback` über mehrere Ladevorgänge hinweg bestehen bleibt. Wenn Sie eine Isolation pro Dokument benötigen, erstellen Sie für jede Iteration eine neue `LoadOptions`‑Instanz.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Benutzerdefinierte Schriftart‑Ersetzungslogik

Anstatt nur zu protokollieren, möchten Sie vielleicht eine bestimmte fehlende Schriftart durch eine unternehmens‑genehmigte Alternative ersetzen. Erweitern Sie den Handler:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Jetzt erkennen Sie nicht nur **fehlende Schriftarten**, sondern entscheiden auch, wie Sie sie ersetzen.

### Unerwünschte Warnungen unterdrücken

Wenn Sie nur an Schriftart‑Problemen interessiert sind und alles andere unterdrücken möchten, filtern Sie nach `WarningType` wie gezeigt. Um hingegen *alle* Warnungen zu protokollieren, entfernen Sie die `if`‑Prüfung und geben Sie `info.WarningType` zusammen mit `info.Description` aus.

## Vollständiges, ausführbares Beispiel

Wenn wir alles zusammenfügen, erhalten Sie ein komplettes Programm, das Sie kompilieren und ausführen können. Ersetzen Sie `"YOUR_DIRECTORY/input.docx"` durch den Pfad zu Ihrer Testdatei.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Erwartete Konsolenausgabe (wenn eine Schriftart fehlt):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Wenn keine Schriftarten fehlen, sehen Sie einfach:

```
Document loaded successfully.
```

## Häufige Fallstricke & Pro‑Tipps

- **Fallstrick:** Vergessen, `WarningCallback` zu setzen. Die API wird weiterhin Schriftarten ersetzen, aber Sie werden nie erfahren, dass es passiert ist.  
  **Pro‑Tipp:** Hängen Sie immer einen Handler an, wenn Sie Schriftart‑Treue benötigen; es kostet praktisch nichts.

- **Fallstrick:** 

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Schriftarten in Aspose.Words erkennt – Warnungen & Einstellungen behandeln](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Wie man Schriftarten in Aspose.Words erfasst – Vollständiger Leitfaden](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Wie man DOCX lädt und fehlende Schriftarten erkennt – Vollständiger C#‑Leitfaden](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}