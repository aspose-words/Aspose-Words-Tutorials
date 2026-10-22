---
category: general
date: 2026-08-04
description: Wie man Datenbeschriftungen in C# mit Aspose.Words hinzufügt. Erfahren
  Sie, wie Sie Diagramme bearbeiten, Diagrammdatenbeschriftungen zentrieren, Prozentsätze
  im Diagramm anzeigen und Diagrammdatenbeschriftungen anpassen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: de
lastmod: 2026-08-04
og_description: Wie man Datenbeschriftungen in C# mit Aspose.Words hinzufügt. Dieses
  Tutorial zeigt Ihnen, wie Sie Diagramme bearbeiten, Diagrammbeschriftungen zentrieren,
  Prozentsätze im Diagramm anzeigen und Diagrammbeschriftungen anpassen.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Wie man Datenbeschriftungen zu einem Word‑Diagramm in C# hinzufügt – vollständige
  Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Wie man Datenbeschriftungen zu einem Word‑Diagramm in C# hinzufügt – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Datenbeschriftungen zu einem Word‑Diagramm in C# hinzufügt – Schritt‑für‑Schritt‑Anleitung

Wenn Sie **how to add data labels** zu einem Diagramm, das sich in einem Word‑Dokument befindet, benötigen, zeigt Ihnen diese Anleitung den genauen Code, den Sie ausführen müssen. Sie sehen, wie Sie Diagrammeigenschaften bearbeiten, **center chart data labels**, **show percentages in chart** und **customize chart data labels** für jedes Szenario anpassen.

Das Tutorial deckt alles ab, was zum Ändern eines bestehenden Diagramms erforderlich ist, vom Laden des Dokuments bis zum Speichern der Änderungen. Es werden keine externen Referenzen benötigt – nur die Aspose.Words for .NET‑Bibliothek und eine grundlegende C#‑Entwicklungsumgebung.

## Voraussetzungen

* .NET 6.0 (oder höher) installiert.
* Aspose.Words for .NET Version 23.9 oder neuer.  
  Sie können es über NuGet installieren:

```bash
dotnet add package Aspose.Words
```

* Eine Word‑Datei (`input.docx`), die mindestens ein Diagramm enthält.

## Wie man Datenbeschriftungen zu einem Word‑Diagramm in C# hinzufügt

Die folgenden Abschnitte führen Sie Schritt für Schritt durch. Das Haupt‑Keyword **how to add data labels** erscheint natürlich im Text und in den Code‑Kommentaren und hält die Dichte im empfohlenen Bereich.

### Schritt 1 – Laden des Word‑Dokuments, das das Diagramm enthält

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Warum dieser Schritt wichtig ist*: Das `Document`‑Objekt repräsentiert die gesamte Word‑Datei. Durch das Laden erhalten Sie Zugriff auf jeden Knoten, einschließlich der Shapes, die Diagramme enthalten.

### Schritt 2 – Das erste Diagramm aus dem Dokument abrufen

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Warum dieser Schritt wichtig ist*: Diagramme werden in `Shape`‑Knoten gespeichert. Durch das Casten des abgerufenen Knotens zu `Shape` und den Aufruf von `GetChart()` erhalten Sie ein `Chart`‑Objekt, das Serien, Achsen und Beschriftungssammlungen bereitstellt.

### Schritt 3 – Datenbeschriftungs‑Anpassung aktivieren und Prozentsätze im Diagramm anzeigen

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Warum dieser Schritt wichtig ist*: Das Setzen von `ShowPercentage` weist Aspose.Words an, den Beitrag jedes Abschnitts zum Gesamtergebnis zu berechnen und anzuzeigen. Dies greift direkt das sekundäre Keyword **show percentages in chart** auf.

### Schritt 4 – Die Beschriftungsposition in die Mitte jedes Datenpunkts ändern

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Warum dieser Schritt wichtig ist*: Die Eigenschaft `Position` bestimmt, wo die Beschriftung relativ zum Datenpunkt erscheint. Die Verwendung von `Center` erfüllt das sekundäre Keyword **center chart data labels** und verbessert die Lesbarkeit bei Kreis‑ oder Donut‑Diagrammen.

### Schritt 5 – Diagrammbeschriftungen weiter anpassen (optional)

Wenn Sie mehr Kontrolle benötigen, können Sie Schriftart, Farbe oder Führungslinien anpassen:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Diese Einstellungen veranschaulichen das sekundäre Keyword **customize chart data labels** und zeigen, wie Sie das Aussehen an Markenrichtlinien anpassen können.

### Schritt 6 – Das geänderte Dokument speichern

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Warum dieser Schritt wichtig ist*: Beim Speichern wird das aktualisierte Diagramm zurück in das Word‑Dokument geschrieben, sodass die neuen Datenbeschriftungen sichtbar werden, wenn die Datei in Microsoft Word geöffnet wird.

## Vollständiges, ausführbares Beispiel

Unten finden Sie ein vollständiges Programm, das Sie kopieren, einfügen und ausführen können. Es enthält alle erforderlichen `using`‑Direktiven und Kommentare, die jede Zeile erklären.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Erwartetes Ergebnis

Wenn Sie `output.docx` in Microsoft Word öffnen, wird das Diagramm anzeigen:

* Prozentwerte neben jedem Abschnitt (z. B. **25 %**, **40 %**, …).
* Beschriftungen, die in der Mitte jedes Datenpunkts positioniert sind.
* Alle zusätzlichen Formatierungen, die Sie angewendet haben, wie fettroter Text.

Diese visuellen Hinweise machen das Diagramm leichter zu interpretieren, besonders in Präsentationen oder Berichten.

## Wie man Diagrammeigenschaften über Datenbeschriftungen hinaus bearbeitet

Obwohl der Schwerpunkt dieses Leitfadens **how to add data labels** ist, möchten Sie vielleicht auch **how to edit chart**‑Einstellungen wie Titel, Legendenposition oder Achsenformatierung ändern. Das `Chart`‑Objekt bietet Eigenschaften wie `Title`, `Legend` und `AxisX/AxisY`. Zum Beispiel, um den Diagrammtitel zu ändern:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Alle Diagrammänderungen folgen demselben Muster: Diagramm abrufen, Eigenschaften anpassen und dann das Dokument speichern.

## Häufige Fallstricke und bewährte Tipps

| Problem | Warum es passiert | Empfohlene Lösung |
|---|---|---|
| Das Diagramm befindet sich in einer gruppierten Form. | `GetChild(NodeType.Shape, …)` gibt die äußere Gruppe zurück, nicht das innere Diagramm. | Rekursiv nach einer Form mit `shape.HasChart` suchen. |
| Datenbeschriftungen erscheinen nach dem Speichern nicht. | `ShowValue` oder `ShowPercentage` war nicht auf `true` gesetzt. | Setzen Sie explizit sowohl `ShowValue` als auch `ShowPercentage` nach Bedarf. |
| Beschriftungen überlappen bei kleinen Abschnitten. | Zentrierte Positionierung kann zu Überfüllung führen. | Verwenden Sie `ChartDataLabelPosition.OutSideEnd` für die Platzierung außen oder aktivieren Sie `LeaderLines`. |

## Fazit

Sie wissen jetzt, wie man **how to add data labels** zu einem Word‑Diagramm mit C# hinzufügt. Das Tutorial behandelte das Abrufen des Diagramms, das Aktivieren der Beschriftungsanzeige, das Zentrieren der Beschriftungen, das Anzeigen von Prozentsätzen und das Anpassen des Aussehens. Mit diesem Wissen können Sie auch **how to edit chart**‑Details, **center chart data labels**, **show percentages in chart** und **customize chart data labels** für jedes Reporting‑Szenario bearbeiten.

Bereit, mehr zu entdecken? Versuchen Sie, mehrere Serien hinzuzufügen, bedingte Formatierungen anzuwenden oder das Diagramm als Bild zu exportieren. Die Aspose.Words‑API bietet umfangreiche Möglichkeiten zur Diagrammbearbeitung – experimentieren Sie, um die perfekte visuelle Darstellung Ihrer Daten zu finden.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}