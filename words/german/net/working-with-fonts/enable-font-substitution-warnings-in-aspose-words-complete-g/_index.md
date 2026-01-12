---
category: general
date: 2026-01-11
description: Aktivieren Sie Warnungen für die Schriftart‑Substitution, um fehlende
  Schriftarten in Ihren .NET‑Dokumenten zu erkennen. Erfahren Sie, wie Sie den Namen
  fehlender Schriftarten abrufen und fehlende Schriftarten mit Aspose.Words auflisten
  können.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: de
og_description: Aktivieren Sie Schriftart‑Substitutionswarnungen in Aspose.Words,
  um fehlende Schriftarten zu erkennen, den Namen fehlender Schriftarten zu erhalten
  und fehlende Schriftarten in Ihren Dokumenten aufzulisten.
og_title: Warnungen bei Schriftart‑Ersetzungen aktivieren – Schritt‑für‑Schritt C#‑Tutorial
tags:
- Aspose.Words
- C#
- Document Processing
title: Aktivieren von Warnungen für Schriftart-Substitution in Aspose.Words – Vollständige
  Anleitung
url: /de/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schriftarten‑Ersetzungswarnungen aktivieren – Komplett‑Leitfaden

Haben Sie sich schon einmal gefragt, warum ein Word‑Dokument nach dem Hochladen auf einen Server leicht anders aussieht? Wahrscheinlich verwendet der ursprüngliche Autor eine Schriftart, die auf Ihrer Maschine nicht verfügbar ist, und Aspose.Words hat sie stillschweigend durch die am besten passende ersetzt. **Aktivieren Sie die Warnungen für Schriftarten‑Ersetzungen** und Sie erfahren sofort, welche Schriftarten fehlen, womit sie ersetzt wurden und wie Sie auf diese Informationen reagieren können.

In diesem Tutorial führen wir Sie durch ein praktisches End‑to‑End‑Beispiel, das zeigt, wie Sie **fehlende Schriftarten erkennen**, den **Namen der fehlenden Schriftart abrufen** und sogar **fehlende Schriftarten auflisten** können – ganz ohne Schnickschnack, nur mit einer klaren Lösung, die Sie noch heute in jedes .NET‑Projekt einbinden können.

---

## Was Sie lernen werden

- Wie Sie `LoadOptions` so konfigurieren, dass Aspose.Words detaillierte Warnungen ausgibt.
- Den genauen Code, der ein Dokument lädt und schriftartenbezogene Warnungen enumeriert.
- Methoden, um den Namen der fehlenden Schriftart und deren Ersatz zu extrahieren und einen übersichtlichen Bericht zu erzeugen.
- Tipps zum Umgang mit Sonderfällen, etwa Dokumenten mit Dutzenden fehlender Schriftarten oder benutzerdefinierten Schriftordnern.

### Voraussetzungen

- .NET 6+ (der Code funktioniert auch mit .NET Framework 4.7+)
- Aspose.Words für .NET 23.10 oder neuer (über NuGet erhältlich)
- Eine Beispiel‑DOCX, die eine Schriftart referenziert, die Sie nicht installiert haben (wir nennen sie `MissingFont.docx`)

Wenn Sie diese Grundlagen haben, legen wir los.

---

## Schritt 1: LoadOptions einrichten, um Warnungen für Schriftarten‑Ersetzungen zu aktivieren  

Der erste Schritt besteht darin, Aspose.Words mitzuteilen, dass Ihnen fehlende Schriftarten wichtig sind. Standardmäßig protokolliert die Bibliothek Warnungen nur intern. Setzen Sie `SubstitutionWarningLevel` auf `Typical` (oder `All` für die ausführlichste Ausgabe), um den Schalter umzulegen.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Warum das wichtig ist:**  
Wenn `SubstitutionWarningLevel` gesetzt ist, fügt Aspose.Words jedes Mal, wenn es eine referenzierte Schriftart nicht finden kann, ein `FontSubstitutionWarning` zur `Warnings`‑Sammlung des Dokuments hinzu. Diese Sammlung ist der einzige zuverlässige Weg, **fehlende Schriftarten zu erkennen**, ohne das Dokument manuell zu parsen.

> **Pro‑Tipp:** Wenn Sie eine Stapelverarbeitung von Dokumenten durchführen und absolut sicher gehen wollen, dass Sie jede Ersetzung erfassen, verwenden Sie `FontSubstitutionWarningLevel.All`. Das erzeugt zwar mehr Rauschen, garantiert aber, dass keine Warnung übersehen wird.

---

## Schritt 2: Dokument mit den konfigurierten Optionen laden  

Jetzt, wo das Warnsystem bereit ist, laden Sie Ihre DOCX mit den zuvor vorbereiteten `LoadOptions`. Der Pfad kann absolut oder relativ sein; stellen Sie nur sicher, dass die Datei existiert.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Was im Hintergrund passiert:**  
Aspose.Words analysiert das XML des Dokuments, löst jedes `<w:font>`‑Element auf und prüft den System‑Schriftkatalog (plus etwaige benutzerdefinierte Ordner, die Sie `FontSettings` hinzugefügt haben). Wenn eine Schriftart nicht gefunden wird, wird eine Warnung aufgezeichnet – genau das, was wir später benötigen, um **fehlende Schriftarten aufzulisten**.

---

## Schritt 3: Warnungen durchlaufen und Details zu fehlenden Schriftarten extrahieren  

Nachdem das Dokument im Speicher ist, enthält die `Warnings`‑Sammlung jedes `FontSubstitutionWarning`. Wir iterieren darüber, filtern nach dem richtigen Typ und geben einen benutzerfreundlichen Bericht aus.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Erwartete Ausgabe** (angenommen, das Quell‑Dokument referenziert `MyCustomFont`, das nicht installiert ist):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Beachten Sie, dass jeder Eintrag sowohl den **Namen der fehlenden Schriftart** (`MyCustomFont`) als auch den Ersatz (`Arial`) liefert. Genau diese Informationen benötigen Sie, um zu entscheiden, ob Sie die Originalschriftart einbetten, den Autor um einen Ersatz bitten oder die Ersetzung einfach akzeptieren.

---

## Schritt 4: Optional – Daten in einer Liste für weitere Verarbeitung sammeln  

Wenn Sie den Bericht in CSV exportieren, über eine API senden oder einfach im Speicher für später behalten möchten, können Sie die Warnungen in einer stark typisierten Liste ablegen.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Jetzt haben Sie **fehlende Schriftarten aufgelistet** in einem Format, das jedes nachgelagerte System verarbeiten kann. Ob Sie ein Dashboard füttern oder ein Audit‑Log erzeugen – die Daten stehen bereit.

---

## Schritt 5: Sonderfälle und häufige Stolperfallen behandeln  

### Mehrere fehlende Schriftarten in einem Durchlauf  

Große Unternehmens‑Templates referenzieren oft Dutzende benutzerdefinierte Schriftarten. Die Warnsammlung kann dadurch umfangreich werden, aber das oben gezeigte Iterationsmuster skaliert linear, sodass die Performance kein Problem darstellt. Denken Sie nur daran, die Ausgabe lesbar zu halten – eine Gruppierung nach Seite oder Stil kann hilfreich sein, wenn Sie tiefergehende Analysen benötigen.

### Benutzerdefinierte Schriftordner  

Wenn Sie Schriftarten in einem nicht‑standardmäßigen Verzeichnis (z. B. einem gemeinsamen Netzwerk‑Share) ablegen, teilen Sie Aspose.Words mit, wo es suchen soll:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Dieses *vor* dem Laden des Dokuments zu setzen gibt der Bibliothek die Chance, die Schriftarten zu finden, wodurch einige Warnungen komplett entfallen können.

### Bestimmte Warnungen unterdrücken  

Manchmal ist eine bestimmte Ersetzung akzeptabel (z. B. eine dekorative Schrift, die Sie gerne ersetzen). Diese können Sie nachträglich herausfiltern:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Versionskompatibilität  

Der `FontSubstitutionWarningLevel`‑Enum ist seit Aspose.Words 20.12 stabil. Wenn Sie eine ältere Version verwenden, müssen Sie möglicherweise ein Upgrade durchführen, um die Warn‑Level‑Funktion nutzen zu können.

---

## Vollständiges Beispiel  

Unten finden Sie das komplette, sofort ausführbare Programm, das alle oben genannten Schritte integriert. Kopieren Sie es in ein neues Konsolen‑Projekt, fügen Sie das Aspose.Words‑NuGet‑Paket hinzu und setzen Sie `docPath` auf ein Dokument, das eine fehlende Schriftart referenziert.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Durch das Ausführen dieses Programms **aktivieren Sie die Warnungen für Schriftarten‑Ersetzungen**, **erkennen fehlende Schriftarten**, **holen den Namen der fehlenden Schriftart** und **listen fehlende Schriftarten** sowohl in der Konsole als auch in einer CSV‑Datei auf.

---

## Fazit  

Wir haben alles behandelt, was Sie benötigen, um **Warnungen für Schriftarten‑Ersetzungen** in Aspose.Words zu aktivieren – von der ersten Konfiguration bis hin zur Extraktion einer sauberen Liste fehlender Schriftarten. Wenn Sie den obigen Schritten folgen, können Sie Ihre Dokumente prüfen, visuelle Konsistenz sicherstellen und unangenehme Überraschungen beim Rendern auf einem Server vermeiden.

Als nächstes könnten Sie folgendes erkunden:

- **Fehlende Schriftarten direkt in das Ausgabe‑PDF oder DOCX einbetten** (verwenden Sie `FontSettings.EmbeddedFonts`).
- **Automatisches Installieren von Schriftarten** auf Build‑Agents basierend auf dem generierten Bericht.
- **Integration in CI‑Pipelines**, um Builds fehlschlagen zu lassen, wenn kritische Schriftarten fehlen.

Probieren Sie das aus, und Sie verwandeln ein einfaches Warnsystem in einen vollwertigen Schrift‑Management‑Workflow.

Viel Spaß beim Coden und mögen all Ihre Schriftarten gefunden werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}