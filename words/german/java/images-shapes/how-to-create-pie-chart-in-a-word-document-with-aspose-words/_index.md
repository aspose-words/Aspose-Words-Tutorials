---
category: general
date: 2026-10-20
description: Erstellen Sie ein Kreisdiagramm in einem Word‑Dokument mit Aspose.Words
  – Schritt‑für‑Schritt‑Anleitung, die zeigt, wie man die Farbe festlegt, ein Segment
  hervorhebt und das Word‑Dokument speichert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: de
lastmod: 2026-10-20
og_description: Erstellen Sie ein Kreisdiagramm in einem Word‑Dokument mit Aspose.Words.
  Erfahren Sie, wie Sie die Farbe festlegen, ein Segment hervorheben und das Word‑Dokument
  in einem einzigen, ausführbaren Beispiel speichern.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Erstelle ein Kreisdiagramm in einem Word‑Dokument – vollständige C#‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Wie man ein Kreisdiagramm in einem Word‑Dokument mit Aspose.Words erstellt
url: /de/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Kreisdiagramm in einem Word‑Dokument mit Aspose.Words erstellt

Wenn Sie ein **Kreisdiagramm** in einer Word‑Datei **erstellen** müssen, zeigt Ihnen diese Anleitung genau, wie das geht. Sie sehen, wie Sie eine benutzerdefinierte Farbe festlegen, ein Segment zur Hervorhebung „explodieren“ und schließlich das **Word‑Dokument** mit dem eingebetteten Diagramm **speichern**.

Das programmgesteuerte Erzeugen von Diagrammen eliminiert die manuellen Schritte, Word zu öffnen, ein Diagramm einzufügen und dessen Aussehen anzupassen. Am Ende dieses Tutorials besitzen Sie eine vollständige, ausführbare C#‑Konsolenanwendung, die ein Kreisdiagramm erstellt, anpasst und das Ergebnis auf die Festplatte schreibt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder neuer installiert  
* Eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder einen kostenlosen Evaluierungsschlüssel)  
* Eine IDE wie Visual Studio 2022 oder VS Code  

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Wie man ein Kreisdiagramm in einem Word‑Dokument erstellt

Der erste Schritt besteht darin, ein `Document` und einen `DocumentBuilder` zu instanziieren. Der Builder gibt Ihnen Zugriff auf hoch‑level Word‑Funktionen, einschließlich des Einfügens von Diagrammen.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

An diesem Punkt enthält das Dokument bereits ein einfaches Kreisdiagramm. Die nächsten Abschnitte erklären **wie man ein Segment explodiert**, **wie man die Farbe festlegt** und **wie man das Word‑Dokument speichert**.

## Wie man ein Segment zur Hervorhebung explodiert

Das Explodieren eines Segments trennt es vom Rest des Kreises und lenkt so die Aufmerksamkeit des Lesers. Die Aspose.Words‑API lässt Sie einen Explosionsabstand in Punkten angeben.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Warum das Segment explodieren? In Berichten, die eine bestimmte Kategorie hervorheben – z. B. „Bestverkauftes Produkt“ – sorgt die visuelle Trennung dafür, dass der Datenpunkt sofort erkennbar ist.

## Wie man die Farbe eines Diagrammsegments festlegt

Benutzerdefinierte Farben verbessern Marken‑Konsistenz und Lesbarkeit. Sie können jedem einzelnen Datenpunkt ein beliebiges `System.Drawing.Color` zuweisen.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Sie sind nicht auf vordefinierte Farben beschränkt; Sie können einen `Color.FromArgb`‑Wert für präzise Farbtöne erzeugen.

## Wie man das Word‑Dokument mit dem Diagramm speichert

Sobald das Diagramm so aussieht, wie Sie es wünschen, ist das Persistieren der Datei unkompliziert. Die Methode `Document.Save` schreibt das Dokument in dem von Ihnen angegebenen Format – hier verwenden wir das Standard‑`.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Das Ausführen des Programms erzeugt `PieChart.docx`. Öffnet man die Datei in Microsoft Word, sieht man ein Kreisdiagramm, bei dem das erste Segment explodiert und rot gefärbt ist, genau wie im Code angegeben.

### Erwartetes Ergebnis

* Eine Word‑Datei namens **PieChart.docx** in `C:\Temp`.  
* Das Dokument enthält ein einzelnes Kreisdiagramm mit einer Größe von 400 × 300 Punkten.  
* Segment 0 ist um 20 Punkte versetzt und rot gefüllt, während die anderen Segmente die Standardfarbe behalten.  

Sie können die Explosion und die Farbe überprüfen, indem Sie das Diagramm in Word auswählen und die Segment‑Eigenschaften inspizieren.

## Profi‑Tipps und häufige Fallstricke

* **Pro‑Tipp:** Wenn Sie den Diagrammtitel oder die Legende ändern müssen, verwenden Sie die Eigenschaften `pieChart.Title.Text` und `pieChart.Legend` vor dem Speichern.  
* **Achten Sie darauf:** Das Vergessen, die Standard‑Datenpunkte zu löschen, kann zu zusätzlichen, unerwünschten Segmenten führen. Rufen Sie stets `Series[0].DataPoints.Clear()` auf, bevor Sie Ihre eigenen Daten hinzufügen.  
* **Performance‑Tipp:** Bei großen Dokumenten sollten Sie eine einzelne `DocumentBuilder`‑Instanz wiederverwenden, anstatt viele Builder zu erzeugen; das reduziert den Speicherverbrauch.

## Wie man ein Diagramm mit Aspose.Words erstellt (zusätzlicher Kontext)

Die Methode `InsertChart` unterstützt viele Diagrammtypen neben Kreisdiagrammen, wie Säulen‑, Linien‑ und Flächendiagramme. Um zu einem anderen Typ zu wechseln, ersetzen Sie `ChartType.Pie` durch den gewünschten Enum‑Wert, z. B. `ChartType.Column`. Die übrigen Anpassungsschritte (Explodieren von Segmenten, Festlegen von Farben) folgen demselben Muster, obwohl nicht alle Diagrammtypen eine „Explosion“-Eigenschaft bereitstellen.

## Wie man ein Segment in anderen Diagrammtypen explodiert

Nur Kreis‑Diagramme besitzen die Methode `SetExplosion`. Wenn Sie sie bei einem Balkendiagramm aufrufen, wirft die API eine `ArgumentException`. In solchen Fällen sollten Sie Datenbeschriftungen oder Callouts verwenden, um einen bestimmten Balken hervorzuheben.

## Wie man die Farbe einer Serie statt eines einzelnen Segments festlegt

Wenn Sie möchten, dass alle Segmente einer Serie dieselbe Farbe haben, iterieren Sie über die Datenpunkte:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Dieser Ansatz ist praktisch, wenn Sie ein einheitliches Farbschema über mehrere Diagramme hinweg benötigen.

## Wie man das Word‑Dokument in anderen Formaten speichert

Aspose.Words kann in PDF, HTML und viele weitere Formate exportieren. Ändern Sie die Dateierweiterung in `Save` und übergeben Sie optional ein `SaveOptions`‑Objekt:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Die Diagramm‑Render‑Engine konvertiert das Diagramm automatisch in das Zielformat und behält Farben sowie Explosions‑Einstellungen bei.

## Fazit

Sie wissen jetzt, wie man ein **Kreisdiagramm** in einem Word‑Dokument **erstellt**, sein Aussehen durch **Explodieren eines Segments** und **Festlegen von Farben** anpasst und schließlich das **Word‑Dokument** mit dem eingebetteten Diagramm **speichert**. Dieses End‑to‑End‑Beispiel bietet Ihnen eine solide Grundlage für die Automatisierung von Berichtserstellung, Dashboards oder jeder Situation, in der visuelle Daten programmgesteuert eingefügt werden müssen.

### Nächste Schritte

* Erkunden Sie weitere Diagrammtypen (`ChartType.Column`, `ChartType.Line`), um Ihr Reporting‑Toolkit zu erweitern.  
* Kombinieren Sie mehrere Diagramme in einem einzigen Dokument, um umfassende Dashboards zu erstellen.  
* Experimentieren Sie mit `ChartDataLabel`, um Prozentsätze oder Werte direkt auf den Segmenten anzuzeigen.  

Passen Sie den Code gern an Ihre eigenen Datenquellen an – egal, ob Sie Werte aus einer Datenbank, einer API oder einer CSV‑Datei ziehen, derselbe Aspose.Words‑Workflow gilt. Viel Spaß beim Diagrammerstellen!

### Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}