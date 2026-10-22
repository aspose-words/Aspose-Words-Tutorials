---
title: Diagrammtitel aktualisieren und Legenden‑Sichtbarkeit in Word mit Aspose.Words für .NET umschalten
weight: 810
limit:
description: Erfahren Sie, wie Sie den Diagrammtitel ändern und die Legenden‑Sichtbarkeit in einem Word‑Dokument mit Aspose.Words für .NET steuern.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erfahren Sie, wie Sie den Diagrammtitel ändern und die Legenden‑Sichtbarkeit
    in einem Word‑Dokument mit Aspose.Words für .NET steuern.
  headline: Diagrammtitel aktualisieren und Legenden‑Sichtbarkeit in Word mit Aspose.Words
    für .NET umschalten
  type: TechArticle
- description: Erfahren Sie, wie Sie den Diagrammtitel ändern und die Legenden‑Sichtbarkeit
    in einem Word‑Dokument mit Aspose.Words für .NET steuern.
  name: Diagrammtitel aktualisieren und Legenden‑Sichtbarkeit in Word mit Aspose.Words
    für .NET umschalten
  steps:
  - name: Definieren Sie den vom Benutzer bereitgestellten Diagrammtitel und ob die
      Legende angezeigt werden soll.
    text: Definieren Sie den vom Benutzer bereitgestellten Diagrammtitel und ob die
      Legende angezeigt werden soll.
  - name: Erstellen Sie ein neues Word‑Dokument und einen DocumentBuilder, um Inhalte
      hinzuzufügen.
    text: Erstellen Sie ein neues Word‑Dokument und einen DocumentBuilder, um Inhalte
      hinzuzufügen.
  - name: Fügen Sie ein 432 × 252 pt column chart in das Dokument ein und prüfen Sie,
      ob die Shape tatsächlich ein Diagramm enthält.
    text: Fügen Sie ein 432 × 252 pt column chart in das Dokument ein und prüfen Sie,
      ob die Shape tatsächlich ein Diagramm enthält.
  - name: Rufen Sie das Chart‑Objekt ab, setzen Sie dessen Titeltext auf den vom Benutzer
      angegebenen Wert und stellen Sie sicher, dass der Titel angezeigt wird.
    text: Rufen Sie das Chart‑Objekt ab, setzen Sie dessen Titeltext auf den vom Benutzer
      angegebenen Wert und stellen Sie sicher, dass der Titel angezeigt wird.
  - name: 'Konfigurieren Sie die Legende: Zeigen Sie sie rechts an, wenn gewünscht,
      andernfalls verbergen Sie sie, und erlauben Sie, dass sie den Plot‑Bereich überlagert.'
    text: 'Konfigurieren Sie die Legende: Zeigen Sie sie rechts an, wenn gewünscht,
      andernfalls verbergen Sie sie, und erlauben Sie, dass sie den Plot‑Bereich überlagert.'
  - name: Speichern Sie das modifizierte Dokument auf dem Datenträger unter dem Namen CustomChart.docx.
    text: Speichern Sie das modifizierte Dokument auf dem Datenträger unter dem Namen CustomChart.docx.
  type: HowTo
- questions:
  - answer: Wenn `displayLegend` auf `true` gesetzt ist, legt der Code `chartLegend.Position`
      auf `LegendPosition.Right` fest, wodurch die Legende rechts neben dem Plot‑Bereich
      sichtbar wird; die Eigenschaft `Overlay` bleibt `true`, sodass die Legende das
      Diagramm überlappen kann, um Platz zu sparen.
    question: Was bewirkt das Setzen von `displayLegend` auf `true` im erzeugten Diagramm?
  - answer: Setzen Sie `chartTitle.Show = false` (oder lassen Sie das Setzen von `Show`
      auf `true` einfach weg), nachdem Sie `chartTitle.Text` zugewiesen haben; der
      Titel wird im Word‑Dokument nicht gerendert.
    question: Wie kann ich den Diagrammtitel ausblenden, wenn der Benutzer keinen
      angibt?
  - answer: Ja – `InsertChart` gibt ein `Shape` zurück, das ein Diagramm enthalten
      sollte, aber die Überprüfung von `HasChart` stellt sicher, dass die Shape tatsächlich
      ein `Chart`‑Objekt enthält; andernfalls wirft der Code eine `InvalidOperationException`.
    question: Ist es notwendig, nach dem Aufruf von `InsertChart` `chartContainer.HasChart`
      zu prüfen?
  - answer: Auf jeden Fall; weisen Sie `chartLegend.Position` einen beliebigen Wert
      aus dem `LegendPosition`‑Enum zu (z. B. `LegendPosition.Top`, `LegendPosition.Bottom`,
      `LegendPosition.Left`), um die Legende nach Bedarf neu zu positionieren.
    question: Kann ich die Legende an einer anderen Stelle als rechts platzieren?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Diagrammtitel & Legende in Word ändern
og_description: Erfahren Sie, wie Sie einen benutzerdefinierten Diagrammtitel festlegen und die Anzeige der Legende in einem Word‑Dokument mit Aspose.Words für .NET steuern.
og_image_alt: Anleitung, die Code zeigt, der den Diagrammtitel aktualisiert und die Legende in einem Word‑Dokument mit Aspose.Words für .NET umschaltet
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Diagrammtitel aktualisieren und Legenden‑Sichtbarkeit in Word mit Aspose.Words für .NET umschalten
Dieses Tutorial zeigt, wie man ein Diagramm in einem Word‑Dokument programmgesteuert mit Aspose.Words für .NET ändert. Sie lernen, ein column chart einzufügen, dessen Titel durch vom Benutzer bereitgestellten Text zu ersetzen und die Sichtbarkeit sowie das Overlay der Legende basierend auf den Benutzereinstellungen zu steuern. Diese Schritte ermöglichen es Ihnen, die Diagramm‑Darstellung dynamisch anzupassen, ohne manuell zu editieren.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Was bewirkt das Setzen von `displayLegend` auf `true` im erzeugten Diagramm?**  
A: Wenn `displayLegend` auf `true` gesetzt ist, legt der Code `chartLegend.Position` auf `LegendPosition.Right` fest, wodurch die Legende rechts neben dem Plot‑Bereich sichtbar wird; die Eigenschaft `Overlay` bleibt `true`, sodass die Legende das Diagramm überlappen kann, um Platz zu sparen.

**Q: Wie kann ich den Diagrammtitel ausblenden, wenn der Benutzer keinen angibt?**  
A: Setzen Sie `chartTitle.Show = false` (oder lassen Sie das Setzen von `Show` auf `true` einfach weg), nachdem Sie `chartTitle.Text` zugewiesen haben; der Titel wird im Word‑Dokument nicht gerendert.

**Q: Ist es notwendig, nach dem Aufruf von `InsertChart` `chartContainer.HasChart` zu prüfen?**  
A: Ja – `InsertChart` gibt ein `Shape` zurück, das ein Diagramm enthalten sollte, aber die Überprüfung von `HasChart` stellt sicher, dass die Shape tatsächlich ein `Chart`‑Objekt enthält; andernfalls wirft der Code eine `InvalidOperationException`.

**Q: Kann ich die Legende an einer anderen Stelle als rechts platzieren?**  
A: Auf jeden Fall; weisen Sie `chartLegend.Position` einen beliebigen Wert aus dem `LegendPosition`‑Enum zu (z. B. `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`), um die Legende nach Bedarf neu zu positionieren.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}