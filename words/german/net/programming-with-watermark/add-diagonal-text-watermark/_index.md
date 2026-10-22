---
title: Erstelle ein diagonales Text‑Wasserzeichen mit benutzerdefinierter Schrift in einem Word‑Dokument mit Aspose.Words für .NET
weight: 210
limit:
description: Schritt‑für‑Schritt‑Code, um ein diagonales Text‑Wasserzeichen mit benutzerdefinierter Schrift zu einem Word‑.docx mit Aspose.Words für .NET hinzuzufügen.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Schritt‑für‑Schritt‑Code, um ein diagonales Text‑Wasserzeichen mit
    benutzerdefinierter Schrift zu einem Word‑.docx mit Aspose.Words für .NET hinzuzufügen.
  headline: Erstelle ein diagonales Text‑Wasserzeichen mit benutzerdefinierter Schrift
    in einem Word‑Dokument mit Aspose.Words für .NET
  type: TechArticle
- description: Schritt‑für‑Schritt‑Code, um ein diagonales Text‑Wasserzeichen mit
    benutzerdefinierter Schrift zu einem Word‑.docx mit Aspose.Words für .NET hinzuzufügen.
  name: Erstelle ein diagonales Text‑Wasserzeichen mit benutzerdefinierter Schrift
    in einem Word‑Dokument mit Aspose.Words für .NET
  steps:
  - name: Erstelle eine neue leere Word‑Dokumentinstanz mit dem Namen `document`.
    text: Erstelle eine neue leere Word‑Dokumentinstanz mit dem Namen `document`.
  - name: Konfiguriere `watermarkSettings` mit der Schriftart Arial, 48 pt, grauer
      Farbe, diagonaler Anordnung und undurchsichtiger Darstellung.
    text: Konfiguriere `watermarkSettings` mit der Schriftart Arial, 48 pt, grauer
      Farbe, diagonaler Anordnung und undurchsichtiger Darstellung.
  - name: Wende das Text‑Wasserzeichen "Private" auf `document` mit den zuvor definierten
      Einstellungen an.
    text: Wende das Text‑Wasserzeichen "Private" auf `document` mit den zuvor definierten
      Einstellungen an.
  - name: Definiere den Dateipfad, unter dem das wasserzeichenversehene Dokument gespeichert
      werden soll.
    text: Definiere den Dateipfad, unter dem das wasserzeichenversehene Dokument gespeichert
      werden soll.
  - name: Speichere das modifizierte `document` am angegebenen Pfad als .docx‑Datei.
    text: Speichere das modifizierte `document` am angegebenen Pfad als .docx‑Datei.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` bestimmt, ob das Wasserzeichen mit teilweiser Transparenz
      gerendert wird; wird es auf `false` gesetzt, ist das Wasserzeichen vollständig
      undurchsichtig, bei `true` wird ein standardmäßiger halbtransparenter Effekt
      angewendet.'
    question: Wofür steht das **IsSemitrasparent**‑Flag in `TextWatermarkOptions`?
  - answer: Ja – setzen Sie die Eigenschaft `Layout` auf `WatermarkLayout.Horizontal`
      (oder einen anderen Enum‑Wert), bevor Sie `document.Watermark.SetText` aufrufen.
    question: Kann ich die Ausrichtung des Wasserzeichens von diagonal auf horizontal
      ändern?
  - answer: Word greift auf die Standardschrift für das Wasserzeichen zurück, sodass
      der Text weiterhin angezeigt wird, jedoch möglicherweise von der gewünschten
      Formatierung abweicht.
    question: Was passiert, wenn die angegebene `FontFamily` (z. B. "Arial") nicht
      auf dem Zielrechner installiert ist?
  - answer: Laden Sie die vorhandene Datei mit `Document document = new Document("Existing.docx");`,
      konfigurieren Sie anschließend `TextWatermarkOptions` und rufen Sie `document.Watermark.SetText`
      wie gezeigt auf.
    question: Ist es möglich, einem bestehenden `.docx`‑Datei ein Wasserzeichen hinzuzufügen,
      anstatt eine neue zu erstellen?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Diagonales Text‑Wasserzeichen mit benutzerdefinierter Schrift hinzufügen
og_description: Lernen Sie, in wenigen Minuten ein schräges Text‑Wasserzeichen mit Ihrer eigenen Schrift in eine Word‑Datei einzubetten.
og_image_alt: Anleitung, die zeigt, wie man ein diagonales Text‑Wasserzeichen mit benutzerdefinierter Schrift zu einem Word‑Dokument mit Aspose.Words für .NET hinzufügt
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Erstelle ein diagonales Text‑Wasserzeichen mit benutzerdefinierter Schrift in einem Word‑Dokument mit Aspose.Words für .NET
Dieses Tutorial führt Sie Schritt für Schritt durch das Erstellen eines neuen Word‑Dokuments, das Konfigurieren eines diagonalen Text‑Wasserzeichens mit Ihren gewünschten Schriftarteinstellungen, das Anwenden über die Document.Watermark.SetText‑API und das Speichern des Ergebnisses als .docx‑Datei. Am Ende besitzen Sie ein professionell wasserzeichenversehendes Dokument, das Ihre Markenidentität oder Eigentümerschaft präsentiert. Der Schritt‑für‑Schritt‑Code ist bereit, in jedes .NET‑Projekt kopiert zu werden.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Wofür steht das **IsSemitrasparent**‑Flag in `TextWatermarkOptions`?**  
A: `IsSemitrasparent` bestimmt, ob das Wasserzeichen mit teilweiser Transparenz gerendert wird; wird es auf `false` gesetzt, ist das Wasserzeichen vollständig undurchsichtig, bei `true` wird ein standardmäßiger halbtransparenter Effekt angewendet.

**Q: Kann ich die Ausrichtung des Wasserzeichens von diagonal auf horizontal ändern?**  
A: Ja – setzen Sie die Eigenschaft `Layout` auf `WatermarkLayout.Horizontal` (oder einen anderen Enum‑Wert), bevor Sie `document.Watermark.SetText` aufrufen.

**Q: Was passiert, wenn die angegebene `FontFamily` (z. B. "Arial") nicht auf dem Zielrechner installiert ist?**  
A: Word greift auf die Standardschrift für das Wasserzeichen zurück, sodass der Text weiterhin angezeigt wird, jedoch möglicherweise von der gewünschten Formatierung abweicht.

**Q: Ist es möglich, einem bestehenden `.docx`‑Datei ein Wasserzeichen hinzuzufügen, anstatt eine neue zu erstellen?**  
A: Laden Sie die vorhandene Datei mit `Document document = new Document("Existing.docx");`, konfigurieren Sie anschließend `TextWatermarkOptions` und rufen Sie `document.Watermark.SetText` wie gezeigt auf.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}