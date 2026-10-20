---
category: general
date: 2026-07-19
description: Kuchendiagrammsegment mit Aspose.Words für C# aufteilen. Erfahren Sie,
  wie Sie ein Kuchensegment explodieren, die Größe des Donut‑Lochs anpassen und Diagrammdatenpunkte
  schnell ändern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: de
lastmod: 2026-07-19
og_description: Kuchendiagramm‑Segment mit Aspose.Words für C# explodieren. Dieser
  Leitfaden zeigt Ihnen, wie Sie ein Kuchensegment explodieren, die Größe des Donut‑Lochs
  anpassen und Diagrammdatenpunkte effizient ändern.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Kreisdiagramm‑Segment in C# explodieren – Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Kuchendiagramm‑Segment in C# mit Aspose.Words explodieren – Vollständige Anleitung
url: /de/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kuchendiagrammsegment in C# mit Aspose.Words explodieren – Vollständige Anleitung

Haben Sie sich jemals gefragt, wie man **Kuchendiagrammsegment explodieren** in einem Word-Dokument mit C#? Sie sind nicht allein. Ob Sie eine Vertriebspräsentation vorbereiten oder Umfrageergebnisse visualisieren, ein explodiertes Segment kann die Aufmerksamkeit genau dorthin lenken, wo Sie sie haben möchten. In diesem Tutorial führen wir Sie durch den gesamten Prozess – Laden eines Dokuments, Abrufen des Diagramms, Explodieren des ersten Segments, Anpassen eines Doughnut‑Lochs und sogar Ändern von Diagrammdatenpunkten.

Wir werden außerdem die sekundären Konzepte einstreuen, nach denen Sie vielleicht suchen: **wie man ein Kuchendiagrammsegment explodiert**, **Doughnut‑Lochgröße anpassen** und **Diagrammdatenpunkte ändern**. Kein Schnickschnack, nur eine vollständige, copy‑paste‑bereite Lösung.

---

## Was Sie benötigen

- **Aspose.Words for .NET** (die neueste Version vom 2026‑07‑19). Sie können es von NuGet mit `Install-Package Aspose.Words` beziehen.
- Ein **.NET 6+**‑Projekt (oder .NET Framework 4.7.2+, falls Sie noch Legacy verwenden).
- Eine Word‑Datei (`Chart.docx`), die bereits ein Kuchendiagramm oder Doughnut‑Diagramm enthält. Falls Sie keine haben, erstellen Sie schnell ein Diagramm in Word und speichern Sie es.

Das war's – keine zusätzlichen Bibliotheken, kein COM‑Interop, nur reiner Managed‑Code.

## Kuchendiagrammsegment explodieren – Schritt‑für‑Schritt‑Implementierung

Im Folgenden zerlegen wir die Aufgabe in kleine Schritte. Jeder Abschnitt hat eine klare Überschrift, einen Code‑Snippet und eine kurze Erklärung, *warum* wir das tun, was wir tun.

### Schritt 1: Aspose.Words installieren und referenzieren

Zuerst fügen Sie das Aspose.Words‑Paket zu Ihrem Projekt hinzu. In der Package‑Manager‑Konsole:

```powershell
Install-Package Aspose.Words
```

> **Pro‑Tipp:** Wenn Sie die integrierte NuGet‑UI von Visual Studio verwenden, suchen Sie nach „Aspose.Words“ und klicken Sie auf Installieren. So erhalten Sie die neuesten Fehlerbehebungen und die Möglichkeit, sofort mit Diagrammen zu arbeiten.

### Schritt 2: Das Word‑Dokument mit dem Diagramm laden

Wir benötigen ein `Document`‑Objekt, das auf die `.docx`‑Datei mit dem Diagramm zeigt, das Sie ändern möchten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Warum das wichtig ist:** `Document` ist der Einstiegspunkt für jede Operation in Aspose.Words. Durch das frühe Prüfen auf Diagramme vermeiden wir später eine Null‑Referenz, wenn wir versuchen, ein Segment zu explodieren.

### Schritt 3: Den ersten Diagrammknoten abrufen

Die meisten Beispiele gehen von einem einzigen Diagramm aus, daher holen wir das erste. Haben Sie mehrere Diagramme, passen Sie den Index entsprechend an.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Hinweis:** Der Cast zu `Chart` ist sicher, nachdem wir bestätigt haben, dass ein Diagramm existiert. Dieses Objekt gibt uns Zugriff auf Serien, Datenpunkte und diagrammspezifische Einstellungen.

### Schritt 4: Das erste Segment eines Kuchendiagramms explodieren

Jetzt der Star der Show—**wie man ein Kuchendiagrammsegment explodiert**. Wir setzen die `Exploded`‑Eigenschaft des ersten Datenpunkts.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Warum das funktioniert:** `Exploded` weist Word an, dieses Segment vom Zentrum wegzuziehen und so den klassischen „explodierten Kuchen“‑Effekt zu erzeugen. Die Eigenschaft ist ein Bool, daher bewirkt das Setzen auf `true` das gewünschte Ergebnis.

### Schritt 5: Doughnut‑Lochgröße anpassen (falls es ein Doughnut‑Diagramm ist)

Falls Ihr Diagramm ein Doughnut ist, möchten Sie vielleicht die **Doughnut‑Lochgröße anpassen**. Die Lochgröße ist ein Prozentsatz des Diagrammradius.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Was die Zahl bedeutet:** Ein Wert von `30` bedeutet, dass der innere Kreis 30 % des Gesamtradius einnimmt, wodurch ein dickerer äußerer Ring entsteht.

### Schritt 6: Diagrammdatenpunkte ändern (optional)

Manchmal müssen Sie **Diagrammdatenpunkte ändern** – vielleicht haben Sie die zugrunde liegenden Zahlen aktualisiert und möchten, dass die Visualisierung das widerspiegelt.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Warum Sie das tun:** Das Ändern des Werts eines Datenpunkts berechnet automatisch die Prozentsätze der Segmente neu und hält das Diagramm ohne manuelle Bearbeitung in Word korrekt.

### Schritt 7: Das geänderte Dokument speichern

Zum Schluss schreiben Sie die Änderungen zurück auf die Festplatte. Sie können die Originaldatei überschreiben oder eine neue Datei erstellen – ganz nach Belieben.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Tipp:** Verwenden Sie `SaveFormat.Docx`, wenn Sie es explizit angeben wollen, aber `Save(string)` erkennt das Format automatisch anhand der Dateierweiterung.

## Erwartetes Ergebnis

Wenn Sie `FormattedChart.docx` in Microsoft Word öffnen, sollten Sie sehen:

- Das erste Segment eines Kuchendiagramms **nach außen explodiert**.
- Wenn das Diagramm ein Doughnut ist, nimmt das zentrale Loch jetzt **30 %** des Radius ein.
- Alle geänderten Datenpunkte spiegeln die von Ihnen gesetzten neuen Werte wider.

Unten sehen Sie eine schematische Darstellung, wie das explodierte Segment aussieht (nur zur Veranschaulichung).

![Explodiertes Kuchendiagrammsegment erstellt mit Aspose.Words in C#](exploded-pie-slice.png)

*Alt‑Text:* **explodiertes Kuchendiagrammsegment** zeigt ein herausgezogenes Segment in einem Word‑Dokument.

## Häufige Fragen & Sonderfälle

**Was ist, wenn das Diagramm kein Kuchendiagramm oder Doughnut ist?**  
Der Code prüft `ChartType`, bevor `Exploded` oder `HoleSize` angewendet werden. Bei Balken‑, Linien‑ oder Flächendiagrammen existieren diese Eigenschaften einfach nicht, sodass die Logik sie sicher überspringt.

**Kann ich mehrere Segmente explodieren?**  
Natürlich. Durchlaufen Sie `chart.PieChartData.Series[0].DataPoints` und setzen Sie `Exploded = true` für jeden gewünschten Index.

**Muss ich mir Sorgen um kulturspezifische Zahlenformate machen?**  
Aspose.Words speichert numerische Werte als Double, unabhängig vom Gebietsschema, sodass Sie keine Probleme mit Kommas vs. Punkten haben.

**Wie sieht es mit Diagrammen aus, die in Kopf‑ oder Fußzeilen eingebettet sind?**  
Verwenden Sie `doc.GetChildNodes(NodeType.Chart, true)`, um alle Diagramme abzurufen, und prüfen Sie dann den `ParentNode` jedes Knotens, um zu sehen, wo es sich befindet. Die gleiche Explode‑Logik gilt.

## Fazit

Sie haben jetzt eine solide, copy‑paste‑bereite Lösung, wie man **Kuchendiagrammsegment explodiert** mit Aspose.Words in C#. Wir haben den gesamten Workflow abgedeckt – vom Laden des Dokuments, Abrufen des Diagramms, Explodieren des Segments, **Anpassen der Doughnut‑Lochgröße**, bis zum **Ändern von Diagrammdatenpunkten** und schließlich dem Speichern der Datei.

Probieren Sie es aus: explodieren Sie ein anderes Segment, ändern Sie die Lochgröße auf 45 %, oder aktualisieren Sie mehrere Datenpunkte gleichzeitig. Die Aspose.Words‑API macht diese Anpassungen mühelos, und die Änderungen erscheinen sofort, wenn Sie die Word‑Datei öffnen.

### Was kommt als Nächstes?

- **Explodiertes Segment formatieren** (Füllfarbe, Rand ändern oder ein Datenetikett hinzufügen). Suchen Sie nach „Aspose.Words chart formatting“.
- **Batch‑Verarbeitung automatisieren** mehrerer Dokumente – durchlaufen Sie einen Ordner, explodieren Sie Segmente und speichern Sie neue Versionen.
- **Kombinieren Sie mit Aspose.Slides**, falls Sie dasselbe Diagramm in einer PowerPoint‑Präsentation benötigen.

Haben Sie weitere Fragen zur Diagrammbearbeitung oder möchten Sie tiefer in andere Diagrammtypen einsteigen? Hinterlassen Sie einen Kommentar unten, und viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Spaltendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)
- [Einfaches Spaltendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Flächendiagramm in Word‑Dokument einfügen | Aspose.Words für .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}