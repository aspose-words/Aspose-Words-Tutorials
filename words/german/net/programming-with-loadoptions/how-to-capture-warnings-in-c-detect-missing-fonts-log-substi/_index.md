---
category: general
date: 2026-04-04
description: Erfahren Sie, wie Sie Warnungen erfassen, fehlende Schriftarten erkennen
  und Substitutionsereignisse mit Aspose.Words LoadOptions in C# protokollieren.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: de
og_description: Wie man Warnungen erfasst, fehlende Schriftarten erkennt und Substitutionsereignisse
  mit Aspose.Words LoadOptions in C# protokolliert.
og_title: Wie man Warnungen in C# erfasst – Fehlende Schriftarten erkennen & Substitution
  protokollieren
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Wie man Warnungen in C# erfasst – fehlende Schriftarten erkennen und Substitution
  protokollieren
url: /de/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen in C# erfasst – Fehlende Schriftarten erkennen & Substitution protokollieren

Haben Sie sich jemals gefragt **wie man Warnungen** erfasst, die beim Laden eines Word‑Dokuments mit fehlenden Schriftarten auftreten? Sie sind nicht allein. In vielen realen Projekten gehen Schriftarten bei Migrationen verloren, und das stille Ausweichverhalten kann Ihr Layout zerstören. Die gute Nachricht? Aspose.Words bietet Ihnen eine saubere Möglichkeit, diese Warnungen zu überwachen, fehlende Schriftarten zu erkennen und sogar jede Substitution zu protokollieren, damit Sie die Quelle später beheben können.

In diesem Tutorial führen wir Sie durch eine vollständige, sofort ausführbare Lösung, die **zeigt, wie man Warnungen erfasst**, **fehlende Schriftarten erkennt** und erklärt, **wie man Substitutions‑Ereignisse protokolliert**. Am Ende haben Sie einen wiederverwendbaren Warnungs‑Handler, ein vollständig konfiguriertes `LoadOptions`‑Objekt und ein Beispiel‑Konsolenausgabe, die Sie überprüfen können.

> **Voraussetzung:** Sie benötigen Aspose.Words für .NET (v24.x oder neuer), installiert über NuGet, sowie eine grundlegende C#‑Entwicklungsumgebung (Visual Studio 2022 oder VS Code funktionieren einwandfrei).

---

## Wie man Warnungen beim Laden von Dokumenten erfasst

Der Kern der Lösung ist eine Klasse, die `IWarningCallback` implementiert. Aspose.Words ruft diesen Callback automatisch für jede während des Dokumenten‑Ladevorgangs erzeugte Warnung auf, einschließlich Warnungen zur Schriftart‑Substitution.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Warum dieser Schritt?**  
> Durch das Filtern nach `WarningType.FontSubstitution` vermeiden wir Unordnung durch nicht relevante Warnungen (wie veraltete Funktionen). Dadurch konzentriert sich das Protokoll auf das genaue Problem, das Sie interessiert – fehlende Schriftarten.

---

## Fehlende Schriftarten mit Aspose.Words erkennen

Wenn ein Dokument eine Schriftart referenziert, die auf dem Rechner nicht installiert ist, ersetzt Aspose.Words die nächstgelegene passende Schriftart und gibt eine Warnung aus. Unser oben genannter Handler fängt jedes Vorkommen ab und **erkennt fehlende Schriftarten** effektiv.

Um dies in Aktion zu sehen, müssen wir `LoadOptions` konfigurieren und den Handler anhängen:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tipp:** Wenn Sie Warnungen lieber für die spätere Verarbeitung sammeln möchten (z. B. in eine Datei schreiben), ersetzen Sie `Console.WriteLine` durch Code, der die Meldung zu einer `List<string>` hinzufügt.

---

## Wie man Substitutions‑Ereignisse protokolliert

Das Protokollieren ist so einfach wie das Weiterleiten der Warnungs‑Ausgabe in einen persistenten Speicher. Unten finden Sie ein kurzes Beispiel, das jede Substitutions‑Warnung in eine Textdatei namens `font-warnings.log` schreibt.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Warum in eine Datei protokollieren?**  
> Persistente Protokolle ermöglichen es Ihnen, Schriftarten‑Probleme über mehrere Durchläufe hinweg zu prüfen, Alarme zu automatisieren oder die Daten in eine Build‑Pipeline‑Prüfung einzuspeisen.

---

## Vollständiges funktionierendes Beispiel

Wenn wir alles zusammenfügen, erhalten Sie eine eigenständige Konsolenanwendung, die Sie kopieren, einfügen und ausführen können. Sie demonstriert **wie man Warnungen erfasst**, **fehlende Schriftarten erkennt** und **wie man Substitutionen protokolliert** in einem Schritt.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Erwartete Konsolenausgabe

Wenn `input.docx` eine Schriftart referenziert, die nicht installiert ist, sehen Sie etwa Folgendes:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Wenn Sie zu `FileLoggingWarningHandler` wechseln, erscheinen dieselben Zeilen mit Zeitstempeln in `font-warnings.log`.

![how to capture warnings console output](image-placeholder.png)

---

## Häufige Fragen & Sonderfälle

### Was, wenn ich *alle* Warnungen erfassen muss, nicht nur die zur Schriftart‑Substitution?

Entfernen Sie einfach die Prüfung `if (info.Type == WarningType.FontSubstitution)`. Der Callback erhält dann jede Warnungsart (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent` usw.). Sie können anschließend anhand von `info.Type` unterschiedliche Fälle behandeln.

### Funktioniert das mit PDFs oder nur mit Word‑Dokumenten?

`LoadOptions` und `IWarningCallback` gehören zu Aspose.Words, daher gelten sie für Word‑kompatible Formate (`.docx`, `.doc`, `.rtf`, `.html`). Für PDFs würden Sie die eigenen Warnmechanismen von Aspose.PDF verwenden.

### Wie kann ich Warnungen unterdrücken, anstatt sie zu protokollieren?

Setzen Sie `LoadOptions.WarningCallback = null` oder implementieren Sie den Callback, lassen Sie jedoch den Methodenrumpf leer. Die Bibliothek führt die Substitution weiterhin still durch.

### Was ist mit Thread‑Sicherheit?

Die Callback‑Instanz wird im selben Thread aufgerufen, der das Dokument lädt, sodass Sie keine zusätzliche Synchronisation benötigen, es sei denn, Sie teilen den Handler über parallele Ladevorgänge hinweg. In diesem Fall schützen Sie gemeinsam genutzte Ressourcen (z. B. die Protokolldatei) mit einem Lock oder verwenden Sie Concurrent‑Collections.

---

## Fazit

Wir haben **wie man Warnungen** von Aspose.Words erfasst, Ihnen gezeigt, **wie man fehlende Schriftarten erkennt**, und erklärt, **wie man Substitutions‑Ereignisse** für die spätere Analyse protokolliert. Durch das Einbinden einer einfachen `IWarningCallback`‑Implementierung in `LoadOptions` erhalten Sie vollständige Transparenz über Schriftarten‑Probleme, ohne Ihren Code zu überladen.

Nächste Schritte? Versuchen Sie, den Logger zu erweitern, um E‑Mails zu senden, mit Azure Monitor zu integrieren oder fehlende Schriftarten automatisch auf einem Build‑Server zu installieren. Sie können auch andere Warnungsarten erkunden – `WarningType.DegradedDocument` kann Sie auf Funktionen aufmerksam machen, die den Konvertierungsprozess nicht überstanden haben.

Haben Sie weitere Fragen zur Schriftarten‑Verarbeitung oder zu Aspose.Words im Allgemeinen? Hinterlassen Sie einen Kommentar oder eröffnen Sie ein neues Thema im Aspose‑Forum. Viel Spaß beim Coden und möge Ihr Dokument stets mit der richtigen Schriftart dargestellt werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}