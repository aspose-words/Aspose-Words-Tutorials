---
category: general
date: 2026-10-13
description: Erfahren Sie, wie Sie Diagrammbeschriftungen in einem Word‑Dokument programmgesteuert
  mit C# anpassen. Dieser Leitfaden behandelt die Diagrammbearbeitung mit Aspose.Words
  und die Ausrichtung von Beschriftungen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: de
lastmod: 2026-10-13
og_description: Passen Sie Diagrammbeschriftungen in einem Word-Dokument programmgesteuert
  mit C# an. Folgen Sie diesem umfassenden Tutorial, um die Platzierung, Ausrichtung
  und weitere Einstellungen der Beschriftungen zu ändern.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Diagrammbeschriftungen in Word programmgesteuert anpassen – Schritt‑für‑Schritt‑Anleitung
  in C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Diagrammbeschriftungen in einem Word‑Dokument programmgesteuert mit C# anpassen
url: /de/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diagrammbeschriftungen in einem Word‑Dokument programmgesteuert anpassen mit C#

Wenn Sie **Diagrammbeschriftungen programmgesteuert anpassen** müssen, zeigt Ihnen dieser Leitfaden genau, wie das mit C# funktioniert. Egal, ob Sie Berichte generieren, Dashboards automatisieren oder Vorlagen anpassen – Sie erhalten ein vollständiges, ausführbares Beispiel, das die Position und Ausrichtung einer Diagrammbeschriftung in einer .docx‑Datei ändert.

Sie lernen außerdem, wie Sie **Aspose.Words‑Diagrammbearbeitung** einsetzen, mehrere Serien handhaben und typische Stolperfallen bei **C#‑Diagrammdatenbeschriftungs**‑Objekten vermeiden.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 (oder neuer) installiert  
* Visual Studio 2022 (oder eine beliebige C#‑IDE)  
* Das **Aspose.Words for .NET**‑NuGet‑Paket (`Install-Package Aspose.Words`)  
* Ein Word‑Dokument (`input.docx`), das mindestens ein Diagramm enthält  

Diese Elemente werden für das **Word‑Dokument‑Diagramm‑Beispiel** benötigt, das wir ändern werden.

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie ein neues Konsolenprojekt und fügen Sie die erforderlichen `using`‑Direktiven hinzu. Damit wird die Umgebung für das **programmgesteuerte Anpassen von Diagrammbeschriftungen** vorbereitet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Warum dieser Schritt?*  
Durch das Laden des Dokuments erhalten Sie Zugriff auf den internen **Word‑Dokument‑Diagramm‑Beispiel**‑Baum, in dem Diagramme als Shape‑Knoten gespeichert sind.

## Schritt 2: Das erste Diagramm‑Shape finden

Diagramme werden als `Shape`‑Knoten gespeichert. Der folgende Code ruft das erste Diagramm im Dokument ab, das Ziel für unsere Beschriftungsanpassungen.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Warum dieser Schritt?*  
Die Methode `GetChild` durchsucht rekursiv (`true`) und gibt den ersten Knoten vom Typ `Shape` zurück. Durch das Casten zu `Chart` können wir die diagrammspezifische API nutzen.

## Schritt 3: Auf die zu ändernde Datenbeschriftung zugreifen

Jede Serie in einem Diagramm besitzt eine Sammlung von Datenbeschriftungen. Für ein einfaches Diagramm reicht häufig die erste Beschriftung aus. Der nachfolgende Code zeigt, wie Sie darauf zugreifen.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Warum dieser Schritt?*  
`ChartSeries` repräsentiert eine Serie von Punkten. `DataLabelCollection` enthält die Beschriftungen dieser Serie und ermöglicht eine präzise Steuerung von Position und Ausrichtung.

## Schritt 4: Position und Ausrichtung der Beschriftung ändern

Jetzt **passen wir Diagrammbeschriftungen programmgesteuert an**, indem wir Position, horizontale Ausrichtung und vertikale Ausrichtung setzen. Diese Eigenschaften entsprechen den Optionen, die Sie in der Word‑Benutzeroberfläche sehen.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Warum diese Einstellungen?*  

* `OutsideEnd` positioniert die Beschriftung direkt außerhalb des Endes jeder Säule oder Spalte und verbessert die Lesbarkeit.  
* `HorizontalAlignment.Center` zentriert den Text über dem Punkt, während `VerticalAlignment.Top` die Oberkante der Beschriftung mit dem Datenpunkt ausrichtet und ein Überlappen mit anderen Elementen verhindert.

### Profi‑Tipp
Hat ein Diagramm mehrere Serien, iterieren Sie über `chart.Series` und wenden dieselben Einstellungen auf jede `DataLabelCollection` an. So erhalten Sie ein einheitliches Erscheinungsbild im gesamten Diagramm.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Schritt 5: Das geänderte Dokument speichern

Nachdem Sie die Beschriftungen angepasst haben, speichern Sie die Änderungen in einer neuen Datei. Damit ist der **Prozess zum Ändern der Diagrammbeschriftungsposition** abgeschlossen.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Wenn Sie `output.docx` öffnen, sehen Sie, dass jede Diagrammbeschriftung an das äußere Ende ihres Datenpunkts verschoben, horizontal zentriert und vertikal nach oben ausgerichtet ist.

## Sonderfälle und Varianten

| Situation | Worauf zu achten ist | Empfohlener Ansatz |
|-----------|----------------------|--------------------|
| **Mehrere Diagramme** im selben Dokument | `GetChild` liefert nur das erste Diagramm. | Verwenden Sie `doc.GetChildNodes(NodeType.Shape, true)`, um über alle Diagramm‑Shapes zu iterieren. |
| **Serien ohne Datenbeschriftungen** | `DataLabelCollection` kann leer sein. | Prüfen Sie `series.HasDataLabels`, bevor Sie auf die Sammlung zugreifen. |
| **Verschiedene Diagrammtypen** (Kreis, Linie, Streudiagramm) | Nicht alle Werte von `DataLabelPosition` sind gültig. | Nutzen Sie `DataLabelPosition.Auto` für Diagramme, die die optimale Platzierung selbst bestimmen. |
| **Lokalisierung** | Ausrichtungskonstanten sind sprachunabhängig, aber der gerenderte Text benötigt ggf. Rechts‑nach‑Links‑Unterstützung. | Setzen Sie `dataLabel.TextDirection`, wenn Sie RTL‑Sprachen benötigen. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie kopieren, einfügen und ausführen können. Ersetzen Sie `YOUR_DIRECTORY` durch einen tatsächlichen Ordnerpfad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erwartetes Ergebnis:** Beim Öffnen von `output.docx` ist jede Diagrammbeschriftung außerhalb des Datenpunkts positioniert, horizontal zentriert und vertikal nach oben ausgerichtet – genau die Wirkung des **programmgesteuerten Anpassens von Diagrammbeschriftungen**, die Sie implementiert haben.

## Fazit

Sie wissen nun, wie Sie **Diagrammbeschriftungen programmgesteuert in einem Word‑Dokument mit C# anpassen** können. Das Tutorial behandelte:

* Laden eines Dokuments mit **Aspose.Words‑Diagrammbearbeitung**  
* Zugriff auf eine **C#‑Diagrammdatenbeschriftung**  
* Ändern der **Diagrammbeschriftungsposition** und Ausrichtung  
* Speichern der Datei und Umgang mit gängigen Sonderfällen  

Ab hier können Sie weiterführende Szenarien erkunden, etwa das Anpassen von Beschriftungs‑Schriftarten, das Hinzufügen bedingter Formatierungen oder das Aktualisieren mehrerer Diagramme in einem Batch‑Prozess. Experimentieren Sie mit den verschiedenen `DataLabelPosition`‑Optionen, um den Stil zu finden, der am besten zu Ihren Berichten passt.

---

*Bereit, Ihre automatisierte Reporting‑Pipeline zu verbessern? Versuchen Sie, benutzerdefinierte Zahlenformate zu den Beschriftungen hinzuzufügen oder das Diagramm als Bild zu exportieren, um es in PDFs zu verwenden.*


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}