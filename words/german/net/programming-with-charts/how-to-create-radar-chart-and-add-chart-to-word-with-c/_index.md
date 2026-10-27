---
category: general
date: 2026-09-05
description: Erstelle ein Radar‑Diagramm in Word mit C#. Lerne, ein leeres Word‑Dokument
  zu erzeugen, ein Radar‑Diagramm hinzuzufügen, die Diagrammgröße festzulegen und
  Achsenmarkierungen schnell zu aktivieren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: de
lastmod: 2026-09-05
og_description: Erstellen Sie ein Radar‑Diagramm in Word mit C#. Diese Anleitung zeigt
  Ihnen, wie Sie ein leeres Word‑Dokument erzeugen, ein Radar‑Diagramm hinzufügen,
  die Diagrammgröße festlegen und Achsenmarkierungen aktivieren – alles in wenigen
  Minuten.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Radar‑Diagramm in Word erstellen – Schritt‑für‑Schritt C#‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Wie man ein Radar‑Diagramm erstellt und das Diagramm mit C# in Word einfügt
url: /de/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Radar-Diagramm erstellt und ein Diagramm zu Word mit C# hinzufügt

Wenn Sie ein **Radar-Diagramm** in einer Word-Datei erstellen müssen, führt Sie diese Anleitung durch den gesamten Prozess. Sie lernen, wie man ein **leeres Word-Dokument erzeugt**, ein Radar-Diagramm einfügt, **die Diagrammgröße in Word festlegt** und Achsenunterteilungen aktiviert – alles mit wenigen Zeilen C#-Code.

Visuelle Daten zu Berichten hinzuzufügen ist ein häufiges Anliegen, und die Verwendung von Aspose.Words macht es unkompliziert. In den nachfolgenden Schritten behandeln wir außerdem, wie man **Diagramme zu Word**-Dokumenten programmgesteuert **hinzufügt**, sodass Sie Dashboards, Finanzzusammenfassungen oder jegliche datengetriebene Inhalte automatisieren können.

## Voraussetzungen

* .NET 6.0 oder höher installiert  
* Eine Aspose.Words für .NET Lizenz (oder eine kostenlose Testversion) – die Bibliothek stellt die in diesem Tutorial verwendeten `Document`, `DocumentBuilder` und Diagramm‑APIs bereit  
* Visual Studio 2022 (oder jede C#‑IDE)  

> **Profi‑Tipp:** Wenn Sie testen, legen Sie die Aspose.Words‑DLL in den `bin`‑Ordner Ihres Projekts und referenzieren Sie sie über NuGet (`Install-Package Aspose.Words`).

## Wie man ein Radar-Diagramm in einem Word-Dokument erstellt

Der erste Schritt besteht darin, ein **leeres Word-Dokument zu erzeugen**, das das Diagramm aufnehmen wird. Das gibt Ihnen eine saubere Arbeitsfläche und ermöglicht es Ihnen, die Metadaten des Dokuments zu steuern, bevor Inhalt hinzugefügt wird.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Warum das wichtig ist:* Ein leeres `Document`‑Objekt stellt sicher, dass keine versteckten Stile oder Abschnitte das Diagrammlayout beeinträchtigen. Es ermöglicht Ihnen außerdem, bei Bedarf später Dokumenteigenschaften (Autor, Titel) festzulegen.

## Wie man ein Diagramm zu Word mit Aspose.Words hinzufügt

Als Nächstes erstellen Sie einen `DocumentBuilder`. Der Builder ist das Arbeitspferd, das Ihnen das Einfügen von Text, Bildern und Diagrammen in das Dokument ermöglicht.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Jetzt können Sie ein **Radar-Diagramm** direkt an der Cursorposition **hinzufügen**. Die Methode `InsertChart` akzeptiert ein `ChartType`‑Enum, Breite und Höhe in Punkten.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Warum 400 × 300?* Diese Abmessungen ergeben ein klares, gut lesbares Diagramm auf einer Standard‑A4‑Seite. Sie können die Größe später mit dem Schritt **Diagrammgröße in Word festlegen** anpassen, falls Ihr Layout ein anderes Seitenverhältnis erfordert.

## Diagrammgröße in Word festlegen

Wenn Sie die Größe nach dem Einfügen feinabstimmen müssen, können Sie die Eigenschaften `Width` und `Height` des Diagramms ändern. Das ist nützlich, wenn der umgebende Text oder die Seitenränder ein anderes visuelles Gleichgewicht erfordern.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Hinweis:** Die Überladung von `InsertChart` legt die Größe bereits fest, sodass der obige Code optional ist und nur zur Vollständigkeit gezeigt wird.

## Achsen‑Tick‑Markierungen auf der radialen Achse aktivieren

Ein Radar-Diagramm ist am nützlichsten, wenn die radiale Achse klare Unterteilungen zeigt. Die folgenden Einstellungen aktivieren Tick‑Markierungen und setzen das Intervall auf 30 Grad, was zu typischen Kompass‑Radar‑Darstellungen passt.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Warum das wichtig ist:* Unterteilungen helfen den Lesern, die Werte in jedem Winkel einzuschätzen, und verbessern die Lesbarkeit für Interessengruppen, die mit den Daten nicht vertraut sind.

## Das Dokument mit dem Diagramm speichern

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Sie können jeden gewünschten Ordner wählen; stellen Sie nur sicher, dass der Pfad existiert.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Wenn Sie `RadialChart.docx` in Microsoft Word öffnen, sehen Sie ein vollständig gerendertes Radar-Diagramm, das zentriert auf der Seite angezeigt wird, in der angegebenen Größe und mit Tick‑Markierungen alle 30 Grad.

### Erwartete Ausgabe

* Eine `.docx`‑Datei mit dem Namen **RadialChart.docx**  
* Die erste Seite enthält ein Radar-Diagramm mit der Größe 400 × 300 Punkte  
* Die X‑Achse (radiale Achse) zeigt Tick‑Markierungen bei 0°, 30°, 60°, …, 330°  

Sie können nun die Platzhalter‑Datenreihe durch Ihre eigenen Werte ersetzen, indem Sie auf `radarChart.Series` zugreifen – das liegt jedoch außerhalb des Umfangs dieses grundlegenden **Radar‑Diagramm‑hinzufügen**‑Tutorials.

## Häufige Variationen und Sonderfälle

| Szenario | Anpassung |
|----------|------------|
| **Anderer Diagrammtyp** | Ersetzen Sie `ChartType.Radar` durch `ChartType.Column`, `ChartType.Pie` usw. |
| **Mehrere Diagramme** | Rufen Sie `InsertChart` wiederholt auf; jeder Aufruf positioniert das neue Diagramm nach dem vorherigen. |
| **Große Datensätze** | Verwenden Sie `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)`, um viele Punkte zu befüllen. |
| **Speichern als PDF** | Rufen Sie `document.Save("RadialChart.pdf", SaveFormat.Pdf);` nach dem Hinzufügen des Diagramms auf. |
| **Ausführung unter .NET Core** | Stellen Sie sicher, dass Sie das Paket `Aspose.Words.NETCore` referenzieren; die API‑Verwendung ist identisch. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie in eine Konsolenanwendung kopieren‑und‑einfügen können. Es enthält alle Schritte, optionale Größenanpassungen und Kommentare zur Klarheit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Führen Sie das Programm aus, öffnen Sie die resultierende Datei, und Sie sehen das Radar‑Diagramm genau wie beschrieben.

## Fazit

Sie wissen jetzt, wie man ein **Radar‑Diagramm erstellt** und **Diagramme zu Word**‑Dokumenten mit C# **hinzufügt**. Das Tutorial behandelte das Erzeugen eines **leeren Word-Dokuments**, das Einfügen eines Radar‑Diagramms, **die Diagrammgröße in Word festlegen** und das Aktivieren von Achsenunterteilungen. Mit dieser Grundlage können Sie die Lösung auf mehrere Diagramme, benutzerdefinierte Datenreihen oder den Export nach PDF erweitern.

### Nächste Schritte

* Erkunden Sie weitere Diagrammtypen mit `ChartType` (z. B. `Bar`, `Line`) – siehe das Stichwort **add radar chart** für verwandte Beispiele.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Scatter-Diagramm in Word-Dokument einfügen](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Spalten‑Diagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)
- [Diagrammachse in einem Word-Dokument ausblenden](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}