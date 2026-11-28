---
category: general
date: 2026-10-13
description: Aspose.Words Radialdiagramm‑Beispiel, das zeigt, wie man Graduierungen
  in einem Radialdiagramm mit C# und Aspose.Words 24.9+ aktiviert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: de
lastmod: 2026-10-13
og_description: Aspose.Words Radialdiagramm‑Beispiel, das das Aktivieren von Graduierungen
  in einem Radialdiagramm mit C# und der neuesten 24.9+‑Bibliothek demonstriert.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words Radialdiagramm‑Beispiel – Graduierungen in C# aktivieren
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words Radialdiagram‑Beispiel: Graduierungen in C# aktivieren'
url: /de/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Radialdiagramm-Beispiel: Graduierungen in C# aktivieren

Wenn Sie nach einem **aspose.words radial chart example** suchen, sind Sie an der richtigen Stelle gelandet. Dieses Tutorial führt Sie durch die genauen Schritte, um Graduierungen für ein Radialdiagramm mit der Aspose.Words for .NET API zu aktivieren.

Radialdiagramme sind nützlich, um zyklische Daten wie Tageszeit‑Metriken oder saisonale Trends zu visualisieren. Standardmäßig sind die Graduierungen (die Markierungen um die kreisförmige Achse) ausgeblendet, was das Diagramm schwerer lesbar machen kann. Das Aktivieren ist ein einzeiliger Änderung, aber Sie müssen das korrekte Objektmodell und die Version kennen, die das Feature unterstützt.

In diesem Leitfaden lernen Sie, wie Sie:

* Ein Word‑Dokument laden, das bereits ein Radialdiagramm enthält.  
* Auf das Diagramm‑Shape über die Aspose.Words chart API zugreifen.  
* **Graduierungen sichtbar** schalten (verfügbar ab **Aspose.Words version 24.9**).  
* Das geänderte Dokument speichern und das Ergebnis überprüfen.

Der vollständige, ausführbare Code ist enthalten, sodass Sie ihn in ein neues Konsolen‑Projekt kopieren‑und‑einfügen können und die Wirkung sofort sehen.

![Aspose.Words Radialdiagramm-Beispiel mit Graduierungen](https://example.com/images/radial-chart-graduations.png "Aspose.Words Radialdiagramm-Beispiel, das aktivierte Graduierungen zeigt")

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie:

| Anforderung | Warum es wichtig ist |
|-------------|----------------------|
| .NET 6.0 oder höher | Aspose.Words for .NET 24.9+ zielt auf .NET Standard 2.0 ab und funktioniert auf .NET 6+. |
| Aspose.Words for .NET **24.9** oder neuer | Die Eigenschaft `IsGraduationsVisible` wurde in Version 24.9 eingeführt. Ältere Versionen werfen eine `MissingMemberException`. |
| Ein Word‑Dokument (`RadialChart.docx`), das ein Radialdiagramm enthält | Das Beispiel bearbeitet ein vorhandenes Diagramm; das Erstellen eines neuen Diagramms von Grund auf ist ein separates Thema. |
| Eine C#‑IDE (Visual Studio, Rider, VS Code) | Jede IDE, die .NET‑Projekte kompilieren kann, funktioniert. |
| NuGet‑Paket `Aspose.Words` | Installation über `dotnet add package Aspose.Words --version 24.9.0` (oder neuer). |

> **Pro tip:** Wenn Sie nicht auf 24.9 aktualisieren können, können Sie weiterhin andere Diagrammeigenschaften ändern, aber Graduierungen bleiben verborgen, weil die API dieses Flag nicht bereitstellt.

## Aspose.Words Radialdiagramm‑Beispiel – Schritt‑für‑Schritt‑Anleitung

Die folgenden Abschnitte zerlegen den Prozess in diskrete, leicht nachvollziehbare Schritte. Jeder Schritt enthält den genauen Code, den Sie benötigen, und eine kurze Erklärung, *warum* der Schritt existiert.

### Schritt 1: Laden Sie das Dokument, das ein Radialdiagramm enthält

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Warum das wichtig ist:**  
`Document` ist der Einstiegspunkt der **Aspose.Words chart API**. Es lädt die DOCX‑Datei in den Speicher und gibt Ihnen Zugriff auf jeden Knoten – Absätze, Tabellen und Diagrammformen. Wenn die Datei nicht gefunden wird, wirft `Document` eine `FileNotFoundException`, die Sie im Produktionscode behandeln sollten.

### Schritt 2: Das erste Diagramm‑Shape aus dem Dokument abrufen

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Warum das wichtig ist:**  
Diagramme werden als `Shape`‑Knoten gespeichert. Die Methode `GetChild` mit `NodeType.Shape` durchläuft den DOM und gibt das erste passende Shape zurück. Das Casting zu `Chart` ermöglicht den Zugriff auf diagrammspezifische Eigenschaften wie `RadialChart`. Die Null‑Prüfung sorgt dafür, dass Sie einen klaren Fehler erhalten, wenn das Dokument kein Diagramm enthält – ein häufiger Randfall bei der Wiederverwendung von Vorlagen.

### Schritt 3: Graduierungen im Radialdiagramm aktivieren

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Warum das wichtig ist:**  
`IsGraduationsVisible` steuert die Markierungen um die kreisförmige Achse. Wenn sie auf `true` gesetzt ist, rendert das Diagramm Graduierungen, was die Lesbarkeit für Betrachter verbessert, die Werte präzise ablesen müssen. Die Eigenschaft befindet sich unter `RadialChart`, das ein Sub‑Typ von `Chart` ist. Wenn Sie dies bei einem Nicht‑Radialdiagramm (z. B. einem Balkendiagramm) versuchen, ist die Eigenschaft `RadialChart` `null`, daher sollten Sie in komplexeren Szenarien zunächst den Diagrammtyp prüfen.

#### Umgang mit Nicht‑Radialdiagrammen (optional)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Diese Prüfung macht den Code robust, wenn das Quelldokument verschiedene Diagrammtypen enthalten könnte.

### Schritt 4: Das geänderte Dokument speichern

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Warum das wichtig ist:**  
Der Aufruf von `Save` schreibt den im Speicher befindlichen DOM zurück in eine .docx‑Datei und speichert die vorgenommenen Änderungen am Diagramm. Die Ausgabedatei kann in Microsoft Word, LibreOffice oder jedem anderen DOCX‑Viewer geöffnet werden. Sie sehen das Radialdiagramm mit sichtbaren Graduierungen.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in `Program.cs` eines .NET‑Konsolenprojekts einfügen können.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Erwartete Ausgabe

Wenn Sie `RadialChart_Graduations.docx` in Word öffnen, wird das Radialdiagramm Markierungen (Graduierungen) um die kreisförmige Achse anzeigen, ähnlich dem zuvor gezeigten Screenshot. Der Rest des Diagramms (Datenreihen, Legende, Titel) bleibt unverändert.

## Häufige Varianten und Randfälle

| Situation | Lösung |
|-----------|--------|
| **Ältere Aspose.Words-Version (< 24.9)** | Aktualisieren Sie auf das neueste NuGet‑Paket. Die Eigenschaft `IsGraduationsVisible` existiert in früheren Versionen nicht. |
| **Mehrere Diagramme im selben Dokument** | Verwenden Sie `doc.GetChild(NodeType.Shape, index, true)` mit dem passenden `index` oder iterieren Sie über `doc.GetChildNodes(NodeType.Shape, true)` und filtern nach `ChartType.Radial`. |
| **Diagramm programmgesteuert erstellt** | Verwenden Sie `DocumentBuilder`, um ein Diagramm einzufügen, und setzen Sie anschließend `RadialChart.IsGraduationsVisible` auf das |

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Diagramm‑Seriendaten in einem Word-Dokument mit Aspose.Words für .NET aktualisieren](/words/english/net/programming-with-charts/modify-chart-series/)
- [Eine Diagramm‑Serie aus einem Word-Dokument mit Aspose.Words für .NET entfernen](/words/english/net/programming-with-charts/remove-chart-series/)
- [Plot‑Bereichsrand in einem Säulendiagramm mit Aspose.Words für .NET ausblenden](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}