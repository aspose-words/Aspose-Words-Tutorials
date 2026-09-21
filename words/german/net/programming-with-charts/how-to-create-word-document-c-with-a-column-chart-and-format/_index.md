---
category: general
date: 2026-09-21
description: Erfahren Sie, wie Sie in C# ein Word‑Dokument erstellen, ein Säulendiagramm
  einfügen, die Beschriftungsposition festlegen und Werte anzeigen – mit Aspose.Words
  in einer Schritt‑für‑Schritt‑Anleitung.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: de
lastmod: 2026-09-21
og_description: Erstellen Sie ein Word-Dokument in C# mit Aspose.Words. Dieses Tutorial
  zeigt, wie man ein Säulendiagramm einfügt, die Beschriftungsposition festlegt und
  Werte anzeigt.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Word-Dokument in C# erstellen – Spaltendiagramm einfügen, Beschriftung setzen,
  Werte anzeigen
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Wie man ein Word‑Dokument in C# mit einem Säulendiagramm und formatierten Beschriftungen
  erstellt
url: /de/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word‑Dokument C# mit einem Säulendiagramm und formatierten Beschriftungen erstellt

Wenn Sie **Word‑Dokument C# erstellen** müssen, das ein Diagramm enthält, zeigt Ihnen dieser Leitfaden genau, wie Sie es tun. Sie lernen, wie Sie ein **Säulendiagramm** einfügen, dessen Datenbeschriftung positionieren und die Werte der Beschriftung anzeigen – alles mit Aspose.Words für .NET.

Das Erzeugen einer diagrammfähigen Word‑Datei erforderte früher manuelle Arbeit in Microsoft Word. Mit den **wie man ein Diagramm einfügt**‑Schritten, die hier beschrieben werden, können Sie den gesamten Prozess aus dem Code heraus automatisieren, wodurch die Berichtserstellung schnell und wiederholbar wird. Das Tutorial behandelt außerdem **wie man Beschriftungen festlegt** und **wie man Werte anzeigt**, sodass das Diagramm für Endbenutzer bereit ist.

Am Ende dieses Artikels haben Sie ein vollständiges, ausführbares C#‑Programm, das eine `.docx`‑Datei erstellt, die ein Säulendiagramm enthält, dessen Datenbeschriftungen innerhalb jeder Säule erscheinen und ihre numerischen Werte anzeigen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder später installiert  
* Eine lizenzierte Kopie von **Aspose.Words for .NET** (die kostenlose Testversion funktioniert zum Testen)  
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code  

Zusätzliche NuGet‑Pakete sind über `Aspose.Words` hinaus nicht erforderlich.

## Schritt 1: Projekt einrichten und Aspose.Words hinzufügen

Erstellen Sie ein neues Konsolenprojekt und fügen Sie das Aspose.Words‑Paket hinzu:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Der Befehl `dotnet add package` holt die neueste stabile Version von **Aspose.Words**, die die Diagramm‑API enthält, die im **insert column chart word**‑Beispiel verwendet wird.

## Schritt 2: Neues leeres Word‑Dokument erstellen

Der erste Codeabschnitt erstellt ein leeres Dokument und einen `DocumentBuilder`, mit dem Sie Inhalte einfügen können. Dies ist die Grundlage für **Word‑Dokument C# erstellen**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` repräsentiert die gesamte `.docx`‑Datei, während `DocumentBuilder` Methoden wie `InsertParagraph`, `InsertImage` und, für dieses Tutorial entscheidend, `InsertChart` bereitstellt.

## Schritt 3: Säulendiagramm einfügen (wie man ein Diagramm einfügt)

Jetzt fügen wir ein **column chart** ein. Die Methode `InsertChart` erwartet den Diagrammtyp, die Breite und die Höhe in Punkten.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

Zu diesem Zeitpunkt enthält das Diagramm eine Standard‑Datenreihe mit Platzhalterwerten. Sie können die Reihen‑Daten ersetzen, wenn Sie benutzerdefinierte Zahlen benötigen, aber für die Demonstration von **wie man Beschriftungen festlegt** und **wie man Werte anzeigt** reichen die Standarddaten aus.

## Schritt 4: Datenbeschriftung innerhalb jeder Säule positionieren (wie man Beschriftungen festlegt)

Datenbeschriftungen sind die Texte, die auf jeder Säule erscheinen. Um das Diagramm leichter lesbar zu machen, verschieben wir die Beschriftung in die Säule und aktivieren ihren numerischen Wert.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` platziert die Beschriftung oben in der Säule, bleibt jedoch innerhalb der Form der Säule – ein gängiger visueller Stil für Berichte. Das Setzen von `ShowValue` auf `true` erfüllt die Anforderung **wie man Werte anzeigt**.

## Schritt 5: Dokument speichern

Schließlich schreiben wir das Dokument auf die Festplatte. Die Datei kann mit Microsoft Word, LibreOffice oder jedem Viewer geöffnet werden, der das Open‑XML‑Format unterstützt.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Das Ausführen des Programms erzeugt `output.docx`, das ein Säulendiagramm mit Datenbeschriftungen enthält, die innerhalb jeder Säule positioniert sind und ihre Werte anzeigen.

### Erwartetes Ergebnis

Wenn Sie `output.docx` öffnen, sollten Sie ein einzelnes Säulendiagramm sehen, das dem Bild unten ähnelt. Jede Säule hat eine numerische Beschriftung an ihrer Oberseite, innerhalb der Säule, die den Reihenwert anzeigt.

![Diagramm in einem mit C# erstellten Word‑Dokument](/images/word-chart-example.png "Diagramm in einem mit C# erstellten Word‑Dokument – create word document C#")

*Alt‑Text:* *Diagramm in einem mit C# erstellten Word‑Dokument, das zeigt, wie man ein Spaltendiagramm in Word einfügt und Werte anzeigt.*

## Häufige Variationen und Randfälle

### Benutzerdefinierte Daten zum Diagramm hinzufügen

Wenn Sie die Platzhalterdaten ersetzen müssen, können Sie die `Series`‑Sammlung des Diagramms ändern:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Schriftart und Farbe der Beschriftung ändern

Sie können das Aussehen der Beschriftung weiter anpassen:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Mehrere Diagramme einfügen

Der `DocumentBuilder` kann so viele Diagramme einfügen, wie Sie benötigen. Rufen Sie einfach erneut `InsertChart` auf, nachdem Sie den Cursor mit `builder.Writeln()` oder `builder.InsertParagraph()` verschoben haben.

## Pro‑Tipps

* **Pro‑Tipp:** Setzen Sie `chart.HasTitle = true` und weisen Sie `chart.Title.Text` zu, um dem Diagramm eine beschreibende Überschrift zu geben. Das verbessert die Barrierefreiheit für Screen‑Reader.
* **Achten Sie darauf:** Beim Speichern auf einem Netzwerk‑Share muss die Anwendung Schreibrechte besitzen; andernfalls wirft `doc.Save` eine `UnauthorizedAccessException`.
* **Performance‑Tipp:** Verwenden Sie eine einzige `DocumentBuilder`‑Instanz für mehrere Einfügungen; das Erzeugen eines neuen Builders für jede Operation verursacht unnötigen Overhead.

## Fazit

Sie wissen jetzt, wie Sie **Word‑Dokument C# erstellen** können, das ein Säulendiagramm enthält, wie Sie **Diagramm‑Elemente einfügen**, **Beschriftungspositionen festlegen** und **Werte** innerhalb jeder Säule **anzeigen**. Das komplette Codebeispiel oben ist bereit zum Ausführen, und Sie können es mit benutzerdefinierten Daten, Styling oder zusätzlichen Diagrammen erweitern.

Als Nächstes können Sie verwandte Themen wie **wie man ein Bild einfügt**, **wie man Tabellen erzeugt** oder **wie man Dokument‑Themes anwendet** erkunden, um Ihre automatisierten Berichte noch umfangreicher zu gestalten. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Spaltendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)
- [Einfaches Spaltendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Flächendiagramm in Word‑Dokument einfügen | Aspose.Words für .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}