---
category: general
date: 2026-08-10
description: Erstellen Sie ein Word‑Dokument mit Kreisdiagramm mithilfe von Aspose.Words.
  Erfahren Sie, wie Sie ein Diagramm einfügen, die Farben des Kreisdiagramms anpassen
  und die Farbe eines Kreisdiagrammsegments in C# ändern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: de
lastmod: 2026-08-10
og_description: Erstellen Sie ein Word‑Dokument mit Kreisdiagramm mithilfe von Aspose.Words.
  Dieser Leitfaden erklärt, wie man ein Diagramm einfügt, die Farben des Kreisdiagramms
  anpasst und die Farbe eines Kreisabschnitts in einer C#‑Anwendung ändert.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Word‑Dokument mit Kreisdiagramm erstellen – Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Word-Dokument mit Kreisdiagramm mit Aspose.Words erstellen
url: /de/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kreisdiagramm‑Word‑Dokument mit Aspose.Words erstellen

Wenn Sie programmgesteuert ein **create pie chart Word document** benötigen, zeigt Ihnen dieses Tutorial genau, wie es geht. Wir gehen das Einfügen eines Diagramms, das **customizing pie chart colors**, und das **changing pie slice color** mit Aspose.Words für .NET durch.

Sie sehen ein vollständiges, ausführbares Beispiel, das Sie in Visual Studio kopieren, ausführen und sofort die erzeugte *.docx* öffnen können, um das formatierte Kreisdiagramm zu überprüfen. Keine externe Dokumentation ist erforderlich – alles, was Sie benötigen, befindet sich in diesem Leitfaden.

## Voraussetzungen

* .NET 6.0 SDK oder neuer installiert  
* Eine gültige Aspose.Words für .NET Lizenz (oder ein temporärer Evaluierungsschlüssel)  
* Visual Studio 2022 (oder jede C#‑IDE)  

Der Code verwendet nur die Namespaces `Aspose.Words` und `Aspose.Words.Drawing.Charts`, sodass keine zusätzlichen NuGet‑Pakete über die Aspose.Words‑Bibliothek hinaus erforderlich sind.

## Kreisdiagramm‑Word‑Dokument erstellen – vollständiges Beispiel

Das folgende C#‑Programm erstellt ein neues Word‑Dokument, fügt ein Kreisdiagramm ein, formatiert die ersten beiden Segmente und speichert die Datei. Jeder Schritt wird im Detail erklärt.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Erklärung jedes Schrittes

| Schritt | Was es tut | Warum es wichtig ist |
|---------|------------|----------------------|
| **1** | Erstellt ein neues `Document` und einen `DocumentBuilder`. | Der `DocumentBuilder` bietet fluente Methoden zum Einfügen von Inhalten, wie Diagrammen, in die Word‑Datei. |
| **2** | Ruft `InsertChart` mit `ChartType.Pie` und einer festen Größe auf. | `InsertChart` ist die **how to insert chart**‑Methode; die Angabe von Breite/Höhe stellt sicher, dass das Diagramm gut auf die Seite passt. |
| **3** | Fügt eine Datenreihe mit drei Kategorien und numerischen Werten hinzu. | Ein Kreisdiagramm ohne Daten ist unsichtbar; das Befüllen demonstriert die Formatierungsschritte. |
| **4** | Setzt `Explosion` beim ersten Punkt. | Das Explodieren eines Segments lenkt die Aufmerksamkeit auf einen bestimmten Abschnitt – nützlich, um wichtige Daten hervorzuheben. |
| **5** | Setzt `ForeColor` für die ersten beiden Punkte. | Dies ist der Kern von **customize pie chart colors**; Sie können jede `System.Drawing.Color` verwenden. |
| **6** | Zeigt, wie man **change pie slice color** für weitere Segmente anwendet. | Demonstriert, dass die Formatierung nicht auf die ersten beiden Segmente beschränkt ist; Sie können jedes Segment einzeln färben. |
| **7** | Speichert das Dokument als `PieChartStyled.docx`. | Die endgültige Ausgabe kann in Microsoft Word, Google Docs oder einem anderen kompatiblen Viewer geöffnet werden. |

#### Erwartete Ausgabe

Das Öffnen von `PieChartStyled.docx` zeigt eine einzelne Seite mit einem 400 × 300 pt Kreisdiagramm:

* Segment 1 (orange) ist nach außen explodiert.  
* Segment 2 (grün) erscheint neben dem explodierten Segment.  
* Segment 3 (stahlblau) füllt das verbleibende Segment.

Das Diagramm spiegelt die Datenwerte (30, 45, 25) und die von Ihnen definierten benutzerdefinierten Farben wider.

## Wie man ein Kreisdiagramm stylt – zusätzliche Tipps

* **Use theme colors** – anstatt `Color.Orange` hart zu codieren, können Sie Farben aus dem Dokument‑Theme übernehmen:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Add data labels** – wenn Sie Prozentsätze im Diagramm anzeigen möchten:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Resize dynamically** – berechnen Sie die Diagrammgröße basierend auf den Seitenrändern:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Diese Varianten demonstrieren die Flexibilität von **how to style pie** über das Grundbeispiel hinaus.

## Häufig gestellte Fragen beantwortet

**Q: Funktioniert das mit .NET Core?**  
A: Ja. Aspose.Words für .NET ist kompatibel mit .NET Core, .NET 5, .NET 6 und späteren Versionen. Verwenden Sie einfach dasselbe NuGet‑Paket.

**Q: Was ist, wenn ich ein Donut‑Diagramm anstelle eines Kreisdiagramms benötige?**  
A: Ersetzen Sie `ChartType.Pie` durch `ChartType.Doughnut`. Die gleichen Styling‑APIs (`Explosion`, `ForeColor`) gelten.

**Q: Kann ich das Diagramm in ein bestehendes Dokument einfügen?**  
A: Öffnen Sie die vorhandene Datei mit `new Document("Existing.docx")`, erstellen Sie einen `DocumentBuilder` für dieses Dokument und rufen Sie `InsertChart` an der gewünschten Cursor‑Position auf.

**Q: Wie gehe ich mit großen Datensätzen um?**  
A: Kreisdiagramme eignen sich am besten für eine begrenzte Anzahl von Kategorien (typischerweise < 10). Bei vielen Kategorien sollten Sie stattdessen ein Balken‑ oder Säulendiagramm in Betracht ziehen.

## Vollständiger Quellcode‑Rückblick

Unten finden Sie das komplette Programm in einem Block zum einfachen Kopieren und Einfügen:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Das Ausführen dieses Codes erzeugt das zuvor beschriebene formatierte Kreisdiagramm‑Word‑Dokument.

## Fazit

Sie wissen jetzt, wie man **create pie chart Word** Dokumente mit Aspose.Words erstellt, **customize pie chart colors** und **change pie slice color** programmgesteuert anpasst. Der Leitfaden behandelte das Einfügen des Diagramms, das Befüllen von Daten, das Explodieren eines Segments, das Anwenden benutzerdefinierter Farben und das Speichern des Ergebnisses.  

Ab hier können Sie verwandte Themen erkunden, wie **how to insert chart** Typen außer Kreisdiagrammen, das Hinzufügen von Legenden oder das Erzeugen von mehrseitigen Berichten mit mehreren Diagrammen. Experimentieren Sie mit verschiedenen Farbschemata und Datensätzen, um Ihren Berichtserfordernissen gerecht zu werden.

Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}