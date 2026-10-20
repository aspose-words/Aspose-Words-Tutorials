---
category: general
date: 2026-07-26
description: Fügen Sie ein Kreisdiagramm in ein Word‑Dokument mit Aspose.Words ein.
  Erfahren Sie, wie Sie ein Diagramm hinzufügen, ein Segment hervorheben und Prozentsätze
  anzeigen – in nur wenigen Schritten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: de
lastmod: 2026-07-26
og_description: Fügen Sie ein Kreisdiagramm in eine Word-Datei mit Aspose.Words ein.
  Folgen Sie dieser Anleitung, um zu lernen, wie man ein Diagramm hinzufügt, ein Segment
  hervorhebt und Prozentsätze schnell anzeigt.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Kreisdiagramm in Word einfügen – Schritt‑für‑Schritt Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Kreisdiagramm in Word mit Aspose.Words einfügen – Vollständige Anleitung
url: /de/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kreisdiagramm in Word mit Aspose.Words einfügen – Komplettanleitung

Haben Sie schon einmal **ein Kreisdiagramm** in einen Word‑Bericht einfügen müssen, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein. In vielen Business‑Anwendungen sorgt das visuelle Highlight eines Kreisdiagramms dafür, dass Daten sofort verständlich werden – und Aspose.Words macht das mit nur wenigen Code‑Zeilen möglich.

In diesem Tutorial gehen wir die genauen Schritte durch, um **ein Diagramm zu Word hinzuzufügen**, einen Abschnitt hervorzuheben und Prozentsätze in den Datenbeschriftungen anzuzeigen. Am Ende haben Sie ein einsatzbereites Beispiel, das Sie in jedes .NET‑Projekt einbinden können.

---

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes haben:

- .NET 6.0 oder höher (der Code funktioniert sowohl mit .NET Core als auch mit .NET Framework)
- Das Aspose.Words for .NET NuGet‑Paket installiert  
  ```bash
  dotnet add package Aspose.Words
  ```
- Grundlegende Kenntnisse der C#‑Syntax – nichts Besonderes erforderlich
- Eine IDE Ihrer Wahl (Visual Studio, Rider oder VS Code)

Das war’s. Packen wir es an.

---

## Kreisdiagramm in ein Word‑Dokument einfügen

Als erstes benötigen wir ein frisches `Document`‑Objekt und einen `DocumentBuilder`. Denken Sie an den Builder wie an einen Stift, der direkt auf die Word‑Leinwand schreibt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Warum das wichtig ist:** Das `Document` repräsentiert die gesamte .docx‑Datei, während der `DocumentBuilder` uns eine bequeme API bietet, um Elemente wie Diagramme, Tabellen und Text einzufügen. Das ist die Grundlage für jede **how to add chart**‑Operation.

---

## Wie man ein Diagramm zu Word hinzufügt

Jetzt, wo wir einen Builder haben, können wir tatsächlich **ein Kreisdiagramm einfügen**. Die Methode `insertChart` nimmt den Diagrammtyp und die gewünschten Abmessungen in Punkten entgegen (1 Punkt = 1/72 Zoll).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tipp:** Wenn Sie eine andere Größe benötigen, passen Sie einfach die Werte für Breite und Höhe an. Das Diagramm skaliert automatisch, um in die Seitenränder zu passen.

---

## Wie man einen Abschnitt hervorhebt (Explode)

Eine gängige visuelle Anpassung besteht darin, einen Abschnitt „zu explodieren“, sodass er aus dem Kreis herausragt. Das lenkt den Blick des Lesers auf das wichtigste Segment.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Warum einen Abschnitt explodieren?** Wenn Sie eine bestimmte Kategorie hervorheben möchten – zum Beispiel „Umsatz Q1“ in einem Finanzbericht – macht das Explodieren des Abschnitts diesen sofort sichtbar, ohne zusätzlichen Text.

---

## Wie man Prozentsätze in den Datenbeschriftungen anzeigt

Die meisten Kreisdiagramme wirken ansprechender, wenn jeder Abschnitt seinen Prozentsatz anzeigt. Aspose.Words ermöglicht das mit einer einzigen Property.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Kurzinfo:** Das Flag `ShowPercentage` gilt für alle Punkte in der Serie, sodass Sie es nicht für jeden Abschnitt einzeln setzen müssen.

---

## Dokument mit dem Diagramm speichern

Zum Schluss schreiben wir das Dokument auf die Festplatte. Wählen Sie beliebig einen Ordner; stellen Sie nur sicher, dass der Pfad existiert.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Wenn Sie `PieChart.docx` in Microsoft Word öffnen, sehen Sie ein perfekt gerendertes Kreisdiagramm mit dem ersten Abschnitt explodiert und den Prozentsätzen – genau das, was man von einem professionellen Business‑Report erwartet.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, copy‑and‑paste‑bereite Programm. Führen Sie es als Konsolen‑App aus und prüfen Sie die Ausgabedatei.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erwartetes Ergebnis:** Öffnen Sie das erzeugte `PieChart.docx`. Sie sehen ein dreiteiliges Kreisdiagramm mit dem Titel „Sales Q1“, wobei der erste Abschnitt herausgezogen ist und jeder Abschnitt mit „30 %“, „45 %“ bzw. „25 %“ beschriftet ist. Die Visualisierung entspricht den eingegebenen Daten.

---

## Häufige Fragen & Sonderfälle

- **Was, wenn ich mehr als eine Serie brauche?**  
  Fügen Sie einfach zusätzliche `ChartSeries`‑Objekte zu `chart.Series` hinzu. Jede Serie kann ihr eigenes Datenset, Farben und Explode‑Einstellungen besitzen.

- **Kann ich die Farben des Diagramms ändern?**  
  Ja. Jeder `ChartPoint` verfügt über die Property `Format.Fill.ForeColor`, die Sie auf jede beliebige `System.Drawing.Color` setzen können.

- **Was ist mit anderen Diagrammtypen?**  
  Das `ChartType`‑Enum enthält Balken, Linien, Donut und viele weitere. Ersetzen Sie `ChartType.Pie` durch den gewünschten Visualisierungstyp.

- **Ist das Diagramm nach dem Einfügen in Word editierbar?**  
  Absolut. Word behandelt das Diagramm als native Office‑Grafik, sodass Benutzer per Doppelklick den integrierten Diagrammeditor öffnen können.

---

## Fazit

Sie wissen jetzt genau, wie Sie **ein Kreisdiagramm** in ein Word‑Dokument mit Aspose.Words **einfügen**, **ein Diagramm zu Word hinzufügen**, **einen Abschnitt explodieren** und **Prozentsätze** in den Datenbeschriftungen anzeigen. Das vollständige Beispiel oben ist sofort einsatzbereit, und Sie können es mit eigenen Daten, Styling‑Optionen oder zusätzlichen Serien erweitern.

Bereit für den nächsten Schritt? Ersetzen Sie das Kreisdiagramm durch ein Donut‑Diagramm oder erzeugen Sie einen Stapel von Berichten mit unterschiedlichen Datensätzen automatisch. Wenn Sie weitere Visualisierungen interessieren, schauen Sie sich unsere Anleitungen zu **how to add chart** für Balken‑ und Liniendiagramme an oder stöbern Sie in der **add chart to word**‑API‑Referenz für tiefere Anpassungen.

Viel Spaß beim Coden und mögen Ihre Dokumente stets so klar sein wie ein perfekt geschnittenes Stück Kuchen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}