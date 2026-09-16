---
title: Rotierte‑Text‑Tabelle in Word‑Dokument mit Aspose.Words für .NET erstellen
weight: 110
limit:
description: Lernen Sie, eine Word‑Tabelle mit festen Spaltenbreiten, rotiertem Text, präzisen Zeilenhöhen und gefüllten Zellen mithilfe von Aspose.Words für .NET zu erstellen.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Lernen Sie, eine Word‑Tabelle mit festen Spaltenbreiten, rotiertem
    Text, präzisen Zeilenhöhen und gefüllten Zellen mithilfe von Aspose.Words für
    .NET zu erstellen.
  headline: Rotierte‑Text‑Tabelle in Word‑Dokument mit Aspose.Words für .NET erstellen
  type: TechArticle
- description: Lernen Sie, eine Word‑Tabelle mit festen Spaltenbreiten, rotiertem
    Text, präzisen Zeilenhöhen und gefüllten Zellen mithilfe von Aspose.Words für
    .NET zu erstellen.
  name: Rotierte‑Text‑Tabelle in Word‑Dokument mit Aspose.Words für .NET erstellen
  steps:
  - name: Instanziieren Sie ein neues Document und einen DocumentBuilder, die zum
      Erstellen der Tabelle verwendet werden.
    text: Instanziieren Sie ein neues Document und einen DocumentBuilder, die zum
      Erstellen der Tabelle verwendet werden.
  - name: Starten Sie eine neue Tabelle, fügen Sie die erste Zelle ein und fixieren
      Sie die Spaltenbreiten, sodass sie nicht automatisch angepasst werden.
    text: Starten Sie eine neue Tabelle, fügen Sie die erste Zelle ein und fixieren
      Sie die Spaltenbreiten, sodass sie nicht automatisch angepasst werden.
  - name: Richten Sie den Inhalt in der aktuellen Zelle vertikal zentriert aus und
      schreiben Sie den Text der ersten Zelle der ersten Zeile.
    text: Richten Sie den Inhalt in der aktuellen Zelle vertikal zentriert aus und
      schreiben Sie den Text der ersten Zelle der ersten Zeile.
  - name: Fügen Sie die zweite Zelle der ersten Zeile ein und schreiben Sie deren
      Text.
    text: Fügen Sie die zweite Zelle der ersten Zeile ein und schreiben Sie deren
      Text.
  - name: Schließen Sie die erste Zeile und finalisieren Sie ihr Layout.
    text: Schließen Sie die erste Zeile und finalisieren Sie ihr Layout.
  - name: Starten Sie die erste Zelle der zweiten Zeile, setzen Sie die Zeilenhöhe
      exakt auf 100 Punkte, drehen Sie den Text nach oben und schreiben Sie den Zellentext.
    text: Starten Sie die erste Zelle der zweiten Zeile, setzen Sie die Zeilenhöhe
      exakt auf 100 Punkte, drehen Sie den Text nach oben und schreiben Sie den Zellentext.
  - name: Fügen Sie die zweite Zelle der zweiten Zeile ein, drehen Sie deren Text
      nach unten und schreiben Sie den Zellentext.
    text: Fügen Sie die zweite Zelle der zweiten Zeile ein, drehen Sie deren Text
      nach unten und schreiben Sie den Zellentext.
  - name: Schließen Sie die zweite Zeile und vervollständigen Sie die zweite Zeile
      der Tabelle.
    text: Schließen Sie die zweite Zeile und vervollständigen Sie die zweite Zeile
      der Tabelle.
  - name: Beenden Sie den Tabellenaufbau und versiegeln Sie die Tabellenstruktur.
    text: Beenden Sie den Tabellenaufbau und versiegeln Sie die Tabellenstruktur.
  - name: Speichern Sie das fertiggestellte Dokument als .docx‑Datei.
    text: Speichern Sie das fertiggestellte Dokument als .docx‑Datei.
  type: HowTo
- questions:
  - answer: Nachdem Sie die Spaltenbreiten fixiert haben, weisen Sie jeder Zelle eine
      Breite zu mittels `builder.CellFormat.Width = <valueInPoints>;` bevor Sie die
      nächste Zelle einfügen; die Tabelle behält diese exakten Breiten bei.
    question: Wie kann ich nach dem Aufruf von `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`
      bestimmte Spaltenbreiten festlegen?
  - answer: '`builder.CellFormat.VerticalAlignment` ist eine zellbezogene Einstellung,
      daher müssen Sie sie für die Zellen der zweiten Zeile erneut setzen (z. B. `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) bevor Sie deren Inhalt schreiben.'
    question: Warum wirkt die vertikale Ausrichtung nur auf die erste Zeile und nicht
      auf die zweite Zeile?
  - answer: Ja – setzen Sie `builder.RowFormat.Height` und `builder.RowFormat.HeightRule
      = HeightRule.Exactly` vor jedem Aufruf von `builder.EndRow();`; die nächste
      Zeile kann dann einen anderen Höhenwert haben.
    question: Kann ich jeder Zeile eine unterschiedliche exakte Höhe zuweisen, und
      wenn ja, wie?
  - answer: Setzen Sie die Orientierung zurück, indem Sie `builder.CellFormat.Orientation
      = TextOrientation.Horizontal;` zuweisen, bevor Sie die nächste Zelle schreiben.
    question: Wie setze ich die Textorientierung nach der Verwendung von `TextOrientation.Upward`
      oder `Downward` wieder auf den Standard zurück?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Rotierte‑Text‑Tabelle in Word mit Aspose.Words erstellen
og_description: Schritt‑für‑Schritt‑Code zum Erstellen einer Tabelle mit fester Breite, vertikal rotiertem Text und exakten Zeilenhöhen.
og_image_alt: Screenshot, der ein Word‑Dokument mit einer Tabelle zeigt, die feste Spaltenbreiten, rotierten Text in den Zellen und definierte Zeilenhöhen hat, erstellt mit Aspose.Words für .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rotierte‑Text‑Tabelle in Word‑Dokument mit Aspose.Words für .NET erstellen
Dieses Tutorial zeigt, wie man ein Word‑Dokument erzeugt und eine Tabelle hinzufügt, deren Spalten feste Breiten haben, Zeilen exakte Höhen besitzen und der Zellentext vertikal rotiert ist. Sie lernen, vertikale Ausrichtung zu setzen, Textorientierung anzuwenden, jede Zelle mit Inhalt zu füllen und das Dokument schließlich zu speichern – alles mit Aspose.Words für .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Wie kann ich nach dem Aufruf von `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` bestimmte Spaltenbreiten festlegen?**  
A: Nachdem Sie die Spaltenbreiten fixiert haben, weisen Sie jeder Zelle eine Breite zu mittels `builder.CellFormat.Width = <valueInPoints>;` bevor Sie die nächste Zelle einfügen; die Tabelle behält diese exakten Breiten bei.

**Q: Warum wirkt die vertikale Ausrichtung nur auf die erste Zeile und nicht auf die zweite Zeile?**  
A: `builder.CellFormat.VerticalAlignment` ist eine zellbezogene Einstellung, daher müssen Sie sie für die Zellen der zweiten Zeile erneut setzen (z. B. `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) bevor Sie deren Inhalt schreiben.

**Q: Kann ich jeder Zeile eine unterschiedliche exakte Höhe zuweisen, und wenn ja, wie?**  
A: Ja – setzen Sie `builder.RowFormat.Height` und `builder.RowFormat.HeightRule = HeightRule.Exactly` vor jedem Aufruf von `builder.EndRow();`; die nächste Zeile kann dann einen anderen Höhenwert haben.

**Q: Wie setze ich die Textorientierung nach der Verwendung von `TextOrientation.Upward` oder `Downward` wieder auf den Standard zurück?**  
A: Setzen Sie die Orientierung zurück, indem Sie `builder.CellFormat.Orientation = TextOrientation.Horizontal;` zuweisen, bevor Sie die nächste Zelle schreiben.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}