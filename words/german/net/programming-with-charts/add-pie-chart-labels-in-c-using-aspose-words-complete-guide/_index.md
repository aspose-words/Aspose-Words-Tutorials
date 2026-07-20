---
category: general
date: 2026-07-20
description: Fügen Sie Tortendiagramm‑Beschriftungen mit Aspose.Words für .NET hinzu.
  Erfahren Sie, wie Sie Tortendiagramm‑Beschriftungen ändern, Prozentangaben anzeigen
  und Serienbeschriftungen des Diagramms schnell aktualisieren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: de
lastmod: 2026-07-20
og_description: Fügen Sie Kuchendiagramm‑Beschriftungen in C# mit Aspose.Words hinzu.
  Beherrschen Sie das Ändern von Kuchendiagramm‑Beschriftungen, das Anzeigen von Prozentwerten
  und das Aktualisieren von Diagramm‑Serien‑Beschriftungen in nur wenigen Schritten.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Kuchendiagramm‑Beschriftungen in C# hinzufügen – Aspose.Words Vollständiges
  Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Kuchendiagramm‑Beschriftungen in C# mit Aspose.Words hinzufügen – Komplettanleitung
url: /de/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pie‑Diagramm‑Beschriftungen in C# mit Aspose.Words – Vollständige Anleitung

Möchten Sie **pie chart labels** zu einem Word‑Dokument mit C# hinzufügen? Mit Aspose.Words können Sie mühelos **pie chart labels ändern** und **pie chart percentages anzeigen** – direkt in der Datei, ohne manuelles Nachbearbeiten in Word.

In diesem Tutorial führen wir Sie Schritt für Schritt durch die genauen Vorgänge, um **percentage labels** anzuzeigen, sie neu zu positionieren und sogar **chart series labels** für dynamische Daten zu **update**. Am Ende haben Sie ein wiederverwendbares Snippet, das Sie in jedes .NET‑Projekt einbinden können.

> **Schnelle Vorschau:** Nach dem Befolgen der Anleitung zeigt das Öffnen der gespeicherten `.docx`‑Datei ein pie chart, bei dem jedes Segment mit seinem Prozentsatz beschriftet ist und außerhalb des Segments positioniert wird, um maximale Lesbarkeit zu gewährleisten.

---

## Was Sie benötigen

- **Aspose.Words for .NET** (die neueste Version ab 2026). Sie können es von NuGet holen: `Install-Package Aspose.Words`.
- Ein **Word‑Dokument**, das bereits ein pie‑ oder doughnut‑Diagramm enthält (wir nennen es `Chart.docx`).
- Grundlegende Kenntnisse in **C#** und Visual Studio (oder Ihrer bevorzugten IDE).

Das war's – keine zusätzlichen Bibliotheken, kein COM‑Interop, nur reiner Managed‑Code.

---

## Pie‑Diagramm‑Beschriftungen hinzufügen – Vollständige Implementierung

Unten finden Sie ein **komplettes, ausführbares** C#‑Konsolenprogramm, das ein Dokument lädt, das erste pie chart ändert und das Ergebnis speichert. Jede Zeile ist kommentiert, damit Sie verstehen **warum** wir etwas tun, nicht nur **was**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Erwartetes Ergebnis

Öffnen Sie `ChartWithCustomLabels.docx` in Microsoft Word. Sie sollten das pie chart **mit Prozent‑Beschriftungen sehen, die außerhalb jedes Segments positioniert sind**. Die Beschriftungen sehen etwa so aus: „35 %“, „20 %“ usw., wodurch das Diagramm sofort verständlich wird.

---

## Pie‑Diagramm‑Beschriftungen ändern: Positionierung und Formatierung

Wenn Sie nur **pie chart labels ändern** möchten, ohne Prozentsätze anzuzeigen, können Sie die `Position`‑Eigenschaft auf einen der folgenden Werte einstellen:

| Position Enum | Visual Effect |
|---------------|---------------|
| `InsideEnd`   | Labels befinden sich innerhalb des Segments, direkt am Rand. |
| `Center`      | Labels erscheinen in der Mitte des Segments (gut für kleine pies). |
| `OutsideEnd`  | Labels befinden sich außerhalb des Segments, verbunden mit einer Führungslinie (Standard). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Pro‑Tipp:** `OutsideEnd` funktioniert am besten, wenn das Diagramm viele Segmente hat; es verhindert überlappenden Text.

---

## Prozent‑Beschriftungen in einem pie chart anzeigen

Die Eigenschaft `ShowPercentage` ist ein **boolesches Flag**. Wird sie auf `true` gesetzt, weist Aspose.Words an, den Beitrag jedes Segments basierend auf der zugrunde liegenden Datenquelle zu berechnen.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Sie können es auch mit `ShowValue` kombinieren, wenn Sie sowohl Rohzahlen **als auch** Prozentsätze benötigen:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Wenn beide Flags aktiviert sind, sieht die Beschriftung so aus: „45 % (120)“.

---

## Diagramm‑Serien‑Beschriftungen für dynamische Daten aktualisieren

Oft erzeugen Sie Diagramme zur Laufzeit – denken Sie an monatliche Verkaufszahlen oder Umfrageergebnisse. Um **chart series labels** programmgesteuert zu **update**, ändern Sie die `Series`‑Sammlung, bevor Sie die Datenbeschriftungen anpassen:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Dieses Snippet zeigt, wie Sie **chart series labels** für jede Serie aktualisieren können, nicht nur für die erste. Es ist praktisch, wenn Sie Berichte erstellen, die Ist‑ und Prognosedaten kombinieren.

---

## Randfälle & häufige Stolperfallen

| Situation | Worauf zu achten ist | Lösung |
|-----------|----------------------|--------|
| **Diagramm ist kein pie/doughnut** | `Position` hat möglicherweise keine visuelle Auswirkung. | Stellen Sie sicher, dass `chart.Type` `ChartType.Pie` oder `ChartType.Doughnut` ist. |
| **No chart found** | `GetChild` gibt `null` zurück. | Fügen Sie eine Guard‑Clause hinzu (siehe Code) und protokollieren Sie eine hilfreiche Meldung. |
| **Ältere Word‑Version** | Einige Beschriftungs‑Features werden ignoriert. | Speichern Sie als `.docx` (das moderne Format), um vollständige Unterstützung zu gewährleisten. |
| **Viele Segmente** | Beschriftungen können selbst bei `OutsideEnd` überlappen. | Erwägen Sie, die Segmentzahl zu reduzieren oder die Diagrammgröße zu erhöhen. |

---

## Vollständiges funktionierendes Beispiel (Copy‑Paste)

Unten finden Sie das **gesamte Programm**, das Sie in ein neues Konsolenprojekt kopieren können. Ersetzen Sie einfach `YOUR_DIRECTORY` durch den Ordner, der `Chart.docx` enthält.



## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Standardoptionen für Datenbeschriftungen in einem Diagramm festlegen](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Einzelne Diagrammserie in einem Diagramm anpassen](/words/english/net/programming-with-charts/single-chart-series/)
- [Spalten‑Diagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}