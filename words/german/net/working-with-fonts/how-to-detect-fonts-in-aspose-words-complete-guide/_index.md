---
category: general
date: 2026-04-07
description: Erfahren Sie, wie Sie Schriftarten erkennen und Warnungen erfassen können,
  während Sie fehlende Schriftarten in C# mit Aspose.Words behandeln. Schritt‑für‑Schritt‑Code
  ist enthalten.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: de
og_description: Wie erkennt man Schriftarten in Aspose.Words? Folgen Sie diesem Tutorial,
  um Warnungen zu erfassen und fehlende Schriftarten mühelos zu handhaben.
og_title: Wie man Schriftarten in Aspose.Words erkennt – Vollständiger Leitfaden
tags:
- Aspose.Words
- C#
- Font handling
title: Wie man Schriftarten in Aspose.Words erkennt – Komplettanleitung
url: /de/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Schriftarten in Aspose.Words erkennt – Vollständige Anleitung

Haben Sie sich schon einmal gefragt, **wie man Schriftarten** erkennt, die in einem Word‑Dokument fehlen, bevor Sie es in die Produktion geben? Sie sind nicht allein. In vielen Unternehmensszenarien kann eine fehlende Schriftart eine PDF‑Konvertierungspipeline zum Absturz bringen oder Layout‑Fehler verursachen, die unprofessionell wirken. Die gute Nachricht: Aspose.Words bietet Ihnen eine integrierte Möglichkeit, diese fehlenden Schriftarten aufzuspüren und klare Warnungen auszugeben.

In diesem Tutorial zeigen wir Ihnen Schritt für Schritt, **wie man Schriftarten erkennt**, **wie man Warnungen abfängt** und die besten Praktiken, **fehlende Schriftarten zu behandeln**, damit Ihre Anwendung robust bleibt. Keine externen Tools, kein Rätselraten – nur reiner C#‑Code, den Sie sofort in Ihr Projekt einbinden können.

> **Kurzer Überblick:** Am Ende haben Sie einen wiederverwendbaren `FontSubstitutionWarningCollector`, der jede Schriftart‑Ersetzungsnachricht beim Laden eines Dokuments sammelt, und Sie wissen, wie Sie reagieren, wenn eine Schriftart nicht gefunden werden kann.

---

## Was Sie lernen werden

- Wie Sie `LoadOptions` konfigurieren, um auf Schriftart‑Ersetzungs‑Warnungen zu hören.  
- Wie Sie diese Warnungen in einer eigenen Collector‑Klasse abfangen.  
- Wie Sie die gesammelten Warnungen verarbeiten und entscheiden, ob Sie abbrechen, protokollieren oder Schriftarten ersetzen.  
- Sonderfall‑Behandlung für Dokumente, die entfernte oder eingebettete Schriftarten referenzieren.  

**Voraussetzungen:** .NET 6+ (oder .NET Framework 4.6+), Aspose.Words für .NET (neueste Version) und Grundkenntnisse in C#. Wenn Sie Aspose.Words noch nie verwendet haben, keine Sorge – dieser Leitfaden setzt nur wenige Minuten Setup‑Zeit voraus.

---

## Wie man Schriftarten mit Aspose.Words LoadOptions erkennt

Der erste Schritt, um fehlende Schriftarten zu erkennen, besteht darin, Aspose.Words mitzuteilen, dass es diese melden soll. Das geschieht über die Eigenschaft `LoadOptions.WarningCallback`, die jede Klasse akzeptiert, die `IWarningCallback` implementiert. Unten erstellen wir einen kleinen Collector, der jede Warnung für eine spätere Inspektion speichert.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Warum das wichtig ist:** Ohne einen Warn‑Callback ersetzt Aspose.Words fehlende Schriftarten stillschweigend durch eine Standardschrift, und Sie erfahren nie, dass ein Problem besteht. Indem wir `WarningType.FontSubstitution` abfangen, erhalten wir volle Transparenz – genau die Daten, die Sie benötigen, um **Schriftarten zu erkennen**, die auf dem Host‑Computer nicht verfügbar sind.

Jetzt binden wir den Collector in `LoadOptions` ein und laden ein Dokument:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Pro‑Tipp:** Wenn Sie viele Dokumente stapelweise verarbeiten, verwenden Sie dieselbe Instanz von `FontSubstitutionWarningCollector`, vergessen Sie jedoch nicht, zwischen den Ladevorgängen `Clear()` aufzurufen, um Warnungen verschiedener Dateien nicht zu vermischen.

---

## Warnungen beim Laden des Dokuments abfangen

Nachdem das Dokument geladen ist, enthält der Collector bereits jede schriftbezogene Warnung. Die nächste logische Frage lautet: *Wie fange ich Warnungen* ab, sodass sie leicht zu protokollieren oder anzuzeigen sind?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Typische Ausgabe sieht so aus:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Was das Ihnen sagt:** Jede Zeile enthüllt den ursprünglichen Schriftartnamen und die Ausweichschrift, die Aspose.Words gewählt hat. Mit diesen Informationen können Sie entscheiden, ob die Ausweichschrift akzeptabel ist oder ob Sie die fehlende Schriftart manuell einbetten müssen.

---

## Fehlende Schriftarten elegant behandeln

Das Erkennen und Abfangen von Warnungen ist nur die halbe Miete. Der eigentliche Nutzen entsteht, wenn Sie **fehlende Schriftarten** in einer produktionsreifen Weise **behandeln**. Im Folgenden drei gängige Strategien:

1. **Protokollieren und Fortfahren** – Geeignet für Batch‑Verarbeitung, bei der Sie nur ein Prüfprotokoll benötigen.  
2. **Bei kritischen Schriftarten abbrechen** – Werfen Sie eine Ausnahme, wenn eine bestimmte Schriftart (z. B. eine markenspezifische Schrift) fehlt.  
3. **Schriftart on‑the‑fly einbetten** – Laden Sie die fehlende Schrift aus einem bekannten Ordner und registrieren Sie sie bei Aspose.Words, bevor Sie das Dokument erneut laden.

### Beispiel: Bei einer kritischen Schriftart abbrechen

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Beispiel: Fehlende Schriftarten automatisch einbetten

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Warum diese Muster helfen:** Indem Sie explizit festlegen, was bei einer fehlenden Schriftart geschehen soll, vermeiden Sie stille Ersetzungen, die das Branding oder die Lesbarkeit beeinträchtigen könnten. Das ist das Wesentliche von **fehlenden Schriftarten behandeln** in kontrollierter Weise.

---

## Komplettes funktionierendes Beispiel

Alles zusammengeführt, hier ein einzelnes, sofort ausführbares Programm, das **zeigt, wie man Schriftarten erkennt**, **wie man Warnungen abfängt** und eine einfache Richtlinie implementiert, **fehlende Schriftarten zu behandeln**, indem sie protokolliert werden.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Erwartetes Ergebnis:** Wenn Sie das Programm gegen ein Dokument ausführen, das eine nicht vorhandene Schriftart referenziert, listet die Konsole jede Ersetzungs‑Warnung auf. Enthält eine Warnung eine Schrift aus dem `critical`‑Set, beendet das Programm frühzeitig, sodass kein fehlerhaftes PDF erzeugt wird.

---

## Häufig gestellte Fragen (FAQs)

| Frage | Antwort |
|----------|--------|
| *Benötige ich eine Lizenz für Aspose.Words, um diesen Code zu verwenden?* | Ja, eine gültige Aspose.Words‑Lizenz entfernt Evaluations‑Wasserzeichen und schaltet die volle Funktionalität frei. |
| *Kann dieser Ansatz eingebettete Schriftarten erkennen?* | Eingebettete Schriftarten sind bereits Teil der Datei, daher erzeugt Aspose.Words keine Ersetzungs‑Warnung. Sie können `Document.FontInfos` prüfen, um eingebettete Schriftarten bei Bedarf aufzulisten. |
| *Was passiert, wenn die fehlende Schriftart unter Windows ein System‑Font ist, aber unter Linux nicht?* | Unter Linux wird dieselbe Warnung ausgelöst, weil die Schrift dort nicht installiert ist. Verwenden Sie die Strategie „fehlende Schriftarten behandeln“, um die erforderlichen `.ttf`‑Dateien mit Ihrer Anwendung zu liefern. |
| *Ist der Warn‑Collector thread...* |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}