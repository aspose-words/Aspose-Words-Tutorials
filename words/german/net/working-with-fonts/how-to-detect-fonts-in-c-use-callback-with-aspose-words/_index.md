---
category: general
date: 2026-03-17
description: Wie man Schriftarten in C# mit Aspose.Words und einem Warn‑Callback erkennt.
  Erfahren Sie, wie Sie den Callback verwenden, um fehlende Schriftart‑Ersetzungen
  beim Laden von Dokumenten zu erfassen.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: de
og_description: Wie man Schriftarten in C# mit Aspose.Words erkennt. Dieser Leitfaden
  zeigt, wie man einen Callback verwendet, um fehlende Schriftart‑Warnungen beim Laden
  eines Dokuments zu erfassen.
og_title: Wie man Schriftarten in C# erkennt – Callback mit Aspose.Words nutzen
tags:
- Aspose.Words
- C#
- Document Processing
title: Wie man Schriftarten in C# erkennt – Callback mit Aspose.Words verwenden
url: /de/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Schriftarten in C# erkennt – Callback mit Aspose.Words verwenden

Haben Sie schon einmal **wie man Schriftarten erkennt** in einem Word‑Dokument programmatisch benötigt und sich gefragt, warum nach einer Konvertierung einige Zeichen seltsam aussehen? Sie sind nicht allein. In vielen realen Projekten – Rechnungs‑Generatoren, Berichtsexporter oder Batch‑Verarbeitungspipelines – fehlen Schriftarten und verursachen stille Layout‑Fehler, die schwer zu debuggen sind.  

Die gute Nachricht? Aspose.Words bietet Ihnen eine saubere Möglichkeit, diese Probleme über einen Warn‑Callback sichtbar zu machen. In diesem Tutorial sehen Sie **wie man einen Callback verwendet**, um jede Schriftart‑Substitution, die Aspose beim Laden eines Dokuments vornimmt, aufzuzeichnen, und Sie erhalten ein sofort einsatzbereites Beispiel, das einen klaren Bericht über fehlende Schriftarten ausgibt.

Wir behandeln:

* Die minimalen Voraussetzungen (ein .NET‑Projekt und das Aspose.Words‑NuGet‑Paket).  
* Wie man `IWarningCallback` implementiert, um `WarningType.FontSubstitution` zu lauschen.  
* Wie man den Callback in `LoadOptions` einbindet und ein Dokument lädt.  
* Wie die Ausgabe aussieht, plus ein paar praktische Tipps für Produktionscode.

Am Ende können Sie **Schriftarten automatisch erkennen** in jeder DOCX-, DOC‑ oder RTF‑Datei und auf fehlende Schriftart‑Informationen reagieren – sei es durch Protokollierung, Benachrichtigung des Benutzers oder das Ersetzen durch eine Ersatzschriftart.

---

![Wie man Schriftarten in einem Word‑Dokument mit Aspose.Words Warn‑Callback erkennt](https://example.com/images/detect-fonts.png "wie man Schriftarten in einem Word‑Dokument erkennt")

## Was Sie benötigen

* **.NET 6.0** oder höher (das Beispiel kompiliert auch mit .NET Framework 4.6+).  
* **Aspose.Words für .NET** – Installation via NuGet: `Install-Package Aspose.Words`.  
* Eine Beispiel‑Word‑Datei, die bewusst eine Schriftart referenziert, die nicht installiert ist (z. B. `MissingFont.docx`).  

Keine zusätzlichen Bibliotheken sind nötig; alles befindet sich im Aspose‑Namespace.

---

## Wie man Schriftarten mit einem Warn‑Callback erkennt

### Schritt 1: Eine Warn‑Callback‑Klasse erstellen

Der Callback implementiert `IWarningCallback`. Wenn Aspose.Words eine Schriftart nicht finden kann, löst es ein `WarningInfo` mit `WarningType.FontSubstitution` aus. Unsere Klasse schreibt einfach eine freundliche Zeile in die Konsole.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Warum das wichtig ist:** Durch das Filtern nach `WarningType.FontSubstitution` vermeiden wir laute Warnungen (wie veraltete Features) und halten das Protokoll fokussiert auf das eigentliche Problem – **Schriftarten erkennen**, die nicht auf dem Rechner vorhanden sind.

---

### Schritt 2: Den Callback in `LoadOptions` einbinden

`LoadOptions` ermöglicht es, das Parsen eines Dokuments anzupassen. Durch Zuweisen unseres `FontWarningCollector` zur Eigenschaft `WarningCallback` teilt Aspose mit, dass der Callback bei jeder fehlenden Schriftart aufgerufen werden soll.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tipp:** Hier können Sie auch `LoadOptions.FontSettings` setzen, wenn Sie programmgesteuert eine Ersatzschriftart bereitstellen wollen. Das ist ein fortgeschrittenes Szenario, das wir später erwähnen.

---

### Schritt 3: Das Dokument laden und die Ausgabe beobachten

Jetzt laden wir die Datei. Sobald Aspose das Dokument parst, löst jede nicht auffindbare Schriftart unseren Callback aus.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Erwartete Konsolenausgabe** (angenommen, das Dokument referenziert *Comic Sans MS*, das nicht installiert ist):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Enthält das Dokument mehrere fehlende Schriftarten, sehen Sie eine Zeile pro Schriftart – genau die **wie man Schriftarten erkennt**‑Information, die Sie benötigen.

---

## Wie man den Callback für komplexere Szenarien nutzt

### Protokollierung in eine Datei statt in die Konsole

In der Produktion wollen Sie wahrscheinlich ein dauerhaftes Log. Ersetzen Sie `Console.WriteLine` durch einen `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Warnungen für spätere Analyse sammeln

Manchmal benötigen Sie die Liste fehlender Schriftarten nach dem Laden des Dokuments, etwa um einen UI‑Dialog anzuzeigen. Speichern Sie die Warnungen in einer `List<string>` und stellen Sie sie bereit:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Programmgesteuerte Bereitstellung einer Ersatzschriftart

Wenn Sie eine Unternehmensschriftart erzwingen wollen, können Sie sie vor dem Laden zu `FontSettings` hinzufügen:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Jetzt ersetzt Aspose fehlende Schriftarten durch *Arial Unicode MS*, während es die Substitution weiterhin über den Callback meldet. Das ist ein eleganter Weg, **wie man einen Callback verwendet** sowohl zur Erkennung als auch zur automatischen Behebung.

---

## Häufige Fallstricke und Profi‑Tipps

| Fallstrick | Warum er auftritt | Wie man ihn vermeidet |
|------------|-------------------|-----------------------|
| **Vergessen, `Aspose.Words.Warnings` zu referenzieren** | Das Interface `IWarningCallback` befindet sich dort. | `using Aspose.Words.Warnings;` am Anfang hinzufügen. |
| **Laden eines Dokuments ohne `LoadOptions`** | Der Standard‑Lader ersetzt Schriftarten stillschweigend ohne Benachrichtigung. | Immer eine `LoadOptions`‑Instanz erstellen und den Callback zuweisen. |
| **Ausführen auf einem Server mit eingeschränkten Berechtigungen** | Schreiben in eine Log‑Datei kann `UnauthorizedAccessException` auslösen. | Einen beschreibbaren Ordner verwenden (z. B. das Anwendungsverzeichnis) oder nur In‑Memory‑Sammlungen nutzen. |
| **Mehrere Threads teilen denselben Collector** | `FontWarningCollector` ist standardmäßig nicht thread‑sicher. | Pro Thread einen eigenen Collector erstellen oder die Liste mit einem Lock schützen. |
| **Annahme, dass der Callback bei eingebetteten Schriftarten feuert** | Eingebettete Schriftarten sind bereits im Dokument enthalten; es wird keine Warnung erzeugt. | Wenn Sie die Integrität eingebetteter Schriftarten prüfen wollen, `FontInfo` über `FontSettings` inspizieren. |

---

## Vollständiges, lauffähiges Beispiel (Copy‑Paste‑bereit)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Was Sie sehen sollten** (angenommen, die Datei referenziert zwei fehlende Schriftarten):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Verwendet die Datei nur installierte Schriftarten, gibt die Konsole lediglich aus:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Fazit

Wir haben gezeigt, **wie man Schriftarten erkennt** in einem Word‑Dokument, indem wir einen benutzerdefinierten Warn‑Callback in Aspose.Words einbinden. Der Ansatz ist leichtgewichtig, erfordert

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}