---
title: Sekundäre Y‑Achse in einem Word‑Diagramm als Währung formatieren mit Aspose.Words for .NET
weight: 710
limit:
description: Erfahren Sie, wie Sie einer Word‑Liniendiagramm eine sekundäre Y‑Achse hinzufügen und sie als Währung formatieren mit Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erfahren Sie, wie Sie einer Word‑Liniendiagramm eine sekundäre Y‑Achse
    hinzufügen und sie als Währung formatieren mit Aspose.Words for .NET.
  headline: Sekundäre Y‑Achse in einem Word‑Diagramm als Währung formatieren mit Aspose.Words
    for .NET
  type: TechArticle
- description: Erfahren Sie, wie Sie einer Word‑Liniendiagramm eine sekundäre Y‑Achse
    hinzufügen und sie als Währung formatieren mit Aspose.Words for .NET.
  name: Sekundäre Y‑Achse in einem Word‑Diagramm als Währung formatieren mit Aspose.Words
    for .NET
  steps:
  - name: Erstellen Sie ein neues leeres Word‑Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
    text: Erstellen Sie ein neues leeres Word‑Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
  - name: Fügen Sie ein Liniendiagramm mit der Größe 450 × 250 Punkte in das Dokument
      ein und erhalten Sie das zugehörige Chart‑Objekt.
    text: Fügen Sie ein Liniendiagramm mit der Größe 450 × 250 Punkte in das Dokument
      ein und erhalten Sie das zugehörige Chart‑Objekt.
  - name: Entfernen Sie die standardmäßige Platzhalter‑Serie, die Aspose einem neuen
      Diagramm hinzufügt.
    text: Entfernen Sie die standardmäßige Platzhalter‑Serie, die Aspose einem neuen
      Diagramm hinzufügt.
  - name: Definieren Sie Quartals‑Beschriftungen und fügen Sie dem Diagramm eine primäre
      Datenreihe mit Beispielwerten hinzu.
    text: Definieren Sie Quartals‑Beschriftungen und fügen Sie dem Diagramm eine primäre
      Datenreihe mit Beispielwerten hinzu.
  - name: Erstellen Sie eine sekundäre Seriengruppe vom Typ Line und weisen Sie sie
      der sekundären Achsengruppe zu.
    text: Erstellen Sie eine sekundäre Seriengruppe vom Typ Line und weisen Sie sie
      der sekundären Achsengruppe zu.
  - name: Blenden Sie die sekundäre X‑Achse aus, sodass nur die sekundäre Y‑Achse
      sichtbar ist.
    text: Blenden Sie die sekundäre X‑Achse aus, sodass nur die sekundäre Y‑Achse
      sichtbar ist.
  - name: Zeigen Sie den Titel der sekundären Y‑Achse an und setzen Sie den Text auf
      "Sales (USD)".
    text: Zeigen Sie den Titel der sekundären Y‑Achse an und setzen Sie den Text auf
      "Sales (USD)".
  - name: Setzen Sie das Zahlenformat der sekundären Y‑Achse auf ein Währungsmuster
      mit zwei Dezimalstellen und lösen Sie die Verknüpfung mit der Quellformatierung.
    text: Setzen Sie das Zahlenformat der sekundären Y‑Achse auf ein Währungsmuster
      mit zwei Dezimalstellen und lösen Sie die Verknüpfung mit der Quellformatierung.
  - name: Fügen Sie der sekundären Gruppe eine Hilfsserie hinzu, die Daten liefert,
      die gegen die sekundäre Y‑Achse geplottet werden.
    text: Fügen Sie der sekundären Gruppe eine Hilfsserie hinzu, die Daten liefert,
      die gegen die sekundäre Y‑Achse geplottet werden.
  - name: Speichern Sie das fertige Dokument unter dem Dateinamen ProfitChart.docx
      im aktuellen Verzeichnis.
    text: Speichern Sie das fertige Dokument unter dem Dateinamen ProfitChart.docx
      im aktuellen Verzeichnis.
  type: HowTo
- questions:
  - answer: Das Diagramm behält die standardmäßige Platzhalter‑Serie, die Aspose.Words
      einfügt, bei, sodass Ihre benutzerdefinierte "Main Series" neben unerwünschten
      Datenpunkten erscheint.
    question: Was passiert, wenn ich den Aufruf `lineChart.Series.Clear()` weglasse?
  - answer: Setzen Sie `secondarySeriesGroup.AxisX.Hidden = false;` (oder lassen Sie
      einfach die Zeile weg, die sie auf `true` setzt).
    question: Wie kann ich die sekundäre X‑Achse anzeigen, anstatt sie auszublenden?
  - answer: Ja – ändern Sie die Formatzeichenfolge, z. B. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";` für Euro oder passen Sie das Muster an Ihre Locale an.
    question: Kann ich ein anderes Währungssymbol oder Format für die sekundäre Y‑Achse
      verwenden?
  - answer: Wenn `IsLinkedToSource` true ist, erbt die Achse das Zahlenformat aus
      der zugrunde liegenden Datenquelle, wodurch jedes benutzerdefinierte `FormatCode`
      überschrieben wird; das Setzen auf false zwingt das Diagramm, das von Ihnen
      angegebene Format zu verwenden.
    question: Warum muss ich `IsLinkedToSource = false` setzen, wenn ich ein benutzerdefiniertes
      Zahlenformat anwende?
  - answer: Ja, weisen Sie `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      zu (oder `Right` für die Vorgabe), um zu steuern, auf welcher Seite die Achse
      gezeichnet wird.
    question: Ist es möglich, die sekundäre Y‑Achse auf die linke Seite des Diagramms
      zu verschieben?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Die sekundäre Achse eines Diagramms als Währung formatieren
og_description: Erfahren Sie, wie Sie einem Word‑Liniendiagramm eine sekundäre Y‑Achse hinzufügen und sie mit zwei Dezimalstellen als Währung formatieren.
og_image_alt: Screenshot, der ein Word‑Liniendiagramm mit einer als Währung formatierten sekundären Y‑Achse zeigt, erstellt mit Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sekundäre Y‑Achse in einem Word‑Diagramm als Währung formatieren mit Aspose.Words
In diesem Tutorial sehen Sie, wie Sie ein Word‑Dokument erstellen, ein Liniendiagramm einfügen, eine sekundäre Y‑Achse hinzufügen, diese Achse als Währung mit zwei Dezimalstellen formatieren und eine sekundäre Datenreihe daran binden, wobei Aspose.Words for .NET verwendet wird. Das Formatieren der sekundären Achse als Währung ermöglicht es, Finanzdaten klar neben der primären Reihe darzustellen. Folgen Sie dem Schritt‑für‑Schritt‑Code, um das Diagramm direkt im erzeugten Dokument zu sehen.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Was passiert, wenn ich den Aufruf `lineChart.Series.Clear()` weglasse?**  
A: Das Diagramm behält die standardmäßige Platzhalter‑Serie, die Aspose.Words einfügt, bei, sodass Ihre benutzerdefinierte "Main Series" neben unerwünschten Datenpunkten erscheint.

**Q: Wie kann ich die sekundäre X‑Achse anzeigen, anstatt sie auszublenden?**  
A: Setzen Sie `secondarySeriesGroup.AxisX.Hidden = false;` (oder lassen Sie einfach die Zeile weg, die sie auf `true` setzt).

**Q: Kann ich ein anderes Währungssymbol oder Format für die sekundäre Y‑Achse verwenden?**  
A: Ja – ändern Sie die Formatzeichenfolge, z. B. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";` für Euro oder passen Sie das Muster an Ihre Locale an.

**Q: Warum muss ich `IsLinkedToSource = false` setzen, wenn ich ein benutzerdefiniertes Zahlenformat anwende?**  
A: Wenn `IsLinkedToSource` true ist, erbt die Achse das Zahlenformat aus der zugrunde liegenden Datenquelle, wodurch jedes benutzerdefinierte `FormatCode` überschrieben wird; das Setzen auf false zwingt das Diagramm, das von Ihnen angegebene Format zu verwenden.

**Q: Ist es möglich, die sekundäre Y‑Achse auf die linke Seite des Diagramms zu verschieben?**  
A: Ja, weisen Sie `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` zu (oder `Right` für die Vorgabe), um zu steuern, auf welcher Seite die Achse gezeichnet wird.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}