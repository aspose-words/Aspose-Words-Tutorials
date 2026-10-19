---
title: Eine benannte Datenreihe zu einem Histogramm‑Diagramm in Word hinzufügen mit Aspose.Words für .NET
weight: 610
limit:
description: Erfahren Sie, wie Sie ein Histogramm‑Diagramm in ein Word-Dokument einbetten und mit Aspose.Words für .NET eine benannte Datenreihe hinzufügen.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erfahren Sie, wie Sie ein Histogramm‑Diagramm in ein Word-Dokument
    einbetten und mit Aspose.Words für .NET eine benannte Datenreihe hinzufügen.
  headline: Eine benannte Datenreihe zu einem Histogramm‑Diagramm in Word hinzufügen
    mit Aspose.Words für .NET
  type: TechArticle
- description: Erfahren Sie, wie Sie ein Histogramm‑Diagramm in ein Word-Dokument
    einbetten und mit Aspose.Words für .NET eine benannte Datenreihe hinzufügen.
  name: Eine benannte Datenreihe zu einem Histogramm‑Diagramm in Word hinzufügen mit
    Aspose.Words für .NET
  steps:
  - name: Erstellen Sie ein neues leeres Word-Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
    text: Erstellen Sie ein neues leeres Word-Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
  - name: Fügen Sie dem Dokument ein Histogramm-Diagramm‑Shape mit der Größe 500×300
      ein und erhalten Sie dessen Chart‑Objekt.
    text: Fügen Sie dem Dokument ein Histogramm-Diagramm‑Shape mit der Größe 500×300
      ein und erhalten Sie dessen Chart‑Objekt.
  - name: Entfernen Sie die standardmäßige Platzhalter‑Reihe, die Aspose.Words zu
      neuen Diagrammen hinzufügt.
    text: Entfernen Sie die standardmäßige Platzhalter‑Reihe, die Aspose.Words zu
      neuen Diagrammen hinzufügt.
  - name: Fügen Sie dem Histogramm‑Diagramm eine benannte Reihe mit dem Namen "Demo
      Series" und den angegebenen Datenpunkten hinzu.
    text: Fügen Sie dem Histogramm‑Diagramm eine benannte Reihe mit dem Namen "Demo
      Series" und den angegebenen Datenpunkten hinzu.
  - name: Speichern Sie das Dokument als .docx‑Datei, die die beschriftete Diagrammreihe
      enthält.
    text: Speichern Sie das Dokument als .docx‑Datei, die die beschriftete Diagrammreihe
      enthält.
  type: HowTo
- questions:
  - answer: '`InsertChart` erstellt eine standardmäßige Platzhalter‑Reihe; das Löschen
      entfernt diese leere Reihe, sodass das Diagramm nur die Daten anzeigt, die Sie
      mit `Series.Add` hinzufügen.'
    question: Warum muss ich `histogramChart.Series.Clear()` aufrufen, bevor ich meine
      eigene Reihe hinzufüge?
  - answer: Ja, rufen Sie `histogramChart.Series.Add` mehrfach auf, jeweils mit einem
      eindeutigen Namen und `double[]`‑Werten; jede Reihe wird in der Diagrammlegende
      mit dem angegebenen Namen aufgeführt.
    question: Kann ich mit derselben Überladung mehr als eine Reihe hinzufügen, und
      wird jede mit ihrer eigenen Beschriftung angezeigt?
  - answer: Die Überladung erwartet ein `double[]`; wenn Sie `int[]` oder andere numerische
      Arrays haben, casten oder konvertieren Sie sie vor dem Übergeben zu `double[]`.
    question: Ist das `double[]`‑Argument der einzige akzeptierte Typ für die Datenpunkte?
  - answer: Der als erstes Argument übergebene String (z. B. "Demo Series") wird als
      Titel der Reihe verwendet und standardmäßig in der Diagrammlegende angezeigt.
    question: Wird der von mir angegebene Reihenname automatisch im Diagramm angezeigt?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Eine benannte Reihe zu einem Word-Histogramm‑Diagramm hinzufügen
og_description: Beschriften Sie schnell eine Diagrammreihe in Word mit Aspose.Words und sehen Sie sie sofort gerendert.
og_image_alt: Screenshot, der ein Word-Dokument mit einem Histogramm‑Diagramm zeigt, das eine mit Aspose.Words für .NET erstellte, beschriftete Datenreihe enthält
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Eine benannte Datenreihe zu einem Histogramm‑Diagramm in Word hinzufügen mit Aspose.Words für .NET
Dieses Tutorial demonstriert, wie man mit Aspose.Words für .NET ein Word-Dokument erstellt, ein Histogramm‑Diagramm einfügt und eine beschriftete Datenreihe hinzufügt, wobei die Überladung ChartSeriesCollection.Add verwendet wird, die einen Namen und Werte akzeptiert. Durch das Benennen der Reihe können Sie jedes Datenset im Diagramm eindeutig identifizieren, wodurch die visuelle Darstellung leichter zu lesen und zu interpretieren ist.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Warum muss ich `histogramChart.Series.Clear()` aufrufen, bevor ich meine eigene Reihe hinzufüge?**  
A: `InsertChart` erstellt eine standardmäßige Platzhalter‑Reihe; das Löschen entfernt diese leere Reihe, sodass das Diagramm nur die Daten anzeigt, die Sie mit `Series.Add` hinzufügen.

**Q: Kann ich mit derselben Überladung mehr als eine Reihe hinzufügen, und wird jede mit ihrer eigenen Beschriftung angezeigt?**  
A: Ja, rufen Sie `histogramChart.Series.Add` mehrfach auf, jeweils mit einem eindeutigen Namen und `double[]`‑Werten; jede Reihe wird in der Diagrammlegende mit dem angegebenen Namen aufgeführt.

**Q: Ist das `double[]`‑Argument der einzige akzeptierte Typ für die Datenpunkte?**  
A: Die Überladung erwartet ein `double[]`; wenn Sie `int[]` oder andere numerische Arrays haben, casten oder konvertieren Sie sie vor dem Übergeben zu `double[]`.

**Q: Wird der von mir angegebene Reihenname automatisch im Diagramm angezeigt?**  
A: Der als erstes Argument übergebene String (z. B. "Demo Series") wird als Titel der Reihe verwendet und standardmäßig in der Diagrammlegende angezeigt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}