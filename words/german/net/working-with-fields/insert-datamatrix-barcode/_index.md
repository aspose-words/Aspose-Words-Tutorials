---
title: DataMatrix-Barcode in ein Word-Dokument einfügen mit Aspose.Words für .NET
weight: 210
limit:
description: Fügen Sie programmgesteuert einen DataMatrix-Barcode zu einem Word-Dokument mit Aspose.Words für .NET hinzu.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Fügen Sie programmgesteuert einen DataMatrix-Barcode zu einem Word-Dokument
    mit Aspose.Words für .NET hinzu.
  headline: DataMatrix-Barcode in ein Word-Dokument einfügen mit Aspose.Words für
    .NET
  type: TechArticle
- description: Fügen Sie programmgesteuert einen DataMatrix-Barcode zu einem Word-Dokument
    mit Aspose.Words für .NET hinzu.
  name: DataMatrix-Barcode in ein Word-Dokument einfügen mit Aspose.Words für .NET
  steps:
  - name: Erstellen Sie ein neues leeres Word-Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
    text: Erstellen Sie ein neues leeres Word-Dokument und einen DocumentBuilder,
      um es zu bearbeiten.
  - name: Fügen Sie an der aktuellen Cursorposition ein DISPLAYBARCODE-Feld ein, das
      einen Feldplatzhalter zum Dokument hinzufügt.
    text: Fügen Sie an der aktuellen Cursorposition ein DISPLAYBARCODE-Feld ein, das
      einen Feldplatzhalter zum Dokument hinzufügt.
  - name: Setzen Sie den BarcodeType des Feldes auf DataMatrix und geben Sie die zu
      codierende Datenzeichenfolge an.
    text: Setzen Sie den BarcodeType des Feldes auf DataMatrix und geben Sie die zu
      codierende Datenzeichenfolge an.
  - name: Optional können Sie die Hintergrund- und Vordergrundfarben des Barcodes
      festlegen.
    text: Optional können Sie die Hintergrund- und Vordergrundfarben des Barcodes
      festlegen.
  - name: Rufen Sie UpdateFields für das Dokument auf, um das Barcode-Bild im Feld
      zu rendern.
    text: Rufen Sie UpdateFields für das Dokument auf, um das Barcode-Bild im Feld
      zu rendern.
  - name: Speichern Sie das Dokument als .docx-Datei.
    text: Speichern Sie das Dokument als .docx-Datei.
  type: HowTo
- questions:
  - answer: Das Feld wird eingefügt, aber `document.UpdateFields()` lässt den Barcode
      leer und Aspose.Words wirft eine `FieldException`, die einen ungültigen Barcode-Typ
      anzeigt.
    question: Was passiert, wenn ich `displayBarcodeField.BarcodeType` einen nicht
      unterstützten Wert zuweise?
  - answer: '`UpdateFields()` rendert die Barcode-Bilder, sodass Sie mehrere `FieldDisplayBarcode`-Objekte
      einfügen und `document.UpdateFields()` am Ende ein einziges Mal aufrufen können,
      um alle zu rendern.'
    question: Muss ich `document.UpdateFields()` nach jeder Barcode-Einfügung aufrufen,
      oder kann ich einmalig nach dem Hinzufügen aller Felder aktualisieren?
  - answer: Beide Eigenschaften erwarten eine hexadezimale RGB-Zeichenfolge, die mit
      `0x` beginnt (z. B. `"0xFF0000"` für Rot); jedes andere Format wird ignoriert
      und die Standardfarben werden verwendet.
    question: In welchem Format müssen die Farbzeichenfolgen für `BackgroundColor`
      und `ForegroundColor` vorliegen?
  - answer: Ja – setzen Sie einfach `displayBarcodeField.BarcodeValue` auf eine neue
      Zeichenfolge und rufen Sie `document.UpdateFields()` erneut auf, um das gerenderte
      Bild zu aktualisieren.
    question: Kann ich die Barcode-Nutzdaten ändern, nachdem das Feld eingefügt wurde?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: DataMatrix-Barcode mit Aspose.Words einfügen
og_description: Erfahren Sie, wie Sie in nur wenigen Zeilen .NET-Code einen DataMatrix-Barcode zu einer Word-Datei hinzufügen.
og_image_alt: Leitfaden, der zeigt, wie man einen DataMatrix-Barcode in ein Word-Dokument einfügt und rendert, wobei Aspose.Words für .NET verwendet wird
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# DataMatrix-Barcode in ein Word-Dokument einfügen mit Aspose.Words für .NET
Mit Aspose.Words für .NET können Sie programmgesteuert einen DataMatrix-Barcode zu einem Word-Dokument hinzufügen. Dieses Tutorial zeigt, wie man ein neues Dokument erstellt, ein DISPLAYBARCODE-Feld einfügt, dessen Typ auf DataMatrix setzt und das Barcode-Bild mit den Klassen Document und DocumentBuilder rendert. Folgen Sie den Schritten, um einen druckbaren Barcode direkt in Ihrer .docx-Datei zu erzeugen.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Was passiert, wenn ich `displayBarcodeField.BarcodeType` einen nicht unterstützten Wert zuweise?**  
A: Das Feld wird eingefügt, aber `document.UpdateFields()` lässt den Barcode leer und Aspose.Words wirft eine `FieldException`, die einen ungültigen Barcode-Typ anzeigt.

**Q: Muss ich `document.UpdateFields()` nach jeder Barcode-Einfügung aufrufen, oder kann ich einmalig nach dem Hinzufügen aller Felder aktualisieren?**  
A: `UpdateFields()` rendert die Barcode-Bilder, sodass Sie mehrere `FieldDisplayBarcode`-Objekte einfügen und `document.UpdateFields()` am Ende ein einziges Mal aufrufen können, um alle zu rendern.

**Q: In welchem Format müssen die Farbzeichenfolgen für `BackgroundColor` und `ForegroundColor` vorliegen?**  
A: Beide Eigenschaften erwarten eine hexadezimale RGB-Zeichenfolge, die mit `0x` beginnt (z. B. `"0xFF0000"` für Rot); jedes andere Format wird ignoriert und die Standardfarben werden verwendet.

**Q: Kann ich die Barcode-Nutzdaten ändern, nachdem das Feld eingefügt wurde?**  
A: Ja – setzen Sie einfach `displayBarcodeField.BarcodeValue` auf eine neue Zeichenfolge und rufen Sie `document.UpdateFields()` erneut auf, um das gerenderte Bild zu aktualisieren.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}