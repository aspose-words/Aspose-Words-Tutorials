---
title: Seitenzahlen zur Fußzeile eines Word-Dokuments hinzufügen mit Aspose.Words für .NET
weight: 210
limit:
description: Automatisch aktualisierende Seitenzahlen zur primären Fußzeile eines Word-Dokuments hinzufügen mit Aspose.Words für .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Automatisch aktualisierende Seitenzahlen zur primären Fußzeile eines
    Word-Dokuments hinzufügen mit Aspose.Words für .NET.
  headline: Seitenzahlen zur Fußzeile eines Word-Dokuments hinzufügen mit Aspose.Words
    für .NET
  type: TechArticle
- description: Automatisch aktualisierende Seitenzahlen zur primären Fußzeile eines
    Word-Dokuments hinzufügen mit Aspose.Words für .NET.
  name: Seitenzahlen zur Fußzeile eines Word-Dokuments hinzufügen mit Aspose.Words
    für .NET
  steps:
  - name: Erstellen Sie ein neues Document-Objekt und einen damit verbundenen DocumentBuilder.
    text: Erstellen Sie ein neues Document-Objekt und einen damit verbundenen DocumentBuilder.
  - name: Bewegen Sie den Cursor des Builders zur primären Fußzeile des ersten Abschnitts.
    text: Bewegen Sie den Cursor des Builders zur primären Fußzeile des ersten Abschnitts.
  - name: Setzen Sie die Absatzausrichtung auf zentriert, damit der Fußzeilentext
      zentriert wird.
    text: Setzen Sie die Absatzausrichtung auf zentriert, damit der Fußzeilentext
      zentriert wird.
  - name: Schreiben Sie das Label "Page " und fügen Sie ein PAGE-Feld ein, das die
      aktuelle Seitennummer anzeigt.
    text: Schreiben Sie das Label "Page " und fügen Sie ein PAGE-Feld ein, das die
      aktuelle Seitennummer anzeigt.
  - name: Schreiben Sie " of " und fügen Sie ein NUMPAGES-Feld ein, das die Gesamtseitenzahl
      anzeigt.
    text: Schreiben Sie " of " und fügen Sie ein NUMPAGES-Feld ein, das die Gesamtseitenzahl
      anzeigt.
  - name: Speichern Sie das Dokument als .docx-Datei.
    text: Speichern Sie das Dokument als .docx-Datei.
  type: HowTo
- questions:
  - answer: Nein. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` bewegt den
      Builder nur zur primären Fußzeile des *ersten* Abschnitts, sodass die Felder
      dort allein eingefügt werden.
    question: Wenn das Dokument mehr als einen Abschnitt hat, fügt dieser Code Seitenzahlen
      zu jeder Fußzeile der Abschnitte hinzu?
  - answer: Setzen Sie `builder.ParagraphFormat.Alignment` vor dem Schreiben der Felder
      auf einen anderen `ParagraphAlignment`‑Wert (z. B. `ParagraphAlignment.Right`).
    question: Wie kann ich die Ausrichtung des Seitenzahl‑Absatzes in der Fußzeile
      ändern?
  - answer: '`InsertField` nimmt den Feldcode und ein optionales Feldresultat; das
      Übergeben von `null` weist Aspose.Words an, Word das Ergebnis zur Laufzeit berechnen
      zu lassen.'
    question: Was stellt das Argument `null` in `InsertField("PAGE", null)` dar?
  - answer: Ja – ersetzen Sie `HeaderFooterType.FooterPrimary` durch `HeaderFooterType.HeaderPrimary`
      (oder einen anderen Kopfzeilentyp), bevor Sie die Felder einfügen.
    question: Kann ich dieselben "Page X of Y"‑Felder in die Kopfzeile statt in die
      Fußzeile einfügen?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Automatische Seitenzahlen in die Word-Fußzeile einfügen
og_description: Schritt‑für‑Schritt‑Code, um Live‑Seitenzahlen zu einer Word‑Fußzeile mit Aspose.Words für .NET hinzuzufügen.
og_image_alt: Anleitung, die zeigt, wie man automatische Seitenzahlen zu einer Word‑Dokumentfußzeile mit Aspose.Words für .NET hinzufügt
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Seitenzahlen zur Fußzeile eines Word-Dokuments hinzufügen mit Aspose.Words für .NET
Dieses Tutorial zeigt, wie man Aspose.Words Document und DocumentBuilder verwendet, um automatisch aktualisierende Seitenzahlen in die primäre Fußzeile eines Word-Dokuments einzufügen. Durch das programmgesteuerte Hinzufügen von Seitenzahlen stellen Sie eine konsistente Seitennummerierung im gesamten Dokument sicher, ohne manuelle Bearbeitung. Der Beispielcode ist bereit, in einer .NET-Umgebung ausgeführt zu werden.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Wenn das Dokument mehr als einen Abschnitt hat, fügt dieser Code Seitenzahlen zu jeder Fußzeile der Abschnitte hinzu?**  
A: Nein. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` bewegt den Builder nur zur primären Fußzeile des *ersten* Abschnitts, sodass die Felder dort allein eingefügt werden.

**Q: Wie kann ich die Ausrichtung des Seitenzahl‑Absatzes in der Fußzeile ändern?**  
A: Setzen Sie `builder.ParagraphFormat.Alignment` vor dem Schreiben der Felder auf einen anderen `ParagraphAlignment`‑Wert (z. B. `ParagraphAlignment.Right`).

**Q: Was stellt das Argument `null` in `InsertField("PAGE", null)` dar?**  
A: `InsertField` nimmt den Feldcode und ein optionales Feldresultat; das Übergeben von `null` weist Aspose.Words an, Word das Ergebnis zur Laufzeit berechnen zu lassen.

**Q: Kann ich dieselben "Page X of Y"‑Felder in die Kopfzeile statt in die Fußzeile einfügen?**  
A: Ja – ersetzen Sie `HeaderFooterType.FooterPrimary` durch `HeaderFooterType.HeaderPrimary` (oder einen anderen Kopfzeilentyp), bevor Sie die Felder einfügen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}