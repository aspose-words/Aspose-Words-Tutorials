---
title: Benutzerdefiniertes Säulendiagramm in Word‑Dokument einfügen mit Aspose.Words für .NET
weight: 310
limit:
description: Erstellen Sie eine Word‑Datei, fügen Sie ein Säulendiagramm ein, ersetzen Sie dessen Daten durch ein benutzerdefiniertes Array, fügen Sie einen Titel hinzu und speichern Sie – alles mit Aspose.Words für .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erstellen Sie eine Word‑Datei, fügen Sie ein Säulendiagramm ein, ersetzen
    Sie dessen Daten durch ein benutzerdefiniertes Array, fügen Sie einen Titel hinzu
    und speichern Sie – alles mit Aspose.Words für .NET.
  headline: Benutzerdefiniertes Säulendiagramm in Word‑Dokument einfügen mit Aspose.Words
    für .NET
  type: TechArticle
- description: Erstellen Sie eine Word‑Datei, fügen Sie ein Säulendiagramm ein, ersetzen
    Sie dessen Daten durch ein benutzerdefiniertes Array, fügen Sie einen Titel hinzu
    und speichern Sie – alles mit Aspose.Words für .NET.
  name: Benutzerdefiniertes Säulendiagramm in Word‑Dokument einfügen mit Aspose.Words
    für .NET
  steps:
  - name: Erstellen Sie ein neues Document und einen daran angehängten DocumentBuilder.
    text: Erstellen Sie ein neues Document und einen daran angehängten DocumentBuilder.
  - name: Fügen Sie ein Säulendiagramm mit der Größe 432 × 252 Punkte in das Dokument
      ein und erhalten Sie das zugehörige Chart‑Objekt.
    text: Fügen Sie ein Säulendiagramm mit der Größe 432 × 252 Punkte in das Dokument
      ein und erhalten Sie das zugehörige Chart‑Objekt.
  - name: Entfernen Sie die automatisch erzeugte Beispielserie aus dem Diagramm.
    text: Entfernen Sie die automatisch erzeugte Beispielserie aus dem Diagramm.
  - name: Definieren Sie die Kategorienbeschriftungen der X‑Achse und die Legendeinträge
      für jede Serie.
    text: Definieren Sie die Kategorienbeschriftungen der X‑Achse und die Legendeinträge
      für jede Serie.
  - name: Erstellen Sie ein zweidimensionales Array, bei dem jede Zeile die Werte
      einer Serie enthält.
    text: Erstellen Sie ein zweidimensionales Array, bei dem jede Zeile die Werte
      einer Serie enthält.
  - name: Iterieren Sie über jede Serie, extrahieren Sie die Zeilenwerte aus der Matrix
      und fügen Sie die Serie dem Diagramm mit dem entsprechenden Legendeintrag und
      den X‑Achsen‑Beschriftungen hinzu.
    text: Iterieren Sie über jede Serie, extrahieren Sie die Zeilenwerte aus der Matrix
      und fügen Sie die Serie dem Diagramm mit dem entsprechenden Legendeintrag und
      den X‑Achsen‑Beschriftungen hinzu.
  - name: Setzen Sie den Diagrammtitel auf 'Half‑Yearly Revenue' und machen Sie ihn
      sichtbar.
    text: Setzen Sie den Diagrammtitel auf 'Half‑Yearly Revenue' und machen Sie ihn
      sichtbar.
  - name: Speichern Sie das Dokument, das das benutzerdefinierte Diagramm enthält,
      als .docx‑Datei.
    text: Speichern Sie das Dokument, das das benutzerdefinierte Diagramm enthält,
      als .docx‑Datei.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` erwartet, dass die Länge des Werte‑Arrays der Anzahl
      der X‑Achsen‑Beschriftungen entspricht, und Sie müssen pro Legendeintrag genau
      eine Serie hinzufügen; ein Mismatch löst zur Laufzeit eine `ArgumentException`
      aus.'
    question: Was passiert, wenn die Zeilen oder Spalten in `dataMatrix` nicht mit
      den Längen von `legendEntries` bzw. `xLabels` übereinstimmen?
  - answer: Ja – ersetzen Sie `ChartType.Column` in `docBuilder.InsertChart` durch
      einen anderen `ChartType` (z. B. `ChartType.Line`), und die nachfolgenden `Series.Add`‑Aufrufe
      füllen das neue Diagramm auf dieselbe Weise.
    question: Kann ich einen anderen Diagrammtyp, z. B. ein Liniendiagramm, mit derselben
      Daten‑Populationslogik verwenden?
  - answer: Passen Sie die Eigenschaften `Width` und `Height` des von `InsertChart`
      zurückgegebenen `Shape` an (z. B. `chartContainer.Width = 500; chartContainer.Height
      = 300;`).
    question: Wie ändere ich die Größe des Diagramms, nachdem es eingefügt wurde?
  - answer: Setzen Sie `chartObj.Series[i].HasDataLabel = true;` für jede Serie nach
      dem Hinzufügen, oder iterieren Sie über `chartObj.Series` und aktivieren Sie
      `HasDataLabel`, um die Werte im Diagramm anzuzeigen.
    question: Gibt es eine schnelle Möglichkeit, Datenbeschriftungen für jede Säule
      des Diagramms anzuzeigen?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Ein benutzerdefiniertes Säulendiagramm zu einem Word‑Dokument hinzufügen
og_description: Ersetzen Sie die Standarddaten eines Diagramms durch Ihr eigenes Array und setzen Sie in Sekundenschnelle einen Titel.
og_image_alt: Screenshot, der ein Word‑Dokument mit einem benutzerdefinierten Säulendiagramm zeigt, erstellt mit Aspose.Words für .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Benutzerdefiniertes Säulendiagramm in Word‑Dokument einfügen mit Aspose.Words für .NET
Dieses Tutorial führt Sie Schritt für Schritt durch das Erstellen eines Word‑Dokuments, das Einfügen eines Säulendiagramms, das Löschen der Standarddaten und das Befüllen des Diagramms mit benutzerdefinierten Werten aus einem zweidimensionalen Array – wobei jede Zeile einer Serie und jede Spalte einer Kategorie zugeordnet wird. Außerdem erfahren Sie, wie Sie vor dem Speichern des Dokuments einen Diagrammtitel hinzufügen. Folgen Sie den Schritten, um ein vollständig angepasstes Diagramm direkt in Ihrer Word‑Datei zu erzeugen.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Was passiert, wenn die Zeilen oder Spalten in `dataMatrix` nicht mit den Längen von `legendEntries` bzw. `xLabels` übereinstimmen?**  
A: `Chart.Series.Add` erwartet, dass die Länge des Werte‑Arrays der Anzahl der X‑Achsen‑Beschriftungen entspricht, und Sie müssen pro Legendeintrag genau eine Serie hinzufügen; ein Mismatch löst zur Laufzeit eine `ArgumentException` aus.

**Q: Kann ich einen anderen Diagrammtyp, z. B. ein Liniendiagramm, mit derselben Daten‑Populationslogik verwenden?**  
A: Ja – ersetzen Sie `ChartType.Column` in `docBuilder.InsertChart` durch einen anderen `ChartType` (z. B. `ChartType.Line`), und die nachfolgenden `Series.Add`‑Aufrufe füllen das neue Diagramm auf dieselbe Weise.

**Q: Wie ändere ich die Größe des Diagramms, nachdem es eingefügt wurde?**  
A: Passen Sie die Eigenschaften `Width` und `Height` des von `InsertChart` zurückgegebenen `Shape` an (z. B. `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Gibt es eine schnelle Möglichkeit, Datenbeschriftungen für jede Säule des Diagramms anzuzeigen?**  
A: Setzen Sie `chartObj.Series[i].HasDataLabel = true;` für jede Serie nach dem Hinzufügen, oder iterieren Sie über `chartObj.Series` und aktivieren Sie `HasDataLabel`, um die Werte im Diagramm anzuzeigen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}