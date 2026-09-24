---
category: general
date: 2026-02-18
description: Erfahren Sie, wie Sie Schriftartwarnungen erfassen und fehlende Schriftarten
  in C# mit Aspose.Words erkennen. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung,
  um fehlende Schriftarten effizient zu handhaben.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: de
og_description: Erfassen Sie Schriftartwarnungen in C# und lernen Sie, fehlende Schriftarten
  zu erkennen, fehlende Schriftarten zu behandeln und fehlende Schriftarten aufzulisten
  – mit einem vollständigen Codebeispiel.
og_title: Font-Warnungen in C# erfassen – Komplettanleitung
tags:
- Aspose.Words
- C#
- Font Management
title: Schriftart‑Warnungen in C# erfassen – Vollständiger Programmierleitfaden
url: /de/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schriftartwarnungen in C# erfassen – Vollständiger Programmierleitfaden

Haben Sie sich schon einmal gefragt, wie man **Schriftartwarnungen** erfasst, wenn ein Dokument eine Schriftart referenziert, die nicht auf dem Server installiert ist? Sie sind nicht allein. In vielen Unternehmens‑Apps führen fehlende Schriftarten zu Layout‑Fehlern, und der zuverlässigste Weg, sie zu entdecken, besteht darin, die Warnungen der Bibliothek abzufangen.  

In diesem Tutorial zeigen wir Ihnen eine sofort einsatzbereite Lösung, die nicht nur **Schriftartwarnungen erfasst**, sondern auch **fehlende Schriftarten erkennt**, **fehlende Schriftarten verarbeitet** und sogar **fehlende Schriftarten auflistet**, sodass Sie entscheiden können, ob Sie ersetzen, einbetten oder den Benutzer benachrichtigen möchten. Keine externe Dokumentation nötig – einfach kopieren, einfügen und ausführen.

## Was Sie lernen werden

- Wie Sie `LoadOptions` konfigurieren, um Warnungen bei Schriftart‑Substitution zu aktivieren.  
- Den genauen Code, den Sie benötigen, um ein DOCX zu laden und jede Warnung herauszuholen.  
- Warum jeder Schritt wichtig ist, einschließlich Leistungsaspekten.  
- Umgang mit Sonderfällen wie Dokumenten mit gemischten Skript‑Schriftarten oder benutzerdefinierten Schriftordnern.  

**Voraussetzungen**: .NET 6+ (oder .NET Framework 4.6+), ein Verweis auf das **Aspose.Words** NuGet‑Paket und Grundkenntnisse in C#. Wenn Sie Aspose.Words noch nie verwendet haben, keine Sorge – dieser Leitfaden führt Sie durch jedes Detail.

![Diagramm zur Erfassung von Schriftartwarnungen](image.png){alt="Diagramm zur Erfassung von Schriftartwarnungen"}

## Schriftartwarnungen erfassen – Warum das wichtig ist

Wenn Aspose.Words ein Dokument lädt, ersetzt es stillschweigend jede nicht verfügbare Schriftart durch eine Ersatzschrift. Diese Ersatzschrift hält den Ladevorgang am Leben, aber das visuelle Ergebnis kann völlig verzerrt sein. Durch Aktivieren des Flags **SubstitutionWarningLevel.All** fügt die Bibliothek für jede fehlende Schriftart einen `WarningInfo`‑Eintrag hinzu, sodass Sie **fehlende Schriftarten** erkennen können, bevor das Dokument gerendert oder gespeichert wird.

> **Pro‑Tipp:** Wenn Sie Hunderte von Dateien in einem Batch‑Job verarbeiten, kann das Protokollieren dieser Warnungen in einem zentralen Speicher Ihnen später Stunden manueller QA ersparen.

## Schritt 1: Projekt einrichten

1. Öffnen Sie Ihre bevorzugte IDE (Visual Studio, Rider, VS Code).  
2. Erstellen Sie ein neues Konsolenprojekt:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Fügen Sie das Aspose.Words‑Paket hinzu:

```bash
dotnet add package Aspose.Words
```

Das war’s – keine zusätzlichen DLLs, kein COM‑Interop. Die Bibliothek liefert alles, was Sie benötigen, um **fehlende Schriftarten zu verarbeiten**.

## Schritt 2: Load‑Optionen vorbereiten, um alle Schriftart‑Substitutionswarnungen zu erfassen

Damit die Engine **Schriftartwarnungen erfasst**, müssen Sie ihr mitteilen, jede Substitution zu protokollieren. Das folgende Snippet erstellt eine `LoadOptions`‑Instanz, aktiviert das Warnungslevel und (optional) weist die Engine auf einen Ordner mit benutzerdefinierten Schriftarten, die Sie verwenden möchten, hin.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Warum das wichtig ist:**  
- `SubstitutionWarningLevel.All` stellt sicher, dass **jede** fehlende‑Schrift‑Ereignis aufgezeichnet wird, nicht nur das erste.  
- Ohne dieses Flag ersetzt Aspose.Words die Schriftart stillschweigend und Sie erfahren nie, dass ein Problem besteht.

## Schritt 3: Dokument mit den konfigurierten Optionen laden

Jetzt öffnen wir die Datei. Ersetzen Sie `DocumentWithMissingFonts.docx` durch den Pfad zu Ihrem Testdokument.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Falls die Datei Verweise auf Schriftarten enthält, die nicht auf dem Rechner (oder im optionalen Ordner) vorhanden sind, wird die `document.WarningInfoCollection` gefüllt.

## Schritt 4: Schriftart‑Substitutionswarnungen finden und anzeigen

Hier kommt der Kern des Tutorials: Durchlaufen der `WarningInfoCollection`, um **fehlende Schriftarten aufzulisten**. Wir filtern nach `WarningType.FontSubstitution` und geben eine benutzerfreundliche Meldung aus.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Erwartete Ausgabe

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Wenn das Dokument nur installierte Schriftarten verwendet, sehen Sie die Zeile „✅ Keine fehlenden Schriftarten erkannt“.

## Schritt 5: Fortgeschritten – Wie man **fehlende Schriftarten** programmgesteuert **verarbeitet**

Einfach nur eine Liste auszugeben reicht vielleicht für ein Diagnose‑Tool, aber viele Produktionssysteme müssen **fehlende Schriftarten** automatisch **verarbeiten**. Im Folgenden zwei gängige Strategien:

### 5.1 Mit einer bekannten Ersatzschrift substituieren

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Eine benutzerdefinierte Schriftart zur Laufzeit einbetten

Wenn Sie eine Unternehmensschriftartdatei (`MyBrand.ttf`) besitzen, können Sie diese einbetten, sobald eine fehlende Schriftart erkannt wird:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Hinweis:** Das Einbetten von Schriftarten kann die Dateigröße erhöhen, also wägen Sie den Kompromiss zwischen Treue und Bandbreite ab.

## Häufige Stolperfallen und wie man sie vermeidet

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Keine Warnungen erscheinen, obwohl das Dokument falsch aussieht | `SubstitutionWarningLevel` nicht auf `All` gesetzt | Stellen Sie sicher, dass Schritt 2 das Flag exakt wie gezeigt setzt |
| Warnungen listen dieselbe Schriftart mehrfach auf | Dokument enthält die Schriftart in mehreren Stilen | Deduplizieren, falls Sie nur eine eindeutige Liste benötigen: `fontWarnings.Select(w => w.Description).Distinct()` |
| Anwendung stürzt bei großen DOCX‑Dateien ab | Laden mit Standard‑Speichereinstellungen | Verwenden Sie `LoadOptions.LoadFormat` oder streamen Sie die Datei, um den Speicherverbrauch zu reduzieren |

## Vollständiges funktionierendes Beispiel (Copy‑Paste‑bereit)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Führen Sie das Programm mit `dotnet run` aus. Sie sollten die Liste der fehlenden Schriftarten in der Konsole sehen, was bestätigt, dass Sie **Schriftartwarnungen erfolgreich erfasst** haben.

## Fazit

Sie verfügen nun über ein komplettes, produktionsreifes Muster, um **Schriftartwarnungen zu erfassen**, **fehlende Schriftarten zu erkennen**, **fehlende Schriftarten zu verarbeiten** und **fehlende Schriftarten aufzulisten** – mit Aspose.Words in C#. Der Ansatz ist leichtgewichtig, erfordert nur wenige Code‑Zeilen und lässt sich in jede bestehende Pipeline einbinden – egal ob Sie

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}