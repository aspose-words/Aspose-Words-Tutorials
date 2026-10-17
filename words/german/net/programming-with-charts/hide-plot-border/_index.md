---
title: Plot‑Bereichsrand in einem Säulendiagramm mit Aspose.Words für .NET ausblenden
weight: 410
limit:
description: Erfahren Sie, wie Sie den Plot‑Bereichsrand eines Diagramms in einem Word‑Säulendiagramm ausblenden, während die Achsenlinien sichtbar bleiben, mit Aspose.Words für .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erfahren Sie, wie Sie den Plot‑Bereichsrand eines Diagramms in einem
    Word‑Säulendiagramm ausblenden, während die Achsenlinien sichtbar bleiben, mit
    Aspose.Words für .NET.
  headline: Plot‑Bereichsrand in einem Säulendiagramm mit Aspose.Words für .NET ausblenden
  type: TechArticle
- description: Erfahren Sie, wie Sie den Plot‑Bereichsrand eines Diagramms in einem
    Word‑Säulendiagramm ausblenden, während die Achsenlinien sichtbar bleiben, mit
    Aspose.Words für .NET.
  name: Plot‑Bereichsrand in einem Säulendiagramm mit Aspose.Words für .NET ausblenden
  steps:
  - name: Erstellen Sie ein neues leeres Word‑Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
    text: Erstellen Sie ein neues leeres Word‑Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
  - name: Fügen Sie ein 432×252‑Säulendiagramm in das Dokument ein und erhalten Sie
      das zugehörige Chart‑Objekt.
    text: Fügen Sie ein 432×252‑Säulendiagramm in das Dokument ein und erhalten Sie
      das zugehörige Chart‑Objekt.
  - name: Löschen Sie vorhandene Serien, definieren Sie drei Kategorienamen und fügen
      Sie dem Diagramm eine Serie mit Beispieldaten hinzu.
    text: Löschen Sie vorhandene Serien, definieren Sie drei Kategorienamen und fügen
      Sie dem Diagramm eine Serie mit Beispieldaten hinzu.
  - name: Setzen Sie die Strichstärke des Plot‑Bereichs auf Null, wodurch die Begrenzung
      entfernt wird, während die Achsenlinien sichtbar bleiben.
    text: Setzen Sie die Strichstärke des Plot‑Bereichs auf Null, wodurch die Begrenzung
      entfernt wird, während die Achsenlinien sichtbar bleiben.
  - name: Speichern Sie das geänderte Dokument als .docx‑Datei.
    text: Speichern Sie das geänderte Dokument als .docx‑Datei.
  type: HowTo
- questions:
  - answer: Die Eigenschaft `Stroke` gehört zum Gesamtlayout des `Chart`‑Objekts und
      zeichnet die rechteckige Begrenzung um den Plot‑Bereich; Achsenlinien sind separate
      `Axis`‑Objekte und werden von den `Stroke`‑Einstellungen des Diagramms nicht
      beeinflusst.
    question: Warum bewirkt das Setzen von `columnChart.Format.Stroke.Weight = 0`,
      dass der Plot‑Bereichsrand entfernt wird, die Achsenlinien jedoch sichtbar bleiben?
  - answer: Nein, die `Stroke`‑Eigenschaft steuert den gesamten Plot‑Bereichsrand
      als ein einzelnes Rechteck, sodass Teilrandbereiche nicht über Aspose.Words
      ausgeblendet werden können; Sie müssten benutzerdefinierte Formen darüberlegen
      oder das Diagramm manuell bearbeiten.
    question: Kann ich nur eine Seite des Plot‑Bereichsrandes (z. B. die linke Seite)
      ausblenden und die anderen drei Seiten sichtbar lassen?
  - answer: Ja, die `Stroke`‑Eigenschaft ist unabhängig vom `ChartType`, sodass das
      Setzen von `Weight` auf 0 den Plot‑Bereichsrand bei Linien-, Kreis- oder jedem
      anderen unterstützten Diagrammtyp entfernt.
    question: Wenn ich den Diagrammtyp zu Linie oder Kreis ändere, wird `columnChart.Format.Stroke.Weight
      = 0` dann immer noch den Plot‑Bereichsrand ausblenden?
  - answer: Eine zusätzliche Aktualisierung ist nicht erforderlich; das Löschen der
      Serien und das Hinzufügen einer neuen aktualisiert das Diagramm intern, und
      `wordDoc.Save(...)` schreibt den aktuellen Zustand in die .docx‑Datei.
    question: Muss ich das Diagramm nach dem Aufruf von `columnChart.Series.Clear()`
      aktualisieren, bevor ich das Dokument speichere?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Plot‑Rand in einem Word‑Säulendiagramm ausblenden
og_description: Entfernen Sie den Plot‑Bereichsrand und behalten Sie die Achsenlinien sichtbar in einem Word‑Säulendiagramm mit Aspose.Words für .NET.
og_image_alt: Leitfaden, der ein Word‑Dokument mit einem Säulendiagramm zeigt, bei dem der Plot‑Bereichsrand ausgeblendet, die Achsenlinien jedoch mit Aspose.Words für .NET sichtbar bleiben.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Plot‑Bereichsrand in einem Säulendiagramm mit Aspose.Words für .NET ausblenden
In diesem Tutorial lernen Sie, wie man ein Word‑Dokument erzeugt, ein Säulendiagramm einfügt, es mit Beispieldaten füllt und anschließend den Plot‑Bereichsrand des Diagramms ausblendet, während die Achsenlinien sichtbar bleiben. Der Schritt‑für‑Schritt‑Code demonstriert jede Operation und endet mit dem Speichern des Dokuments, sodass Sie das Ergebnis sofort sehen können.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: Warum bewirkt das Setzen von `columnChart.Format.Stroke.Weight = 0`, dass der Plot‑Bereichsrand entfernt wird, die Achsenlinien jedoch sichtbar bleiben?**  
A: Die Eigenschaft `Stroke` gehört zum Gesamtlayout des `Chart`‑Objekts und zeichnet die rechteckige Begrenzung um den Plot‑Bereich; Achsenlinien sind separate `Axis`‑Objekte und werden von den `Stroke`‑Einstellungen des Diagramms nicht beeinflusst.

**Q: Kann ich nur eine Seite des Plot‑Bereichsrandes (z. B. die linke Seite) ausblenden und die anderen drei Seiten sichtbar lassen?**  
A: Nein, die `Stroke`‑Eigenschaft steuert den gesamten Plot‑Bereichsrand als ein einzelnes Rechteck, sodass Teilrandbereiche nicht über Aspose.Words ausgeblendet werden können; Sie müssten benutzerdefinierte Formen darüberlegen oder das Diagramm manuell bearbeiten.

**Q: Wenn ich den Diagrammtyp zu Linie oder Kreis ändere, wird `columnChart.Format.Stroke.Weight = 0` dann immer noch den Plot‑Bereichsrand ausblenden?**  
A: Ja, die `Stroke`‑Eigenschaft ist unabhängig vom `ChartType`, sodass das Setzen von `Weight` auf 0 den Plot‑Bereichsrand bei Linien-, Kreis- oder jedem anderen unterstützten Diagrammtyp entfernt.

**Q: Muss ich das Diagramm nach dem Aufruf von `columnChart.Series.Clear()` aktualisieren, bevor ich das Dokument speichere?**  
A: Eine zusätzliche Aktualisierung ist nicht erforderlich; das Löschen der Serien und das Hinzufügen einer neuen aktualisiert das Diagramm intern, und `wordDoc.Save(...)` schreibt den aktuellen Zustand in die .docx‑Datei.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}