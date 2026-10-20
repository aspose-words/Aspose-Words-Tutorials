---
title: Diagramm proportional skalieren beim Ändern der Seitengröße in Word mit Aspose.Words für .NET
weight: 210
limit:
description: Erfahren Sie, wie Sie ein Word‑Säulendiagramm automatisch skalieren, wenn das Dokument auf A4 umgestellt wird, mithilfe von Aspose.Words für .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erfahren Sie, wie Sie ein Word‑Säulendiagramm automatisch skalieren,
    wenn das Dokument auf A4 umgestellt wird, mithilfe von Aspose.Words für .NET.
  headline: Diagramm proportional skalieren beim Ändern der Seitengröße in Word mit
    Aspose.Words für .NET
  type: TechArticle
- description: Erfahren Sie, wie Sie ein Word‑Säulendiagramm automatisch skalieren,
    wenn das Dokument auf A4 umgestellt wird, mithilfe von Aspose.Words für .NET.
  name: Diagramm proportional skalieren beim Ändern der Seitengröße in Word mit Aspose.Words
    für .NET
  steps:
  - name: Erstellen Sie ein neues Document‑Objekt und einen DocumentBuilder, um es
      zu bearbeiten.
    text: Erstellen Sie ein neues Document‑Objekt und einen DocumentBuilder, um es
      zu bearbeiten.
  - name: Fügen Sie ein Säulendiagramm mit der Größe 432 × 252 Punkte ein und erhalten
      Sie das zugehörige Chart‑Objekt.
    text: Fügen Sie ein Säulendiagramm mit der Größe 432 × 252 Punkte ein und erhalten
      Sie das zugehörige Chart‑Objekt.
  - name: Setzen Sie den Diagrammtitel‑Text auf \"Quarterly Revenue\" und machen Sie
      ihn sichtbar.
    text: Setzen Sie den Diagrammtitel‑Text auf \"Quarterly Revenue\" und machen Sie
      ihn sichtbar.
  - name: Speichern Sie das Dokument in einer Datei, die die ursprüngliche Diagrammgröße
      anzeigt.
    text: Speichern Sie das Dokument in einer Datei, die die ursprüngliche Diagrammgröße
      anzeigt.
  - name: Ändern Sie die Papiergröße des Dokuments auf A4 und aktualisieren Sie das
      Layout.
    text: Ändern Sie die Papiergröße des Dokuments auf A4 und aktualisieren Sie das
      Layout.
  - name: Berechnen Sie eine neue Diagrammbreite, die 80 % der Seitenbreite entspricht,
      und erhalten Sie dabei das ursprüngliche Seitenverhältnis bei.
    text: Berechnen Sie eine neue Diagrammbreite, die 80 % der Seitenbreite entspricht,
      und erhalten Sie dabei das ursprüngliche Seitenverhältnis bei.
  - name: Falls die Form ein Diagramm enthält, wenden Sie die berechnete Breite und
      Höhe an, um sie zu skalieren.
    text: Falls die Form ein Diagramm enthält, wenden Sie die berechnete Breite und
      Höhe an, um sie zu skalieren.
  - name: Speichern Sie das Dokument, nachdem das Diagramm an die neue Seitengröße
      angepasst wurde.
    text: Speichern Sie das Dokument, nachdem das Diagramm an die neue Seitengröße
      angepasst wurde.
  type: HowTo
- questions:
  - answer: Ja. Das Ändern von `docBuilder.PageSetup.PaperSize` passt vorhandene Formen
      nicht automatisch an, daher müssen Sie `chartContainer.Width` und `Height` selbst
      neu berechnen und zuweisen, wie gezeigt.
    question: Muss ich das Diagramm nach dem Ändern der Papiergröße des Dokuments
      manuell skalieren?
  - answer: Es speichert `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      und berechnet anschließend `newChartHeight = newChartWidth * originalAspectRatio`,
      nachdem die neue Breite ermittelt wurde.
    question: Wie bewahrt der Code das ursprüngliche Breiten‑zu‑Höhen‑Verhältnis des
      Diagramms beim Skalieren?
  - answer: '`UpdatePageLayout()` zwingt die Layout‑Engine, die Seitenabmessungen
      neu zu bewerten, sodass `docBuilder.PageSetup.PageWidth` die neue A4‑Breite
      widerspiegelt, bevor die Diagrammgröße neu berechnet wird.'
    question: Warum wird `myDoc.UpdatePageLayout()` nach dem Festlegen der Papiergröße
      auf A4 aufgerufen?
  - answer: Die Bedingung `if (chartContainer.HasChart)` verhindert, dass der Code
      `Width` und `Height` zuweist, wenn kein Diagramm vorhanden ist, und vermeidet
      so eine Laufzeitausnahme.
    question: Was passiert, wenn die eingefügte Form tatsächlich kein Diagramm enthält?
  - answer: Auf jeden Fall – ersetzen Sie den Multiplikator `0.8` durch einen beliebigen
      gewünschten Prozentsatz; der Rest der Skalierungslogik bewahrt weiterhin das
      ursprüngliche Seitenverhältnis.
    question: Kann ich den Skalierungsfaktor von 80 % auf einen anderen Wert ändern?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Word‑Diagramm beim Wechsel zu A4 skalieren
og_description: Halten Sie Ihr Diagramm proportional, indem Sie es nach dem Wechsel des Dokuments zu A4 automatisch skalieren.
og_image_alt: Screenshot, der ein Säulendiagramm zeigt, das automatisch auf die Größe eines A4‑Word‑Dokuments angepasst wurde, mithilfe von Aspose.Words für .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Diagramm proportional skalieren beim Ändern der Seitengröße in Word mit Aspose.Words für .NET
Dieses Tutorial zeigt, wie man ein Säulendiagramm in ein Word‑Dokument einfügt, die Seitengröße des Dokuments auf A4 umstellt und das Diagramm automatisch so skaliert, dass es proportional zur neuen Seitenbreite bleibt. Wenn Sie den Schritten folgen, sehen Sie, wie das Diagramm seine Abmessungen ohne manuelle Skalierung anpasst, wodurch ein konsistentes Layout über verschiedene Seitenformate hinweg gewährleistet wird.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Muss ich das Diagramm nach dem Ändern der Papiergröße des Dokuments manuell skalieren?**  
A: Ja. Das Ändern von `docBuilder.PageSetup.PaperSize` passt vorhandene Formen nicht automatisch an, daher müssen Sie `chartContainer.Width` und `Height` selbst neu berechnen und zuweisen, wie gezeigt.

**Q: Wie bewahrt der Code das ursprüngliche Breiten‑zu‑Höhen‑Verhältnis des Diagramms beim Skalieren?**  
A: Es speichert `originalAspectRatio = chartContainer.Height / chartContainer.Width` und berechnet anschließend `newChartHeight = newChartWidth * originalAspectRatio`, nachdem die neue Breite ermittelt wurde.

**Q: Warum wird `myDoc.UpdatePageLayout()` nach dem Festlegen der Papiergröße auf A4 aufgerufen?**  
A: `UpdatePageLayout()` zwingt die Layout‑Engine, die Seitenabmessungen neu zu bewerten, sodass `docBuilder.PageSetup.PageWidth` die neue A4‑Breite widerspiegelt, bevor die Diagrammgröße neu berechnet wird.

**Q: Was passiert, wenn die eingefügte Form tatsächlich kein Diagramm enthält?**  
A: Die Bedingung `if (chartContainer.HasChart)` verhindert, dass der Code `Width` und `Height` zuweist, wenn kein Diagramm vorhanden ist, und vermeidet so eine Laufzeitausnahme.

**Q: Kann ich den Skalierungsfaktor von 80 % auf einen anderen Wert ändern?**  
A: Auf jeden Fall – ersetzen Sie den Multiplikator `0.8` durch einen beliebigen gewünschten Prozentsatz; der Rest der Skalierungslogik bewahrt weiterhin das ursprüngliche Seitenverhältnis.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}