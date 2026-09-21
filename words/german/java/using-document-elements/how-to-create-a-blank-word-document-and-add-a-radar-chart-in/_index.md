---
category: general
date: 2026-09-21
description: Erstellen Sie ein leeres Word‑Dokument und lernen Sie, wie Sie ein Radar‑Diagramm
  in eine Word‑Datei mit DocumentBuilder einfügen – Schritt‑für‑Schritt‑Anleitung.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: de
lastmod: 2026-09-21
og_description: Erstellen Sie ein leeres Word‑Dokument und fügen Sie ein Radar‑Diagramm
  in eine Word‑Datei mit Aspose.Words ein. Folgen Sie diesem Tutorial, um schnell
  ein Diagramm in einem Word‑Dokument zu erstellen.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Erstelle ein leeres Word‑Dokument und füge ein Radar‑Diagramm hinzu – vollständige
  C#‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Wie man ein leeres Word‑Dokument erstellt und ein Radar‑Diagramm in C# hinzufügt
url: /de/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word‑Dokument erstellt und ein Radar‑Diagramm in C# hinzufügt

Wenn Sie ein **leeres Word‑Dokument erstellen** und ein Radar‑ (radiales) Diagramm einbetten möchten, liefert dieses Tutorial eine sofort einsatzbereite Lösung. Sie sehen, wie Sie Aspose.Words .NET verwenden, um die Datei zu erzeugen, das Diagramm einzufügen und das Ergebnis zu speichern – alles in wenigen prägnanten Schritten.

Ein leeres Dokument bietet eine saubere Leinwand für jedes automatisierte Reporting‑Szenario, und das Hinzufügen eines Radar‑Diagramms ermöglicht es Ihnen, mehrdimensionale Daten direkt in Word zu visualisieren. Am Ende dieses Leitfadens können Sie ein Word‑Diagramm ohne manuelle Nachbearbeitung erzeugen.

## Was Sie lernen werden

* Wie man ein **leeres Word‑Dokument** programmgesteuert mit C# erstellt.
* Der genaue Code, um **ein Radar‑Diagramm einzufügen** mit `DocumentBuilder`.
* Möglichkeiten, **ein Diagramm in eine Word‑Datei einzufügen** und seine Größe anzupassen.
* Wie man **ein Word‑Dokument‑Diagramm generiert** und die Ausgabe überprüft.
* Tipps zum **Hinzufügen von radialen Diagrammen in Word‑Dateien**, einschließlich häufiger Stolperfallen.

### Voraussetzungen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+).
* Aspose.Words für .NET (NuGet‑Paket `Aspose.Words` Version 23.9 oder neuer).
* Grundlegende Kenntnisse in C# und Visual Studio oder Ihrer bevorzugten IDE.

## Erstellen eines leeren Word‑Dokuments mit C#

Der erste Schritt besteht darin, ein leeres `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert eine völlig leere `.docx`‑Datei.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` erzeugt die Dateistruktur, enthält aber noch keine Abschnitte oder Seiten. Aspose.Words fügt automatisch einen Standardabschnitt hinzu, sobald Sie Inhalte einfügen, weshalb der nächste Schritt ohne zusätzliche Konfiguration funktioniert.

## Wie man ein Radar‑Diagramm in die Word‑Datei einfügt

Ein Radar‑Diagramm (auch radiales Diagramm genannt) visualisiert Datenpunkte auf Achsen, die von einem zentralen Punkt ausstrahlen. Aspose.Words stellt dafür `DocumentBuilder.insertChart` bereit.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` gibt ein `Chart`‑Objekt zurück, das Sie weiter konfigurieren können. Das Diagramm erscheint auf der ersten Seite des leeren Dokuments, weil der Builder standardmäßig am Dokumentanfang positioniert ist.

## Diagramm in eine Word‑Datei einfügen – Datenreihen hinzufügen

Ein Diagramm ohne Daten ist unsichtbar. Befüllen Sie das Radar‑Diagramm mit einer oder mehreren Reihen, um es sinnvoll zu machen.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Sie können beliebig viele Reihen hinzufügen. Jede Reihe kann einen eigenen Namen besitzen, der in der Diagrammlegende erscheint. Die Datenpunkte entsprechen den radialen Achsen; die Reihenfolge, in der Sie sie hinzufügen, bestimmt ihre Position um den Kreis herum.

## Word‑Dokument‑Diagramm generieren – Datei speichern

Nachdem das Diagramm erstellt wurde, speichern Sie das Dokument auf dem Datenträger. Wählen Sie einen Ort, für den Sie Schreibrechte besitzen.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Wenn Sie die resultierende `.docx`‑Datei in Microsoft Word öffnen, sehen Sie eine leere Seite mit einem Radar‑Diagramm in der Größe 400 × 300 Punkte, befüllt mit den Beispieldaten.

### Erwartete Ausgabe

* Eine `RadialChartExample.docx`‑Datei auf Ihrem Desktop.
* Die erste Seite enthält ein Radar‑Diagramm mit fünf Datenpunkten, bezeichnet als „Series 1“.
* Kein zusätzlicher Text erscheint, weil das Dokument leer begann.

## Radiales Diagramm in Word hinzufügen – Umgang mit gängigen Randfällen

### 1. Diagrammgröße nach dem Einfügen ändern

Wenn die anfänglichen Abmessungen nicht in Ihr Layout passen, ändern Sie die Größe des Diagramms wie folgt:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Diagramm an einer bestimmten Position einfügen

Sie können den Cursor des Builders zu einem Lesezeichen, einer Tabellenzelle oder einem Absatz bewegen, bevor Sie `InsertChart` aufrufen.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Diagrammappearance anpassen

Aspose.Words stellt das vollständige Diagramm‑Objektmodell bereit, sodass Sie Titel, Achsenbeschriftungen und Farben festlegen können.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Umgang mit fehlenden Schriftarten

Fehlt in der Zielumgebung eine im Diagramm verwendete Schriftart, ersetzt Aspose.Words sie durch eine Standardschriftart. Um Konsistenz zu gewährleisten, betten Sie die erforderlichen Schriftarten ein:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Exportieren in andere Formate

Dasselbe Dokument kann ohne zusätzlichen Code als PDF, HTML oder PNG gespeichert werden:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Vollständiges, ausführbares Beispiel

Wenn Sie alle Bausteine zusammenfügen, erhalten Sie ein einzelnes Programm, das Sie kopieren, einfügen und ausführen können.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Führen Sie dieses Programm aus, öffnen Sie die erzeugte Datei, und Sie sehen ein professionelles Radar‑Diagramm, das zur Verteilung bereitsteht.

## Fazit

Sie wissen jetzt, wie man **ein leeres Word‑Dokument erstellt**, **ein Radar‑Diagramm einfügt** und **ein Word‑Dokument‑Diagramm generiert** mit Aspose.Words. Durch Befolgen der obigen Schritte können Sie außerdem **radiale Diagramme in Word‑Dateien hinzufügen** zu jeder automatisierten Reporting‑Pipeline, Größe, Stil anpassen und in weitere Formate exportieren.

**Nächste Schritte**

* Untersuchen Sie weitere Diagrammtypen (`ChartType.Column`, `ChartType.Pie`), um Ihr Reporting‑Toolkit zu erweitern.
* Kombinieren Sie mehrere Diagramme auf einer Seite, indem Sie `InsertChart` wiederholt aufrufen.
* Integrieren Sie Daten aus einer Datenbank oder einer CSV‑Datei, um Reihen dynamisch zu befüllen.
* Lesen Sie die Aspose.Words‑Dokumentation für erweiterte Formatierungsoptionen wie bedingte Datenbeschriftungen und Diagrammvorlagen.

Experimentieren Sie gern mit dem Code, passen Sie die Abmessungen an oder ersetzen Sie die Beispieldaten durch echte Geschäftskennzahlen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Spalten‑Diagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)
- [Streudiagramm in Word mit Aspose.Words für .NET erstellen](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Blasendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}