---
category: general
date: 2026-10-07
description: Erfahren Sie, wie Sie ein Word‑Dokument erstellen und ein Kreisdiagramm
  mit Aspose.Words in C# einfügen. Der Leitfaden zeigt außerdem, wie Sie eine Word‑Datei
  mit benutzerdefinierten Diagrammbeschriftungen erzeugen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: de
lastmod: 2026-10-07
og_description: Erstelle ein Word‑Dokument und füge ein Kreisdiagramm in C# ein. Befolge
  diese Schritt‑für‑Schritt‑Anleitung, um eine Word‑Datei mit vollständig angepassten
  Diagrammbeschriftungen zu erstellen.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Erstelle ein Word‑Dokument mit einem benutzerdefinierten Kreisdiagramm in
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Wie man ein Word‑Dokument mit einem angepassten Kreisdiagramm in C# erstellt
url: /de/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word‑Dokument mit einem angepassten Kreisdiagramm in C# erstellt

Wenn Sie **ein Word‑Dokument** programmgesteuert **erstellen** möchten, zeigt Ihnen dieses Tutorial, wie Sie ein **Kreisdiagramm einfügen** und dessen Datenbeschriftungen mit Aspose.Words für .NET anpassen. Sie lernen außerdem, wie Sie eine **Word‑Datei generieren**, die ein vollständig formatieres Diagramm enthält – von der Projekt‑Einrichtung bis zum Speichern des fertigen Dokuments.

Der Leitfaden führt Sie Schritt für Schritt durch das Hinzufügen eines Diagramms, das Anpassen der Beschriftungspositionen, das Aktivieren von Führungslinien und schließlich das Speichern des Ergebnisses als `.docx`‑Datei. Es werden keine externen Tools außer der Aspose.Words‑Bibliothek benötigt, und der komplette Quellcode wird bereitgestellt, sodass Sie ihn sofort kopieren, einfügen und ausführen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder neuer installiert  
* Eine gültige Aspose.Words für .NET‑Lizenz (oder einen kostenlosen Evaluierungsschlüssel)  
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code  

Sie müssen außerdem die folgenden NuGet‑Pakete zu Ihrem Projekt hinzufügen:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Diese Pakete stellen die Klassen `Document`, `DocumentBuilder` und die diagrammspezifischen Klassen bereit, die in den nachfolgenden Beispielen verwendet werden.

## Word‑Dokument erstellen und ein Diagramm hinzufügen

Der erste Schritt besteht darin, ein **Word‑Dokument** zu **erstellen** und einen `DocumentBuilder` zu erhalten, mit dem Sie Inhalte einfügen können. Der Builder funktioniert wie ein Cursor, der im Dokument positioniert ist.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Das Objekt `Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` Methoden wie `InsertChart` bereitstellt, die Objekte direkt in den Dokumenten‑Fluss einfügen.

## Kreisdiagramm in das Dokument einfügen

Jetzt, wo der Builder bereit ist, können Sie ein **Kreisdiagramm** mit einer bestimmten Größe **einfügen**. Das Diagramm wird an der aktuellen Position des Builders hinzugefügt.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` gibt ein `Chart`‑Objekt zurück, das Sie weiter manipulieren können. Die Beispieldaten erzeugen vier Segmente, die den Quartalsumsatz darstellen.

## Datenbeschriftungen des Kreisdiagramms anpassen

Um das Diagramm besser lesbar zu machen, müssen Sie häufig die **Kreisdiagramm**‑Beschriftungen **anpassen** – sie außerhalb der Segmente positionieren und Führungslinien anzeigen. Hier kommt die `ChartDataLabelCollection` ins Spiel.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Durch Setzen von `Position` auf `OutsideEnd` wird jede Beschriftung jenseits des Segmentrandes platziert, während `ShowLeaderLines` eine Linie zeichnet, die die Beschriftung mit ihrem Segment verbindet. Die optionalen Flags `ShowValue` und `ShowPercentage` geben dem Leser sowohl Rohzahlen als auch relative Prozentsätze.

**Pro‑Tipp:** Wenn Sie die Schriftart der Beschriftung formatieren möchten, verwenden Sie `dataLabels.Font`, um Größe, Farbe und Stil festzulegen. So stimmt das Diagramm mit Ihrem Corporate Branding überein.

## Word‑Datei speichern und generieren

Nachdem das Diagramm vollständig konfiguriert ist, können Sie die **Word‑Datei** **generieren**, indem Sie die `Document`‑Instanz auf die Festplatte speichern. Wählen Sie das `.docx`‑Format für maximale Kompatibilität mit modernen Word‑Versionen.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wenn Sie `CustomPieChart.docx` öffnen, sehen Sie ein Kreisdiagramm mit vier Segmenten, jedes außen beschriftet, verbunden durch Führungslinien und mit sowohl Wert als auch Prozentsatz angezeigt.

![Screenshot eines Word‑Dokuments, das ein angepasstes Kreisdiagramm enthält, erstellt mit C#](image-placeholder.png)

*Das Bild zeigt das Endergebnis des **create word document**‑Tutorials.*

## Häufige Varianten und Sonderfälle

| Szenario | Wie der Code anzupassen ist |
|----------|-----------------------------|
| **Mehrere Serien** | Fügen Sie zusätzliche `ChartSeries`‑Objekte zu `pieChart.Series` hinzu. Jede Serie kann ihre eigene `DataLabels`‑Sammlung für unabhängige Formatierung besitzen. |
| **Andere Diagrammgröße** | Ändern Sie die Breiten‑ und Höhenparameter in `InsertChart(width, height)`. Werte sind in Punkten (1 pt ≈ 1/72 in). |
| **Diagrammtitel** | Verwenden Sie `pieChart.Title.Text = "Quarterly Sales"` um einen beschreibenden Titel hinzuzufügen. |
| **Export nach PDF** | Rufen Sie `document.Save("Report.pdf", SaveFormat.Pdf);` auf, nachdem das Diagramm erstellt wurde. |
| **Lizenzverwaltung** | Platzieren Sie Ihre Lizenzdatei (`Aspose.Words.lic`) im Anwendungsverzeichnis und laden Sie sie mit `new License().SetLicense("Aspose.Words.lic");` bevor Sie das Dokument erstellen. |

Diese Varianten ermöglichen es Ihnen, die Frage **how to add pie chart** in vielen realen Szenarien zu beantworten – von einfachen Berichten bis zu komplexen Dashboards.

## Fazit

Sie wissen jetzt, wie Sie **ein Word‑Dokument erstellen**, **ein Kreisdiagramm einfügen** und **Kreisdiagramm‑Beschriftungen** mit Aspose.Words für .NET **anpassen**. Das vollständige Beispiel demonstriert einen klaren Workflow: Dokument initialisieren, Diagramm hinzufügen, Position der Datenbeschriftungen anpassen, Führungslinien aktivieren und schließlich die **Word‑Datei generieren**, die Sie mit jedem teilen können.

Versuchen Sie, dieses Tutorial zu erweitern, indem Sie mit anderen Diagrammtypen (`ChartType.Column`, `ChartType.Line`) experimentieren oder benutzerdefinierte Farbpaletten anwenden, um Ihrer Marke zu entsprechen. Bei Problemen konsultieren Sie die Aspose.Words‑Dokumentation oder erkunden verwandte Themen wie „how to add pie chart“ mit mehreren Serien und dynamischen Datenquellen.

Viel Spaß beim Coden und teilen Sie gern Ihre Ergebnisse oder stellen Sie Nachfragen in den Kommentaren!

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}