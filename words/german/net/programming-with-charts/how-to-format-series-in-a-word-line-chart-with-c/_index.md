---
category: general
date: 2026-09-21
description: Wie man Serien in einem Word‑Liniendiagramm mit C# formatiert. Erfahren
  Sie, wie man ein Word‑Dokument erstellt, ein Liniendiagramm einfügt und ein benutzerdefiniertes
  Zahlenformat anwendet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: de
lastmod: 2026-09-21
og_description: Wie man Serien in einem Word‑Liniendiagramm mit C# formatiert. Dieses
  Tutorial zeigt, wie man ein Word‑Dokument erstellt, ein Liniendiagramm einfügt und
  ein benutzerdefiniertes Zahlenformat anwendet.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Wie man Serien in einem Word‑Liniendiagramm mit C# formatiert – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Wie man Serien in einem Word‑Liniendiagramm mit C# formatiert
url: /de/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Datenreihen in einem Word‑Liniendiagramm mit C# formatiert

Wenn Sie **Datenreihen formatieren** in einem Word‑Liniendiagramm müssen, bietet Ihnen dieser Leitfaden eine vollständige, sofort ausführbare Lösung. Sie sehen, wie man **ein Word‑Dokument erstellt**, **ein Liniendiagramm einfügt** und **ein benutzerdefiniertes Zahlenformat** auf die Y‑Werte anwendet – alles mit Aspose.Words für .NET.

Die Word‑Automatisierung wird einfach, sobald Sie das Diagramm‑Objektmodell verstehen. Am Ende dieses Tutorials besitzen Sie eine Word‑Datei, die ein Liniendiagramm enthält, dessen Datenreihen als Prozentsätze mit zwei Dezimalstellen angezeigt werden.

## Was Sie erreichen werden

* Erzeugen Sie programmgesteuert eine leere `.docx`‑Datei.  
* Fügen Sie ein Liniendiagramm mit der Größe 400 × 300 Punkten hinzu.  
* Greifen Sie auf die erste Datenreihe des Diagramms zu.  
* Wenden Sie den Formatcode `#,##0.00%` an, damit die Y‑Werte als Prozentsätze angezeigt werden.  

Keine externen Werkzeuge sind erforderlich, außer dem Aspose.Words NuGet‑Paket.

## Voraussetzungen

* .NET 6.0 SDK oder neuer.  
* Visual Studio 2022 (oder jede C#‑IDE).  
* Aspose.Words für .NET 23.10 oder neuer – Installation über `dotnet add package Aspose.Words`.  

Der Code funktioniert unter Windows, Linux und macOS, da Aspose.Words plattformunabhängig ist.

## Erstellen eines Word‑Dokuments mit Aspose.Words

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die gesamte Word‑Datei im Speicher.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Warum das wichtig ist*: `Document` ist der Einstiegspunkt für alle Word‑Verarbeitungs‑Operationen. Ohne es können Sie keine Absätze, Tabellen oder Diagramme hinzufügen.

## Liniendiagramm in das Dokument einfügen

Ein `DocumentBuilder` schreibt Inhalte in das `Document`. Der Aufruf von `InsertChart` erzeugt eine Diagramm‑Form auf der aktuellen Seite.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Warum das wichtig ist*: `InsertChart` liefert ein `Chart`‑Objekt, das Ihnen die vollständige Kontrolle über Reihen, Achsen und Formatierung gibt. Die Größenparameter werden in Punkten angegeben (1 Punkt = 1/72 Zoll).

## Auf die erste Datenreihe zugreifen

Jedes Diagramm enthält ein oder mehrere `ChartSeries`. Die erste Reihe befindet sich an Index 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Warum das wichtig ist*: Das `ChartSeries`‑Objekt enthält die Y‑Werte, X‑Werte und Formatierungsoptionen für eine einzelne Linie in einem Liniendiagramm. Das Ändern dieses Objekts verändert die visuelle Darstellung der Daten.

## Ein benutzerdefiniertes Zahlenformat auf die Reihe anwenden

Die Eigenschaft `FormatCode` bestimmt, wie numerische Werte angezeigt werden. Wird sie auf `#,##0.00%` gesetzt, weist das Word an, die Werte als Prozentsätze mit zwei Dezimalstellen zu behandeln.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Warum das wichtig ist*: Ohne ein benutzerdefiniertes Format zeigt Word rohe Dezimalzahlen (z. B. `0.15`). Der Formatcode wandelt sie in `15.00%` um, was häufig von Geschäftsberichten verlangt wird.

## Dokument speichern und Ergebnis überprüfen

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wenn Sie `FormattedSeriesLineChart.docx` in Microsoft Word öffnen, sehen Sie ein Liniendiagramm, bei dem die Y‑Achsen‑Beschriftungen `15.00%`, `30.00%`, `45.00%` und `60.00%` lauten. Die Diagrammgröße entspricht den in `InsertChart` angegebenen Abmessungen.

### Erwarteter Screenshot der Ausgabe

> *Bild: Eine Word‑Dokumentseite, die ein Liniendiagramm mit prozentual formatierten Y‑Achsenwerten zeigt.*  
> *(Alt-Text: Screenshot eines Word‑Dokuments, das ein Liniendiagramm mit prozentual formatierten Y‑Achsenwerten zeigt)*

## Häufige Variationen und Sonderfälle

| Situation | Anpassung |
|-----------|-----------|
| **Mehrere Reihen** | Durchlaufen Sie `chart.Series` und setzen Sie `FormatCode` für jede Reihe. |
| **Anderer Diagrammtyp** | Ersetzen Sie `ChartType.Line` durch `ChartType.Column`, `ChartType.Pie` usw. |
| **Länderspezifische Trennzeichen** | Verwenden Sie `CultureInfo`‑bewusste Formatzeichenfolgen, z. B. `"# ##0,00 %"` für französische Locale. |
| **Dynamische Datenquelle** | Befüllen Sie `series.YValues` aus einer Datenbank oder CSV‑Datei, bevor Sie das Format anwenden. |

**Pro‑Tipp:** Wenden Sie das Format immer **nach** dem Hinzufügen der Y‑Werte an. Das Format zuerst zu ändern und dann Werte hinzuzufügen funktioniert ebenfalls, aber die spätere Anwendung stellt sicher, dass das Format auf den endgültigen Datensatz angewendet wird.

## Zusammenfassung

Sie wissen jetzt, **wie man Datenreihen** in einem Word‑Liniendiagramm mit C# formatiert. Das Tutorial behandelte:

* Erstellen eines Word‑Dokuments (`create word document`).  
* Einfügen eines Liniendiagramms (`insert line chart`, `add chart to word`).  
* Zugriff auf die erste Reihe des Diagramms.  
* Anwenden eines benutzerdefinierten Zahlenformats (`apply custom number format`), um Prozentsätze anzuzeigen.

## Nächste Schritte

* Experimentieren Sie mit verschiedenen `ChartType`‑Werten, um zu sehen, wie sich andere Visualisierungen verhalten.  
* Fügen Sie Titel, Achsenbeschriftungen und Legenden mit `chart.Title`, `chart.AxisX.Title` und `chart.AxisY.Title` hinzu.  
* Exportieren Sie das Diagramm als Bild (`chart.Save` mit `SaveFormat.Png`) zur Verwendung in Web‑Berichten.  

Passen Sie dieses Muster gerne an, um Dashboards, Finanzberichte oder jedes Dokument zu erstellen, das programmatisches Diagrammieren erfordert. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}