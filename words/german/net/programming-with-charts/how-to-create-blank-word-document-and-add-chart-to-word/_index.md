---
category: general
date: 2026-09-08
description: Erstellen Sie ein leeres Word‑Dokument und fügen Sie ein Diagramm mit
  Aspose.Words hinzu. Erfahren Sie, wie Sie ein Radar‑Diagramm einfügen, Graduierungen
  aktivieren und die Datei speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: de
lastmod: 2026-09-08
og_description: Erstellen Sie ein leeres Word‑Dokument und fügen Sie ein Diagramm
  zu Word mit Aspose.Words hinzu. Dieses Tutorial zeigt, wie man ein Radar‑Diagramm
  einfügt, die Achsen konfiguriert und das Dokument speichert.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Erstellen Sie ein leeres Word-Dokument und fügen Sie ein Radar‑Diagramm
  hinzu – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Wie man ein leeres Word‑Dokument erstellt und ein Diagramm in Word einfügt
url: /de/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word-Dokument erstellt und ein Diagramm zu Word hinzufügt

Wenn Sie ein **leeres Word-Dokument** für einen Bericht, eine Vorlage oder einen automatisierten Seriendruck benötigen, führt Sie diese Anleitung durch den gesamten Prozess mit C# und Aspose.Words. Sie lernen außerdem, wie man **ein Diagramm zu Word hinzufügt**, insbesondere wie man **ein Radar‑Diagramm einfügt**, Graduierungen aktiviert und das Ergebnis als .docx‑Datei speichert.

Dieses Tutorial deckt alles ab, von der Projektkonfiguration bis zum abschließenden Verifizierungsschritt. Am Ende haben Sie einen wiederverwendbaren Code‑Snippet, den Sie in jede .NET‑Anwendung einbinden können. Vorkenntnisse mit Aspose.Words sind nicht erforderlich, aber Sie sollten grundlegende C#‑Kenntnisse und ein aktuelles .NET‑SDK installiert haben.

## Voraussetzungen

- .NET 6.0 SDK oder höher  
- Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`)  
- Eine IDE wie Visual Studio 2022 oder VS Code  
- Schreibberechtigung für den Ordner, in dem das Dokument gespeichert wird  

Sie können die Bibliothek mit dem folgenden Befehl installieren:

```bash
dotnet add package Aspose.Words
```

## Schritt 1: Leeres Word-Dokument erstellen

Der erste Schritt besteht darin, ein **leeres Word-Dokument** im Speicher zu **erstellen**. Die Klasse `Document` repräsentiert die gesamte Datei, während `DocumentBuilder` eine fluente API zum Hinzufügen von Inhalten bereitstellt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` beginnt leer, sodass Sie eine saubere Leinwand haben, auf der Sie das Diagramm platzieren können. Das Dokument zu diesem Zeitpunkt leer zu lassen, erleichtert die Wiederverwendung desselben Codes für verschiedene Vorlagen.

## Schritt 2: Diagramm zu Word hinzufügen

Als Nächstes **fügen wir ein Diagramm zu Word hinzu**, indem wir `InsertChart` aufrufen. Die Methode benötigt den Diagrammtyp und die gewünschten Abmessungen in Punkten (1 Punkt = 1/72 Zoll).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` weist Aspose.Words an, ein radiales Diagramm zu erzeugen, das ideal ist, um multivariate Daten in einer kreisförmigen Anordnung darzustellen. Die Größenwerte (400 × 300) eignen sich gut für die meisten Hochformatseiten, können jedoch an Ihr Layout angepasst werden.

## Schritt 3: Radar‑Diagramm einfügen und Graduierungen konfigurieren

Jetzt **fügen wir ein Radar‑Diagramm ein** und aktivieren Graduierungen (Markierungen) sowohl auf der Kategorien‑ (X‑) als auch auf der Werte‑Achse (Y). Graduierungen verbessern die Lesbarkeit, indem sie die genauen Positionen jedes Datenpunkts anzeigen.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Durch Setzen von `HasGraduations` auf `true` werden Markierungen auf den Achsen gezeichnet. Das optionale `GraduationStep` steuert den Abstand zwischen den Markierungen auf der radialen Achse; ein Schritt von 10 bedeutet eine Markierung alle 10 Grad.

### Profi‑Tipp
Wenn Sie Datenbeschriftungen anzeigen müssen, rufen Sie `radarChart.Series[0].HasDataLabel = true;` auf. Dadurch wird der numerische Wert neben jedem Punkt hinzugefügt, was für Präsentationen nützlich ist.

## Schritt 4: Diagramm mit Beispieldaten füllen (optional)

Ein Radar‑Diagramm ohne Daten ist unsichtbar. Unten finden Sie eine schnelle Methode, um eine Reihe von Beispielwerten hinzuzufügen. Sie können diesen Block durch Ihre eigene Datenquelle ersetzen.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Jeder Aufruf von `Add` fügt einen Punkt zur Serie hinzu. Die Reihenfolge der Punkte entspricht den Winkelpositionen um den Kreis.

## Schritt 5: Dokument mit dem Diagramm speichern

Abschließend speichern Sie das Dokument auf dem Datenträger. Die Methode `Save` schreibt automatisch die .docx‑Datei und bewahrt das Diagramm sowie alle Formatierungen.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Das Ausführen des Programms erzeugt ein **leeres Word-Dokument**, das nun ein voll funktionsfähiges Radar‑Diagramm enthält. Öffnen Sie die Datei in Microsoft Word, um das Ergebnis zu sehen.

![Radar-Diagramm in Word-Dokument](radar_chart.png){alt="Radar-Diagramm in ein leeres Word-Dokument eingefügt"}

## Häufige Varianten und Sonderfälle

| Situation | Was zu ändern ist |
|-----------|-------------------|
| **Andere Diagrammgröße** | Passen Sie die Breiten-/Höhen‑Parameter von `InsertChart` an. |
| **Andere Diagrammtypen** | Ersetzen Sie `ChartType.Radar` durch `ChartType.Column`, `ChartType.Pie` usw. und behalten Sie die gleiche Graduierungslogik bei. |
| **Speichern in einen Stream** | Verwenden Sie `document.Save(Stream, SaveFormat.Docx)` |

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Flächendiagramm in Word-Dokument einfügen | Aspose.Words für .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Word-Streudiagramm mit Aspose.Words für .NET erstellen](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Säulendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}