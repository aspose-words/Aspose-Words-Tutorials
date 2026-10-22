---
title: Entfernen einer Diagrammserie aus einem Word Document mit Aspose.Words für .NET
weight: 510
limit:
description: Erfahren Sie, wie Sie eine bestimmte Datenreihe aus einem Säulendiagramm in einem Word Document mit Aspose.Words für .NET löschen.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erfahren Sie, wie Sie eine bestimmte Datenreihe aus einem Säulendiagramm
    in einem Word Document mit Aspose.Words für .NET löschen.
  headline: Entfernen einer Diagrammserie aus einem Word Document mit Aspose.Words
    für .NET
  type: TechArticle
- description: Erfahren Sie, wie Sie eine bestimmte Datenreihe aus einem Säulendiagramm
    in einem Word Document mit Aspose.Words für .NET löschen.
  name: Entfernen einer Diagrammserie aus einem Word Document mit Aspose.Words für
    .NET
  steps:
  - name: Erstellen Sie ein neues Word Document und einen damit verknüpften DocumentBuilder.
    text: Erstellen Sie ein neues Word Document und einen damit verknüpften DocumentBuilder.
  - name: Fügen Sie ein Säulendiagramm mit der Größe 432 × 252 Punkte ein und erhalten
      Sie das Chart-Objekt für weitere Manipulationen.
    text: Fügen Sie ein Säulendiagramm mit der Größe 432 × 252 Punkte ein und erhalten
      Sie das Chart-Objekt für weitere Manipulationen.
  - name: Definieren Sie den nullbasierten Index der zu entfernenden Serie (die zweite
      Serie).
    text: Definieren Sie den nullbasierten Index der zu entfernenden Serie (die zweite
      Serie).
  - name: Ist der Index gültig, rufen Sie RemoveAt auf der Series-Collection des Diagramms
      auf, um diese Serie zu löschen.
    text: Ist der Index gültig, rufen Sie RemoveAt auf der Series-Collection des Diagramms
      auf, um diese Serie zu löschen.
  - name: Speichern Sie das aktualisierte Dokument als .docx-Datei.
    text: Speichern Sie das aktualisierte Dokument als .docx-Datei.
  type: HowTo
- questions:
  - answer: Die `if`-Prüfung (`targetSeriesIdx < columnChart.Series.Count`) schlägt
      fehl, sodass `RemoveAt` nie aufgerufen wird und das Diagramm unverändert bleibt.
    question: Was passiert, wenn ich einen Index übergebe, der gleich der Anzahl der
      Serien im Diagramm ist?
  - answer: Ja, nach `columnChart.Series.RemoveAt` wird die Legende neu erstellt,
      um die verbleibenden Serien widerzuspiegeln, sodass der entfernte Eintrag aus
      der Legende verschwindet.
    question: Wird die Legende des Diagramms automatisch aktualisiert, wenn eine Serie
      entfernt wird?
  - answer: Der Code funktioniert für jeden Diagrammtyp, der eine `Series`-Collection
      unterstützt; ändern Sie einfach beim Einfügen des Diagramms `ChartType.Column`
      in den gewünschten Typ.
    question: Kann ich denselben Code verwenden, um eine Serie aus einem Linien- oder
      Kreisdiagramm zu löschen?
  - answer: Ein Diagramm ohne Serien ist weiterhin ein gültiges `Shape` und wird gespeichert,
      erscheint jedoch im resultierenden Dokument leer.
    question: Wenn ich die einzige Serie in einem Diagramm entferne, wird das Diagramm
      trotzdem korrekt gespeichert?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Eine Diagrammserie in einem Word Document löschen
og_description: Schritt-für-Schritt-Anleitung, um eine Datenreihe aus einem Word-Diagramm mit Aspose.Words für .NET zu entfernen.
og_image_alt: Leitfaden, der zeigt, wie man eine bestimmte Datenreihe aus einem Säulendiagramm in einem Word Document mit Aspose.Words für .NET löscht
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Entfernen einer Diagrammserie aus einem Word Document mit Aspose.Words für .NET
Dieses Tutorial zeigt, wie man ein Word Document erstellt, mit DocumentBuilder ein Säulendiagramm hinzufügt und anschließend eine bestimmte Datenreihe aus diesem Diagramm mit der Methode ChartSeriesCollection.RemoveAt löscht. Am Ende haben Sie ein gespeichertes Dokument, aus dem die unerwünschte Serie entfernt wurde, was Ihnen eine präzise Kontrolle über den Diagramminhalt direkt aus .NET-Code ermöglicht.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Was passiert, wenn ich einen Index übergebe, der gleich der Anzahl der Serien im Diagramm ist?**  
A: Die `if`-Prüfung (`targetSeriesIdx < columnChart.Series.Count`) schlägt fehl, sodass `RemoveAt` nie aufgerufen wird und das Diagramm unverändert bleibt.

**Q: Wird die Legende des Diagramms automatisch aktualisiert, wenn eine Serie entfernt wird?**  
A: Ja, nach `columnChart.Series.RemoveAt` wird die Legende neu erstellt, um die verbleibenden Serien widerzuspiegeln, sodass der entfernte Eintrag aus der Legende verschwindet.

**Q: Kann ich denselben Code verwenden, um eine Serie aus einem Linien- oder Kreisdiagramm zu löschen?**  
A: Der Code funktioniert für jeden Diagrammtyp, der eine `Series`-Collection unterstützt; ändern Sie einfach beim Einfügen des Diagramms `ChartType.Column` in den gewünschten Typ.

**Q: Wenn ich die einzige Serie in einem Diagramm entferne, wird das Diagramm trotzdem korrekt gespeichert?**  
A: Ein Diagramm ohne Serien ist weiterhin ein gültiges `Shape` und wird gespeichert, erscheint jedoch im resultierenden Dokument leer.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}