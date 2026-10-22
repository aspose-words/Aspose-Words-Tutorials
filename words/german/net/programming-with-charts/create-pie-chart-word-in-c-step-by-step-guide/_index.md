---
category: general
date: 2026-08-07
description: Erstelle schnell ein Kreisdiagramm in C#. Lerne, wie man ein Kreisdiagramm
  einfügt, Datenbeschriftungen zum Kreisdiagramm hinzufügt, Prozentsätze im Diagramm
  anzeigt und die Datenbeschriftungen des Diagramms anpasst.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: de
lastmod: 2026-08-07
og_description: Erstellen Sie ein Kreisdiagramm in Word mit C# und Aspose.Words. Dieses
  Tutorial zeigt, wie man ein Kreisdiagramm einfügt, Datenbeschriftungen hinzufügt
  und ein Prozentdiagramm anzeigt, während die Diagrammbeschriftungen angepasst werden.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Erstelle ein Kreisdiagramm‑Wort in C# – vollständiges Tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Kreisdiagramm in C# erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines Kreisdiagramms in Word mit C# – Schritt‑für‑Schritt‑Anleitung

Wenn Sie **Kreisdiagramme in Word**‑Dokumenten mit C# erstellen müssen, bietet Ihnen diese Anleitung eine vollständige, sofort ausführbare Lösung. Sie erfahren, wie Sie **ein Kreisdiagramm einfügen**, **Datenbeschriftungen für das Kreisdiagramm hinzufügen** und **Prozentwerte im Diagramm anzeigen**, während Sie **Diagrammbeschriftungen anpassen**, um ein professionelles Erscheinungsbild zu erzielen.

Das programmgesteuerte Erzeugen von Diagrammen erspart Ihnen manuelle Nachbearbeitung, insbesondere wenn Berichte oder Dashboards automatisch erstellt werden müssen. In den nachfolgenden Abschnitten lernen Sie alles, was Sie benötigen, um ein vollständig beschriftetes Kreisdiagramm in eine Word‑Datei mit Aspose.Words für .NET einzubetten.

## Voraussetzungen und Einrichtung

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder neuer installiert.  
* Eine gültige Aspose.Words für .NET‑Lizenz (oder einen temporären Evaluierungsschlüssel).  
* Visual Studio 2022 (oder eine beliebige IDE, die C# unterstützt).  

Fügen Sie das Aspose.Words‑NuGet‑Paket zu Ihrem Projekt hinzu:

```bash
dotnet add package Aspose.Words
```

> **Profi‑Tipp:** Wenn Sie viele Diagramme erzeugen wollen, aktivieren Sie den **Free‑Form Drawing**‑Modus (`DocumentBuilder.UseFreeFormDrawing = true`) für bessere Performance.

## Kreisdiagramm in Word mit Aspose.Words erstellen

Der erste wichtige Schritt besteht darin, ein leeres Word‑Dokument und einen `DocumentBuilder` zu erzeugen. Dieses Objekt steuert alle nachfolgenden Einfügungen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist*: `Document` repräsentiert die gesamte `.docx`‑Datei, während `DocumentBuilder` eine fluente API bereitstellt, um Absätze, Tabellen und Diagramme hinzuzufügen. Ein sauberes Dokument zu starten verhindert, dass versteckte Formatierungen das Diagrammlayout beeinträchtigen.

## Kreisdiagramm in das Dokument einfügen

Jetzt platzieren wir ein Kreisdiagramm in der gewünschten Größe. Die Methode `InsertChart` liefert ein `Chart`‑Objekt, das wir weiter konfigurieren können.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Warum das wichtig ist*: Das Flag `ChartType.Pie` weist Aspose.Words an, ein rundes Diagramm zu erzeugen. Breite (`400`) und Höhe (`300`) werden in Punkten angegeben, sodass Sie die visuelle Größe exakt steuern können.

## Das Diagramm mit Daten füllen

Ein Kreisdiagramm benötigt mindestens eine Datenreihe mit numerischen Werten. Hier fügen wir drei Kategorien hinzu: „Apples“, „Bananas“ und „Cherries“.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Warum das wichtig ist*: Jeder Aufruf von `AddCategory` erzeugt ein Segment. Der numerische Wert bestimmt die Segmentgröße, während das Label zum Kategorienamen wird, der angezeigt wird, wenn Datenbeschriftungen aktiviert sind.

## Datenbeschriftungen hinzufügen und Prozentwerte anzeigen

Um das Diagramm informativ zu machen, aktivieren wir Datenbeschriftungen, positionieren sie außerhalb der Segmente und lassen Aspose.Words sowohl den Kategorienamen als auch den Prozentsatz anzeigen.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Warum das wichtig ist*: Das Setzen von `Position` auf `OutsideEnd` verbessert die Lesbarkeit, besonders bei kleinen Segmenten. Das Aktivieren von `ShowCategoryName` und `ShowPercentage` erfüllt die Anforderung **show percentage chart** und deckt das Ziel **add data labels pie** ab.

## Diagrammbeschriftungen weiter anpassen (optional)

Möglicherweise möchten Sie die Schriftart ändern, eine Führungslinie hinzufügen oder die Legende ausblenden. Das folgende Snippet demonstriert gängige Anpassungen:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Warum das wichtig ist*: Das Anpassen des Beschriftungs‑Looks stellt sicher, dass das Diagramm zum Stil‑Guide Ihres Dokuments passt. Das Entfernen der Legende reduziert visuelle Unordnung, wenn Datenbeschriftungen bereits alle nötigen Informationen liefern.

## Dokument mit dem angepassten Diagramm speichern

Abschließend schreiben wir das Dokument auf die Festplatte. Wählen Sie einen Pfad, für den Sie Schreibrechte besitzen.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Wenn Sie `ChartWithCustomLabels.docx` in Microsoft Word öffnen, sehen Sie ein Kreisdiagramm, bei dem jedes Segment mit seinem Kategorienamen und Prozentsatz beschriftet ist, die Beschriftungen außerhalb des Segments positioniert und mit den benutzerdefinierten Schriftarteinstellungen formatiert sind.

### Erwartete Ausgabe

| Segment | Wert | Prozentsatz | Beschriftung in Word |
|---------|------|-------------|----------------------|
| Apples  | 40   | 40 %        | Apples – 40 %        |
| Bananas | 35   | 35 %        | Bananas – 35 %       |
| Cherries| 25   | 25 %        | Cherries – 25 %      |

Das Diagramm sollte ähnlich wie die Abbildung unten aussehen:

![Word‑Dokument, das ein Kreisdiagramm mit Prozentbeschriftungen außerhalb jedes Segments anzeigt](pie-chart-word.png "Create pie chart word example")

*Der Alt‑Text des Bildes enthält das Haupt‑Keyword für SEO.*

## Umgang mit mehreren Datenreihen und Sonderfällen

Das Basisbeispiel verwendet eine einzige Datenreihe, was für ein Kreisdiagramm üblich ist. Wenn Sie mehrere Reihen darstellen wollen (z. B. zum Vergleich zweier Jahre), müssen Sie:

1. `chart.Series.Add()` für jede zusätzliche Reihe aufrufen.  
2. Sicherstellen, dass jede Reihe dieselben Kategorien verwendet; andernfalls wirft Aspose.Words eine `ArgumentException`.  
3. Optional `labels.ShowSeriesName = true` setzen, um die Segmente zu unterscheiden.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Existieren mehrere Reihen, rendert das Diagramm automatisch als **clustered pie** (auch „pie of pies“ genannt). Prüfen Sie die Ausgabe, um sicherzustellen, dass die Beschriftungen lesbar bleiben.

## Häufige Stolperfallen und wie man sie vermeidet

| Problem | Ursache | Lösung |
|---------|---------|--------|
| Beschriftungen überlappen Segmente | Kleiner Diagrammbereich oder viele Kategorien | Diagrammgröße erhöhen (`InsertChart(width, height)`) oder `Position` auf `InsideEnd` umstellen. |
| Prozentsätze ergeben nicht 100 % | Rundungsfehler in den Daten | `labels.ShowPercentage = true` verwenden (Aspose.Words normalisiert automatisch). |
| Diagramm erscheint leer in Word | Fehlende Lizenz oder abgelaufener Evaluierungszeitraum | Vor der Dokumenterstellung eine gültige Aspose.Words‑Lizenz laden. |
| Schriftfarben weichen vom Word‑Theme ab | Benutzerdefinierte Schriftart im Code | Benutzerdefinierte Schriftarteinstellungen entfernen oder Word‑Theme‑Farben verwenden (`System.Drawing.Color.Black`). |

## Vollständiger Quellcode (ausführbar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Beim Ausführen des Programms entsteht `ChartWithCustomLabels.docx`, das ein **create pie chart word**‑Beispiel enthält und alle im Tutorial genannten Anforderungen erfüllt.

## Fazit

Sie wissen jetzt, wie Sie **Kreisdiagramme in Word**‑Dokumenten mit C# und Aspose.Words erstellen. Die Anleitung behandelte das Einfügen eines Kreisdiagramms, **add data labels pie**, **show percentage chart** und das **customize chart data labels**, um eine professionelle, datengetriebene Word‑Datei zu erzeugen.  

Ab hier können Sie verwandte Themen erkunden, etwa **insert pie chart** in bestehende Absätze, das Erzeugen von **bar**‑ oder **line**‑Diagrammen oder die automatisierte Stapelerstellung von Berichten mit variierenden Datensätzen. Experimentieren Sie mit unterschiedlichen Beschriftungspositionen, Schriftstilen und Mehrreihen‑Konfigurationen, um die Ausgabe an Ihre spezifischen Reporting‑Bedürfnisse anzupassen.

Viel Spaß beim Diagramm‑Erstellen!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}