---
category: general
date: 2026-06-24
description: Wie man IWarningCallback verwendet, um fehlende Schriftarten in Aspose.Words-Dokumenten
  zu erkennen. Erfahren Sie ein vollständiges, ausführbares Beispiel und bewährte
  Vorgehensweisen.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: de
og_description: Wie man IWarningCallback verwendet, um fehlende Schriftarten in Aspose.Words
  zu erkennen. Folgen Sie der Schritt‑für‑Schritt‑Anleitung für eine vollständige,
  produktionsreife Lösung.
og_title: Wie man IWarningCallback verwendet – Fehlende Schriftarten erkennen
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Wie man IWarningCallback verwendet – Fehlende Schriftarten mit Aspose.Words
  erkennen
url: /de/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man IWarningCallback verwendet – Fehlende Schriftarten mit Aspose.Words erkennen

Die Verwendung von **IWarningCallback** ist unverzichtbar, wenn Sie mit Aspose.Words arbeiten und **fehlende Schriftarten** in einer DOCX‑Datei erkennen müssen. In diesem Leitfaden führen wir Sie durch ein vollständiges Copy‑and‑Paste‑Beispiel, das genau zeigt, wie Sie IWarningCallback verwenden, um Schriftart‑Ersetzungswarnungen abzufangen, warum das wichtig ist und was zu tun ist, sobald Sie sie erfasst haben.

Wenn Sie jemals ein Dokument geöffnet haben und unleserlichen Text gesehen haben, weil eine benutzerdefinierte Schriftart nicht installiert war, kennen Sie die Frustration. Am Ende dieses Tutorials haben Sie eine zuverlässige Methode, diese Probleme programmgesteuert sichtbar zu machen, zu protokollieren oder sogar automatisch eine Ersatzschriftart anzuwenden.

## Was Sie lernen werden

- Der Zweck von **IWarningCallback** und wann er zu verwenden ist.  
- Wie man einen benutzerdefinierten Warnungs‑Collector implementiert, der **detect missing fonts**‑Ereignisse isoliert.  
- Den Collector in **LoadOptions** einbinden, sodass jeder Dokument‑Ladevorgang überwacht wird.  
- Die Ausgabe verifizieren und Randfälle behandeln (mehrere fehlende Schriftarten, stille Warnungen usw.).  

### Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+).  
- Aspose.Words für .NET, installiert über NuGet (`Install-Package Aspose.Words`).  
- Eine DOCX‑Datei, die eine Schriftart referenziert, die auf dem Rechner nicht vorhanden ist (z. B. `DocumentWithMissingFont.docx`).  

Weitere Bibliotheken sind nicht erforderlich – alles befindet sich innerhalb von Aspose.Words.

---

## Wie man IWarningCallback verwendet, um fehlende Schriftarten in Aspose.Words zu erkennen

Unten finden Sie das **vollständige, ausführbare Programm**. Kopieren Sie es in ein neues Konsolenprojekt, passen Sie den Dateipfad an und führen Sie es aus. Sie sehen die Konsolenausgabe für jede fehlende‑Schriftart‑Warnung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Erwartete Ausgabe

Wenn `DocumentWithMissingFont.docx` eine Schriftart namens *„MyFancyFont“* referenziert, die nicht installiert ist, sehen Sie etwa Folgendes:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Jede Zeile, die mit **[Missing Font]** beginnt, wird von unserer **IWarningCallback**‑Implementierung erzeugt und beweist, dass wir erfolgreich **fehlende Schriftarten erkennen**.

## Schritt 1: Implementieren der IWarningCallback‑Schnittstelle

Warum benötigen wir eine benutzerdefinierte Klasse? Aspose.Words gibt **Warnungen** aus verschiedenen Gründen aus – Dateiformat‑Probleme, veraltete Funktionen und, für uns am wichtigsten, Schriftart‑Ersetzung. Durch die Implementierung von `IWarningCallback` erhalten wir einen Hook, der jede Warnung in Echtzeit empfängt. Das Filtern nach `WarningType.FontSubstitution` isoliert das spezifische Szenario, bei dem eine Schriftart fehlt.

**Pro‑Tipp:** Wenn Sie *alle* Warnungen zu Diagnosezwecken erfassen müssen, entfernen Sie einfach die `if`‑Abfrage und protokollieren Sie jedes `info.Type`.

## Schritt 2: Den Callback in LoadOptions einbinden

`LoadOptions` ist das Tor, das Aspose.Words mitteilt, wie das eingehende Dokument behandelt werden soll. Das Setzen von `WarningCallback` auf eine Instanz unseres Collectors stellt sicher, dass der Callback für den gesamten Ladevorgang aktiv ist. Sie können dasselbe `LoadOptions`‑Objekt für mehrere Dokumente wiederverwenden, was in Batch‑Verarbeitungspipelines praktisch ist.

**Häufige Frage:** *Was passiert, wenn ich ein Dokument lade, ohne LoadOptions anzugeben?*  
Antwort: Aspose.Words wird weiterhin intern Warnungen ausgeben, aber ohne Callback werden sie still verworfen, und Sie verlieren die Möglichkeit, **fehlende Schriftarten zu erkennen**.

## Schritt 3: Ein Dokument laden und fehlende Schriftart‑Warnungen erfassen

Der `Document`‑Konstruktor, der einen Dateipfad und `LoadOptions` entgegennimmt, übernimmt die Hauptarbeit. Während die Datei geparst wird, löst jede fehlende Schriftart unsere Methode `FontWarningCollector.Warning` aus. Die Konsolenausgabe beweist, dass der Mechanismus funktioniert.

**Randfall:** Ein einzelnes Dokument kann mehrere fehlende Schriftarten referenzieren. Der Callback wird einmal pro fehlender Schriftart ausgelöst, sodass Sie mehrere Zeilen sehen – ideal, um einen umfassenden Bericht zu erstellen.

## Warum IWarningCallback statt manueller Schriftart‑Prüfungen verwenden?

Sie könnten nach dem Laden manuell die `Run.Font`‑Eigenschaften des Dokuments durchsuchen, aber das würde voraussetzen, dass das Dokument erfolgreich geladen wird – was fehlschlägt, wenn die Schriftart völlig nicht verfügbar ist. Das Warnsystem arbeitet **vor** jeder Ersetzung und liefert Ihnen ein echtes Bild dessen, was fehlt.

Zusätzlich wird der Callback **im Rahmen der Ladepipeline** ausgeführt, sodass Sie frühzeitig abbrechen, Schriftarten unterwegs ersetzen oder detaillierte Diagnosen protokollieren können, ohne zusätzliche Durchläufe über den Dokumentenbaum.

## Mehrere fehlende Schriftarten elegant handhaben

Wenn Sie viele fehlende Schriftarten erwarten, sollten Sie sie in einer Sammlung aggregieren:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Nach dem Laden können Sie über `MissingFonts` iterieren und sie beispielsweise in eine CSV‑Datei für das Design‑Team schreiben.

## Bonus: Warnungen in eine Datei protokollieren

Konsolenausgabe ist für Demonstrationen in Ordnung, aber Produktionscode protokolliert normalerweise in einem persistenten Speicher. Ersetzen Sie den Aufruf `Console.WriteLine` durch etwas wie:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Jetzt haben Sie ein Prüfprotokoll, das später überprüft werden kann und Compliance‑Anforderungen erfüllt.

## Fazit

Wir haben behandelt, **wie man IWarningCallback** verwendet, um **fehlende Schriftarten** in Aspose.Words zu **erkennen**, von der Implementierung des Callbacks über das Einbinden in `LoadOptions` bis hin zur Verarbeitung der resultierenden Warnungen. Dieser Ansatz liefert Ihnen Echtzeit‑Einblicke in schriftbezogene Probleme, sodass Sie protokollieren, ersetzen oder Benutzer warnen können, bevor das Dokument gerendert wird.

Nächste Schritte, die Sie erkunden könnten:

- **Fallback fonts:** programmgesteuert eine Standardschriftart zuweisen, wenn eine Ersetzung erfolgt.  
- **Batch processing:** über einen Ordner von Dokumenten iterieren und dabei denselben `AggregatingFontCollector` wiederverwenden.  
- **User feedback:** fehlende‑Schriftart‑Warnungen in einer Benutzeroberfläche statt in der Konsole anzeigen.

Probieren Sie es in Ihrem eigenen Projekt aus – kein mysteriöser, unleserlicher Text mehr, sondern klare, umsetzbare Diagnosen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}