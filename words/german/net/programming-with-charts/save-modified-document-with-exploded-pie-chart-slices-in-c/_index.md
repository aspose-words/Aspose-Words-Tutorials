---
category: general
date: 2026-10-13
description: 'Speichern Sie das modifizierte Dokument nach der Anpassung eines Kreisdiagramms:
  Segmente herausziehen, den Winkel des ersten Segments ändern und Prozentbeschriftungen
  anzeigen in C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: de
lastmod: 2026-10-13
og_description: Speichern Sie das modifizierte Dokument, nachdem Sie ein Kreisdiagramm
  in C# angepasst haben. Erfahren Sie, wie Sie Kreisdiagramm‑Segmente hervorheben,
  den Winkel des ersten Segments ändern und Prozentbeschriftungen anzeigen.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Speichern eines modifizierten Dokuments mit explodierten Tortendiagramm‑Segmenten
  – C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Modifiziertes Dokument mit herausgelösten Tortendiagramm‑Segmenten in C# speichern
url: /de/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokument mit explodierten Kuchendiagrammsegmenten in C# speichern

Wenn Sie ein **modifiziertes Dokument speichern** nach der Anpassung eines Word‑Kuchendiagramms benötigen, zeigt Ihnen diese Anleitung genau, wie das geht. Sie lernen, Kuchendiagrammsegmente zu explodieren, den Winkel des ersten Segments zu ändern und Prozent‑Beschriftungen anzuzeigen – alles mit wenigen Zeilen C#‑Code.

Das Anpassen von Diagrammen ist eine häufige Anforderung beim programmgesteuerten Erstellen von Berichten, Rechnungen oder Dashboards. Am Ende dieses Tutorials können Sie eine DOCX‑Datei laden, das Aussehen des Diagramms ändern und ein **modifiziertes Dokument speichern**, das bereit für die Verteilung ist.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
- Aspose.Words für .NET 23.10 oder neuer (Kostenlose Testversion oder lizenzierte Kopie)
- Eine Word‑Datei (`input.docx`), die ein einzelnes Kuchendiagramm enthält
- Visual Studio 2022 oder eine beliebige C#‑IDE

> **Hinweis:** Das Aspose.Words‑NuGet‑Paket wird mit `dotnet add package Aspose.Words` hinzugefügt.

## Schritt 1: Laden des Word‑Dokuments, das das Diagramm enthält

Der erste Schritt besteht darin, die Quell‑DOCX‑Datei zu öffnen. Die Klasse `Document` repräsentiert die gesamte Word‑Datei im Speicher.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Das Laden des Dokuments gibt Ihnen vollen Zugriff auf jeden Knoten, einschließlich Formen, die Diagramme enthalten.

## Schritt 2: Das erste Diagramm‑Shape aus dem Dokument abrufen

Diagramme werden in `Shape`‑Knoten gespeichert. Sie können das erste Diagramm mit `GetChild` finden.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Falls das Dokument mehrere Diagramme enthält, passen Sie den Index (`0`) an oder iterieren Sie durch die Sammlung. Diese Zeile stellt sicher, dass Sie eine Referenz auf das `Chart`‑Objekt haben, das Sie ändern werden.

## Schritt 3: Kuchendiagrammsegmente explodieren

Das Explodieren eines Segments trennt es vom Rest des Kuchens, wodurch das Diagramm leichter zu lesen ist. Die Eigenschaft `Explode` wirkt auf die gesamte Serie.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Durch Setzen von `Explode` auf `true` **werden die Kuchendiagrammsegmente** für die gesamte Serie explodiert, was nützlich ist, wenn jedes Segment hervorgehoben werden soll.

## Schritt 4: Winkel des ersten Segments ändern

Manchmal muss das erste Segment bei einem benutzerdefinierten Winkel beginnen, zum Beispiel um einer Design‑Richtlinie zu entsprechen.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

Die Eigenschaft `FirstSliceAngle` **ändert die Ausrichtung des ersten Segments**, indem sie den gesamten Kuchen rotiert, sodass das erste Segment bei 30 Grad beginnt.

## Schritt 5: Prozent‑Beschriftungen auf den Kuchensegmenten anzeigen

Die Anzeige des numerischen Beitrags jedes Segments ist in Berichten häufig erforderlich. Das Flag `DataLabel.ShowPercentage` aktiviert die Prozentwerte.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Dieser Schritt **zeigt Prozent‑Beschriftungen** direkt im Diagramm an, was zudem die Anforderung **Prozentwerte im Kuchendiagramm anzeigen** erfüllt.

## Schritt 6: Das modifizierte Dokument speichern

Nachdem alle Anpassungen vorgenommen wurden, speichern Sie die Änderungen in einer neuen Datei. Die Methode `Save` schreibt das aktualisierte DOCX auf die Festplatte.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Jetzt haben Sie ein **modifiziertes Dokument speichern**, das ein explodiertes Kuchendiagramm, ein rotiertes erstes Segment und sichtbare Prozent‑Beschriftungen enthält.

![Modifiziertes Dokument mit explodiertem Kuchendiagramm](/images/pie-chart-exploded.png "Modifiziertes Dokument mit explodierten Kuchendiagrammsegmenten und Prozent‑Beschriftungen")

*Der Screenshot zeigt das Endergebnis, nachdem das Dokument gespeichert wurde.*

## Vollständiges, ausführbares Beispiel

Die einzelnen Teile zusammengefügt, hier das komplette Programm, das Sie in ein Konsolenprojekt kopieren‑und‑einfügen können:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Erwartetes Ergebnis

Das Öffnen von `output.docx` zeigt ein Kuchendiagramm, bei dem:

- Jedes Segment ist leicht getrennt (**explodierte Kuchendiagrammsegmente**)
- Das erste Segment beginnt mit einem Versatz von 30 Grad (**erstes Segment ändern**)
- Jedes Segment zeigt seinen Beitrag als Prozentsatz (**Prozent‑Beschriftungen anzeigen**, **Prozentwerte im Kuchendiagramm anzeigen**)
- Die Datei wurde **modifiziertes Dokument speichern**, ohne das Original zu verändern.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Was ist, wenn das Dokument kein Diagramm enthält?** | Der Code prüft nach `GetChild` auf `null`. Wenn kein Diagramm vorhanden ist, können Sie entweder programmgesteuert eines hinzufügen oder mit einer klaren Meldung abbrechen. |
| **Kann ich nur ein einzelnes Segment explodieren?** | Ja. Verwenden Sie `chart.PieChart.Series[0].DataPoints[i].Explosion = true;`, wobei `i` der Index des Segments ist. |
| **Wie ändere ich das Beschriftungsformat (z. B. Wert + % anzeigen)?** | Setzen Sie `chart.PieChart.DataLabel.ShowValue = true;` und optional `chart.PieChart.DataLabel.ShowPercentage = true;`, um beides zu kombinieren. |
| **Wird der Diagrammstil nach dem Speichern beibehalten?** | Aspose.Words behält alle Formatierungen, einschließlich Farben und Schriftarten, bei, wenn Sie ein **modifiziertes Dokument speichern**. |
| **Kann ich mehrere Diagramme in derselben Datei verarbeiten?** | Durchlaufen Sie alle `Shape`‑Knoten mit `NodeType.Shape` und filtern Sie nach `shape.HasChart`. Wenden Sie die gleichen Schritte auf jedes Diagramm an. |

## Fazit

Sie wissen jetzt, wie Sie ein **modifiziertes Dokument speichern** können, nachdem Sie ein Kuchendiagramm in Word programmgesteuert angepasst haben. Die Anleitung behandelte das Explodieren von Kuchendiagrammsegmenten, das Ändern des Winkels des ersten Segments und das Anzeigen von Prozent‑Beschriftungen – wodurch die Anforderungen **Prozent‑Beschriftungen anzeigen**, **Kuchendiagrammsegmente explodieren**, **Prozentwerte im Kuchendiagramm anzeigen** und **erstes Segment ändern** erfüllt werden.

Als Nächstes sollten Sie folgendes erkunden:

- Datenreihen dynamisch hinzufügen (`chart.Series.Add(...)`)
- Anpassen der Legendenposition und Diagrammtitel
- Konvertieren des DOCX in PDF bei gleichzeitiger Beibehaltung des Diagramm‑Stils

Experimentieren Sie gern mit verschiedenen Winkeln, Explosions‑Einstellungen oder Beschriftungsformaten, um Ihre Berichtsanforderungen zu erfüllen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in dieser Anleitung gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein bearbeitetes Dokument in C# mit Aspose.Words speichert – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Diagramm‑Seriendaten in einem Word‑Dokument mit Aspose.Words für .NET aktualisieren](/words/english/net/programming-with-charts/modify-chart-series/)
- [Spalten‑Diagramm in ein Word‑Dokument einfügen](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}