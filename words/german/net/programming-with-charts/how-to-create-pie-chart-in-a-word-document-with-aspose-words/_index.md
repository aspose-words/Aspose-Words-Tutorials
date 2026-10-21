---
category: general
date: 2026-09-21
description: Erfahren Sie, wie Sie ein Kreisdiagramm erstellen und ein Diagramm mit
  Aspose.Words in Word einfügen, Datenbeschriftungen zum Kreisdiagramm hinzufügen
  und Prozentsätze im Kreisdiagramm anzeigen – in nur wenigen Schritten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: de
lastmod: 2026-09-21
og_description: Erstellen Sie ein Kreisdiagramm in Word mit Aspose.Words, fügen Sie
  das Diagramm in Word ein, fügen Sie Datenbeschriftungen zum Kreisdiagramm hinzu
  und zeigen Sie Prozentsätze im Kreisdiagramm an – alles mit klaren Codebeispielen.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Erstellen Sie ein Kreisdiagramm in Word mit Aspose.Words – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Wie man ein Kreisdiagramm in einem Word‑Dokument mit Aspose.Words erstellt
url: /de/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Kreisdiagramm in einem Word-Dokument mit Aspose.Words erstellt

Wenn Sie programmgesteuert **ein Kreisdiagramm erstellen** müssen, macht Aspose.Words das einfach. In diesem Tutorial sehen Sie, wie Sie **ein Diagramm in Word einfügen**, die Serie konfigurieren, **Datenbeschriftungen zum Kreisdiagramm hinzufügen** und schließlich **Prozentsätze im Kreisdiagramm anzeigen**, sodass die Visualisierung genaue Werte vermittelt. Am Ende haben Sie ein vollständiges, ausführbares Beispiel, das Sie in jedes .NET‑Projekt einbinden können.

Dieser Leitfaden deckt alles ab, was Sie wissen müssen: erforderliche NuGet‑Pakete, den vollständigen C#‑Quellcode, Erklärungen, warum jeder API‑Aufruf wichtig ist, und Tipps zur Anpassung des Diagramms. Keine externe Dokumentation ist nötig – einfach kopieren, ausführen und anpassen.

## Voraussetzungen

* .NET 6.0 SDK oder höher installiert.  
* Visual Studio 2022 (oder jede IDE, die .NET unterstützt).  
* Eine Aspose.Words für .NET‑Lizenz (die kostenlose Testversion funktioniert zum Testen).  
* Grundlegende Kenntnisse in C# und Word‑Dokumentstrukturen.

Wenn Sie diese bereits haben, können Sie direkt zum Code springen.

## Schritt 1: Projekt einrichten und Aspose.Words importieren

Erstellen Sie ein neues Konsolenprojekt und fügen Sie das Aspose.Words‑NuGet‑Paket hinzu:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Das Paket enthält den Namespace `Aspose.Words.Drawing.Charts`, der die Klassen `Chart` und `ChartSeries` bereitstellt, die wir verwenden werden.

> **Pro‑Tipp:** Bewahren Sie Ihre Lizenzdatei (`Aspose.Words.lic`) im Projektstammverzeichnis auf und laden Sie sie beim Start, um Evaluationswasserzeichen zu vermeiden.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Schritt 2: Ein leeres Dokument und einen DocumentBuilder erstellen

Ein `Document` repräsentiert die Word‑Datei, während `DocumentBuilder` eine fluente API zum Einfügen von Inhalten bereitstellt.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:** Der `DocumentBuilder` behält den aktuellen Einfügepunkt bei, sodass das Diagramm genau dort erscheint, wo Sie es im Dokumentenfluss haben möchten.

## Schritt 3: Ein Kreisdiagramm in das Word‑Dokument einfügen

Jetzt **fügen wir ein Diagramm in Word ein**. Die Methode `InsertChart` nimmt den Diagrammtyp, die Breite und die Höhe (in Punkten) entgegen.

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Zu diesem Zeitpunkt enthält das Diagramm eine Standard‑Datenserie mit Platzhalterwerten (25, 25, 25, 25). Sie können diese bei Bedarf später ersetzen.

## Schritt 4: Auf die erste Serie zugreifen und Datenbeschriftungen anpassen

Ein Kreisdiagramm hat typischerweise eine einzige Serie. Um **Datenbeschriftungen zum Kreisdiagramm hinzuzufügen**, rufen wir sie ab und aktivieren die Prozentanzeige.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Warum wir `ShowPercentage` setzen:** Dieses Flag weist Aspose.Words an, den Beitrag jedes Segments zu berechnen und als Prozentsatz darzustellen. Die Eigenschaft `Position` sorgt dafür, dass die Beschriftung das Segment nicht überlappt, was die Lesbarkeit verbessert – besonders bei kleinen Segmenten.

## Schritt 5: (Optional) Platzhalterdaten ersetzen

Wenn Sie bestimmte Werte benötigen, ersetzen Sie die Standard‑Punkte:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Die angezeigten Prozentsätze passen sich automatisch an die neuen Werte an.

## Schritt 6: Dokument speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Die Dateierweiterung bestimmt das Format; `.docx` erzeugt eine moderne Word‑Datei.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Das Ausführen des Programms erzeugt eine Datei namens **PieChart.docx** im Ausgabeverzeichnis. Beim Öffnen in Microsoft Word wird ein Kreisdiagramm angezeigt, bei dem jedes Segment mit seinem Prozentsatz beschriftet ist, wobei die Beschriftungen außerhalb der Segmente positioniert sind.

### Erwartete Ausgabe

Wenn Sie das erzeugte Dokument öffnen, sollten Sie sehen:

* Ein einzelnes Kreisdiagramm, 400 × 300 pt groß.  
* Vier Segmente (oder so viele Punkte, wie Sie hinzugefügt haben).  
* Prozent‑Beschriftungen wie „40 %“, „30 %“ usw., die außerhalb jedes Segments angezeigt werden.

Wenn die Beschriftungen innerhalb der Segmente erscheinen, überprüfen Sie, ob `ChartDataLabelPosition.OutsideEnd` korrekt gesetzt wurde.

## Schritt 7: Häufige Variationen und Sonderfälle

### Einen Titel zum Diagramm hinzufügen

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Segmentfarben ändern

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Umgang mit einer leeren Serie

Falls Ihre Datenquelle leer sein könnte, schützen Sie sich vor `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exportieren nach PDF statt nach Word

Die gleiche Diagramm‑Render‑Logik gilt; Aspose.Words konvertiert das Word‑Layout automatisch nach PDF.

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

## Vollständige Quellcode‑Auflistung

Unten finden Sie das vollständige, sofort ausführbare Programm. Kopieren Sie es in `Program.cs` und führen Sie `dotnet run` aus.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Fazit

Sie wissen jetzt, wie man mit Aspose.Words ein **Kreisdiagramm** in einer Word‑Datei **erstellt**, **ein Diagramm in Word einfügt**, **Datenbeschriftungen zum Kreisdiagramm hinzufügt** und **Prozentsätze im Kreisdiagramm anzeigt**. Das Beispiel demonstriert den gesamten Arbeitsablauf – von der Projekteinrichtung bis zum fertigen Dokument – sodass Sie es für Dashboards, Berichte oder die automatisierte Rechnungserstellung anpassen können.

Als Nächstes können Sie verwandte Themen erkunden, wie **Prozentsätze in Diagramm‑Legenden anzeigen**, Diagrammfarben anpassen oder das Word‑Dokument zur Verteilung nach PDF konvertieren. Experimentieren Sie mit verschiedenen Diagrammtypen (Balken, Linie) mithilfe der gleichen `InsertChart`‑Methode, um Ihre Automatisierungsfähigkeiten zu erweitern.

Viel Spaß beim Erstellen von Diagrammen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Spaltendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)
- [Word‑Scatter‑Diagramm mit Aspose.Words für .NET erstellen](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Flächendiagramm in ein Word‑Dokument einfügen | Aspose.Words für .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}