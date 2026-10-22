---
category: general
date: 2026-08-04
description: Benutzerdefinierte Platzierung von Datenbeschriftungen für Diagramme
  in C# ermöglicht das Zentrieren von Beschriftungen auf Diagrammsegmenten. Folgen
  Sie dieser Schritt‑für‑Schritt‑Anleitung mit der Aspose.Words‑Diagramm‑API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: de
lastmod: 2026-08-04
og_description: Benutzerdefinierte Datenbeschriftungsplatzierung für Diagramme in
  C# zeigt Ihnen, wie Sie alle Datenbeschriftungen auf jedem Abschnitt eines Word‑Diagramms
  zentrieren. Beherrschen Sie die Positionierung von Diagrammdatenbeschriftungen mit
  Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Benutzerdefinierte Datenbeschriftungsplatzierung für Diagramme in C# – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Benutzerdefinierte Platzierung von Datenbeschriftungen für Diagramme in C#
url: /de/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Benutzerdefinierte Daten‑Label‑Platzierung für Diagramme in C#

**Custom Data‑Label Placement for Charts** ermöglicht es Ihnen, genau zu steuern, wo jede Beschriftung in einem Diagramm in einem Word‑Dokument erscheint. In diesem Tutorial lernen Sie, wie Sie alle Daten‑Labels jeder Scheibe zentrieren, indem Sie C# und die Aspose.Words‑Diagramm‑API verwenden.

Sie erhalten ein vollständiges, ausführbares Beispiel, das eine `.docx`‑Datei lädt, die erste Diagramm‑Shape zugreift, die `Position` jeder Beschriftung auf `Center` ändert und das aktualisierte Dokument speichert. Es sind keine externen Referenzen erforderlich – nur die Aspose.Words für .NET‑Bibliothek und eine grundlegende C#‑Entwicklungsumgebung.

**What you’ll learn**

* Wie man ein Word‑Dokument lädt, das ein Diagramm enthält.  
* Wie man die Diagramm‑Shape mit der Aspose.Words‑Diagramm‑API findet.  
* Wie man **chart data label positioning** auf jede Serie im Diagramm anwendet.  
* Wie man das Dokument speichert, damit die zentrierten Beschriftungen in Word angezeigt werden.  

**Prerequisites**

* .NET 6.0 (oder neuer) installiert.  
* Visual Studio 2022 (oder jede C#‑IDE).  
* Ein Verweis auf das `Aspose.Words`‑NuGet‑Paket.  
* Eine Word‑Datei (`Chart.docx`), die mindestens ein Diagramm enthält.

---

## Benutzerdefinierte Daten‑Label‑Platzierung für Diagramme – Schritt 1: Dokument laden

Der erste Schritt besteht darin, die Word‑Datei zu öffnen, die das Diagramm enthält. `Document` ist der Einstiegspunkt für jede Manipulation mit Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Warum dieser Schritt wichtig ist*: Ohne das Laden des Dokuments können Sie nicht auf das Diagramm‑Objekt zugreifen. Die Validierung stellt sicher, dass Sie einen klaren Fehler erhalten, wenn die Datei kein Diagramm enthält, und verhindert später eine Null‑Referenz.

---

## Verwendung der Aspose.Words‑Diagramm‑API zum Zugriff auf Diagramm‑Shapes

Aspose.Words behandelt ein Diagramm als ein `Chart`‑Objekt, das in einem `Shape` verschachtelt ist. Sie erhalten es, indem Sie den entsprechenden Kindknoten casten.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Warum dieser Schritt wichtig ist*: Der direkte Zugriff auf `Chart` gibt Ihnen die volle Kontrolle über Serien, Datenpunkte und Beschriftungseigenschaften. Wenn das Shape kein Diagramm ist, bricht der Code früh mit einer informativen Meldung ab.

---

## Festlegen der Diagrammdaten‑Label‑Position in C#

Iterieren Sie nun über jede Serie und jede Daten‑Label und setzen Sie die `Position` auf `Center`. Dies ist der Kern von **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Profi‑Tipp**: Wenn Sie eine andere Platzierung benötigen (z. B. `InsideEnd` für ein Säulendiagramm), ändern Sie den Enum‑Wert entsprechend. Das Enum `ChartDataLabelPosition` deckt alle von Word unterstützten Standardpositionen ab.

*Warum dieser Schritt wichtig ist*: Das Ändern von `label.Position` aktualisiert die zugrunde liegende OOXML‑Darstellung, sodass die Beschriftung zentriert erscheint, wenn das Dokument in Microsoft Word geöffnet wird.

---

## Speichern des Word‑Dokuments mit aktualisierten Beschriftungen

Nachdem das Diagramm geändert wurde, speichern Sie die Änderungen in einer Datei. Sie können das Original überschreiben oder eine neue Kopie erstellen.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Warum dieser Schritt wichtig ist*: Beim Speichern wird das aktualisierte OOXML auf die Festplatte geschrieben. Das Öffnen von `ChartLabelsCentered.docx` in Word zeigt jede Scheibenbeschriftung zentriert an und bestätigt, dass **Custom Data‑Label Placement for Charts** erfolgreich war.

---

## Sonderfälle und Variationen

| Situation | Wie zu handhaben |
|-----------|-------------------|
| **Mehrere Diagramme** im selben Dokument | Schleife über `doc.GetChildNodes(NodeType.Shape, true)` und prüfe `shape.HasChart` für jedes Shape. |
| **Verschiedene Diagrammtypen** (Kreis, Donut, Balken) | Das gleiche `ChartDataLabelPosition.Center` funktioniert für Kreis‑Diagramme. Für Balken‑/Säulen‑Diagramme bevorzugen Sie möglicherweise `InsideEnd` oder `OutsideEnd`. |
| **Beschriftungstext benötigt Formatierung** | Greifen Sie auf `label.TextProperties` zu, um Schriftgröße, Farbe oder Fettformatierung festzulegen. |
| **Ausführung auf .NET Core** | Stellen Sie sicher, dass Sie die .NET‑Standard‑Version von Aspose.Words referenzieren; die API ist identisch. |

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige Programm, das Sie in eine Konsolenanwendung kopieren‑und‑einfügen können. Es enthält alle erforderlichen `using`‑Direktiven und die Fehlerbehandlung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Erwartetes Ergebnis**: Öffnen Sie `ChartLabelsCentered.docx` in Microsoft Word. Jede Scheibe des Diagramms zeigt jetzt ihre Daten‑Label direkt in der Mitte der Scheibe an, was ein saubereres Erscheinungsbild liefert.

---

## Fazit

Sie haben nun eine vollständige **Custom Data‑Label Placement for Charts**‑Lösung in C#. Durch das Laden des Dokuments, den Zugriff auf das Diagramm über die Aspose.Words‑Diagramm‑API, das Setzen von `ChartDataLabelPosition.Center` für jede Beschriftung und das Speichern der Datei können Sie die Beschriftungsposition für jedes Word‑Diagramm automatisieren.

Als Nächstes erkunden Sie weitere **chart data label positioning**‑Optionen wie `InsideEnd` oder `OutsideEnd` oder experimentieren mit **C# chart manipulation**, um Farben zu ändern, Legenden hinzuzufügen oder Diagramme von Grund auf zu erzeugen. Diese Erweiterungen bauen direkt auf den hier behandelten Techniken auf und erweitern Ihre Fähigkeiten zur Automatisierung von Word‑Diagrammen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Diagrammdatenbeschriftung anpassen](/words/english/net/programming-with-charts/chart-data-label/)
- [Zahl der Datenbeschriftungen in einem Diagramm formatieren](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Diagrammdatenbeschriftung](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}