---
title: Rotes diagonales Textwasserzeichen zu Word-Dokumenten hinzufügen mit Aspose.Words für .NET
weight: 110
limit:
description: Automatisches Anwenden eines roten diagonalen Textwasserzeichens auf jede in einem Batch erzeugte Word-Datei mit Aspose.Words für .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Automatisches Anwenden eines roten diagonalen Textwasserzeichens auf
    jede in einem Batch erzeugte Word-Datei mit Aspose.Words für .NET.
  headline: Rotes diagonales Textwasserzeichen zu Word-Dokumenten hinzufügen mit Aspose.Words
    für .NET
  type: TechArticle
- description: Automatisches Anwenden eines roten diagonalen Textwasserzeichens auf
    jede in einem Batch erzeugte Word-Datei mit Aspose.Words für .NET.
  name: Rotes diagonales Textwasserzeichen zu Word-Dokumenten hinzufügen mit Aspose.Words
    für .NET
  steps:
  - name: Erstellen Sie den Ordner "GeneratedReports", in dem die Ausgabedateien gespeichert
      werden.
    text: Erstellen Sie den Ordner "GeneratedReports", in dem die Ausgabedateien gespeichert
      werden.
  - name: Starten Sie eine Schleife, die drei separate Dokumente erzeugt.
    text: Starten Sie eine Schleife, die drei separate Dokumente erzeugt.
  - name: Erstellen Sie ein neues leeres Word-Dokumentobjekt.
    text: Erstellen Sie ein neues leeres Word-Dokumentobjekt.
  - name: Verwenden Sie DocumentBuilder, um eine Titelzeile und eine Beschreibung
      in das Dokument zu schreiben.
    text: Verwenden Sie DocumentBuilder, um eine Titelzeile und eine Beschreibung
      in das Dokument zu schreiben.
  - name: Definieren Sie das Aussehen des Wasserzeichens, einschließlich Schriftart,
      Größe, Farbe und diagonaler Anordnung.
    text: Definieren Sie das Aussehen des Wasserzeichens, einschließlich Schriftart,
      Größe, Farbe und diagonaler Anordnung.
  - name: Wenden Sie das konfigurierte rote diagonale Wasserzeichen mit dem Text "PROTECTED"
      auf das Dokument an.
    text: Wenden Sie das konfigurierte rote diagonale Wasserzeichen mit dem Text "PROTECTED"
      auf das Dokument an.
  - name: Speichern Sie das wassergezeichnete Dokument im Ordner "GeneratedReports"
      mit einem eindeutigen Dateinamen.
    text: Speichern Sie das wassergezeichnete Dokument im Ordner "GeneratedReports"
      mit einem eindeutigen Dateinamen.
  - name: Schließen Sie die Schleife nach der Verarbeitung des aktuellen Dokuments.
    text: Schließen Sie die Schleife nach der Verarbeitung des aktuellen Dokuments.
  type: HowTo
- questions:
  - answer: IsSemitrasparent bestimmt, ob das Wasserzeichen mit teilweiser Transparenz
      gerendert wird; das Setzen auf **true** macht den Text halbtransparent, sodass
      der darunterliegende Inhalt besser lesbar bleibt.
    question: Wofür steht die Option **IsSemitrasparent** und welche Auswirkung hat
      das Setzen auf **true**?
  - answer: Ja – setzen Sie die Eigenschaft **Layout** auf **WatermarkLayout.Horizontal**
      in den **TextWatermarkOptions**, bevor Sie **document.Watermark.SetText** aufrufen.
    question: Kann ich die Ausrichtung des Wasserzeichens von diagonal auf horizontal
      ändern?
  - answer: Das Snippet erstellt eine neue **Document**‑Instanz, aber Sie können jede
      vorhandene Datei öffnen (z. B. `new Document("Existing.docx")`) und anschließend
      **document.Watermark.SetText** aufrufen, um dasselbe Wasserzeichen anzuwenden.
    question: Fügt dieser Code ein Wasserzeichen zu einer bestehenden Word-Datei hinzu
      oder nur zu neu erstellten Dokumenten?
  - answer: Weisen Sie der **Color**‑Eigenschaft von **TextWatermarkOptions** eine
      benutzerdefinierte Farbe mit **Color.FromArgb(red, green, blue)** zu, z. B.
      `Color = Color.FromArgb(128, 0, 128)` für Lila.
    question: Wie kann ich eine benutzerdefinierte RGB‑Farbe für das Wasserzeichen
      verwenden anstelle des vordefinierten **Color.Red**?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Ein rotes diagonales Textwasserzeichen zu Word-Dokumenten hinzufügen
og_description: Sehen Sie, wie man mit Aspose.Words ein rotes diagonales Wasserzeichen automatisch auf jedes Word-Dokument in einem Batch anwendet.
og_image_alt: Leitfaden, der zeigt, wie man mit Aspose.Words für .NET ein rotes diagonales Textwasserzeichen zu Word-Dokumenten hinzufügt
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rotes diagonales Textwasserzeichen zu Word-Dokumenten hinzufügen mit Aspose.Words für .NET
Dieses Tutorial demonstriert, wie man automatisch ein rotes diagonales Textwasserzeichen in jedes während einer Batch‑Berichtserstellung erzeugte Word-Dokument einbettet. Mit den Klassen Document und DocumentBuilder von Aspose.Words für .NET wird das Wasserzeichen programmgesteuert beim Erzeugen der Dateien angewendet, sodass jedes Dokument dieselbe Markenkennzeichnung oder Vertraulichkeitsmitteilung ohne manuellen Aufwand enthält.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Wofür steht die Option **IsSemitrasparent** und welche Auswirkung hat das Setzen auf **true**?**  
A: IsSemitrasparent bestimmt, ob das Wasserzeichen mit teilweiser Transparenz gerendert wird; das Setzen auf **true** macht den Text halbtransparent, sodass der darunterliegende Inhalt besser lesbar bleibt.

**Q: Kann ich die Ausrichtung des Wasserzeichens von diagonal auf horizontal ändern?**  
A: Ja – setzen Sie die Eigenschaft **Layout** auf **WatermarkLayout.Horizontal** in den **TextWatermarkOptions**, bevor Sie **document.Watermark.SetText** aufrufen.

**Q: Fügt dieser Code ein Wasserzeichen zu einer bestehenden Word-Datei hinzu oder nur zu neu erstellten Dokumenten?**  
A: Das Snippet erstellt eine neue **Document**‑Instanz, aber Sie können jede vorhandene Datei öffnen (z. B. `new Document("Existing.docx")`) und anschließend **document.Watermark.SetText** aufrufen, um dasselbe Wasserzeichen anzuwenden.

**Q: Wie kann ich eine benutzerdefinierte RGB‑Farbe für das Wasserzeichen verwenden anstelle des vordefinierten **Color.Red**?**  
A: Weisen Sie der **Color**‑Eigenschaft von **TextWatermarkOptions** eine benutzerdefinierte Farbe mit **Color.FromArgb(red, green, blue)** zu, z. B. `Color = Color.FromArgb(128, 0, 128)` für Lila.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}