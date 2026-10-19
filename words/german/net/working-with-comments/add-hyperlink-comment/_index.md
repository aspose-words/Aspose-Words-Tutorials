---
title: Hyperlink‑Comment hinzufügen und als PDF‑Annotation exportieren mit Aspose.Words für .NET
weight: 110
limit:
description: Lernen Sie, wie man einen Hyperlink‑Comment in einer Word‑Datei hinzufügt und ihn mit Aspose.Words für .NET als PDF‑Annotation exportiert.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lernen Sie, wie man einen Hyperlink‑Comment in einer Word‑Datei hinzufügt
    und ihn mit Aspose.Words für .NET als PDF‑Annotation exportiert.
  headline: Hyperlink‑Comment hinzufügen und als PDF‑Annotation exportieren mit Aspose.Words
    für .NET
  type: TechArticle
- description: Lernen Sie, wie man einen Hyperlink‑Comment in einer Word‑Datei hinzufügt
    und ihn mit Aspose.Words für .NET als PDF‑Annotation exportiert.
  name: Hyperlink‑Comment hinzufügen und als PDF‑Annotation exportieren mit Aspose.Words
    für .NET
  steps:
  - name: Erstellen Sie ein neues leeres Document‑Objekt und einen DocumentBuilder,
      um damit zu arbeiten.
    text: Erstellen Sie ein neues leeres Document‑Objekt und einen DocumentBuilder,
      um damit zu arbeiten.
  - name: Schreiben Sie eine Zeile sichtbaren Textes, die den kommenden Kommentar
      aufnehmen wird.
    text: Schreiben Sie eine Zeile sichtbaren Textes, die den kommenden Kommentar
      aufnehmen wird.
  - name: Erstellen Sie einen Comment von Jane Doe und fügen Sie ihn dem ersten Absatz
      des Dokuments hinzu.
    text: Erstellen Sie einen Comment von Jane Doe und fügen Sie ihn dem ersten Absatz
      des Dokuments hinzu.
  - name: Fügen Sie innerhalb des Comments einen Absatz hinzu und setzen Sie einen
      blauen, unterstrichenen Hyperlink zur Aspose.Words Library‑Website ein.
    text: Fügen Sie innerhalb des Comments einen Absatz hinzu und setzen Sie einen
      blauen, unterstrichenen Hyperlink zur Aspose.Words Library‑Website ein.
  - name: Konfigurieren Sie das Dokument so, dass Kommentare als PDF‑Annotationen
      gerendert werden, und aktualisieren Sie das Layout.
    text: Konfigurieren Sie das Dokument so, dass Kommentare als PDF‑Annotationen
      gerendert werden, und aktualisieren Sie das Layout.
  - name: Erstellen Sie im aktuellen Verzeichnis einen Ordner namens "Output", um
      das erzeugte PDF zu speichern.
    text: Erstellen Sie im aktuellen Verzeichnis einen Ordner namens "Output", um
      das erzeugte PDF zu speichern.
  - name: Speichern Sie das vorbereitete Dokument mit PdfSaveOptions als PDF‑Datei.
    text: Speichern Sie das vorbereitete Dokument mit PdfSaveOptions als PDF‑Datei.
  - name: Überprüfen Sie, ob die PDF‑Datei existiert und Daten enthält, und geben
      Sie das Ergebnis anschließend in der Konsole aus.
    text: Überprüfen Sie, ob die PDF‑Datei existiert und Daten enthält, und geben
      Sie das Ergebnis anschließend in der Konsole aus.
  type: HowTo
- questions:
  - answer: '`InsertHyperlink`s dritter Parameter gibt an, ob der Link als Feld behandelt
      werden soll; wird er auf `false` gesetzt, wird ein einfacher Hyperlink eingefügt,
      der in der PDF‑Annotation funktioniert, ohne dass ein Feldcode erforderlich
      ist.'
    question: Was steuert das dritte Argument (`false`) in `InsertHyperlink`?
  - answer: Setzen Sie `myDocument.LayoutOptions.CommentDisplayMode` auf `CommentDisplayMode.ShowInBalloons`,
      bevor Sie `Save` aufrufen; das PDF enthält dann den Kommentar als regulären
      Word‑Comment statt als Annotation.
    question: Wie kann ich den Kommentar im Word‑Dokument als Sprechblase anzeigen
      lassen, anstatt als PDF‑Annotation?
  - answer: Ja – jeder `Comment`, den Sie einem Absatz hinzufügen, kann einen eigenen
      `InsertHyperlink`‑Aufruf enthalten, und alle Hyperlinks werden beim Speichern
      des Dokuments als separate PDF‑Annotationen erhalten bleiben.
    question: Wenn ich mehr als einen Kommentar hinzufüge, funktioniert dann jeder
      Hyperlink im exportierten PDF?
  - answer: Öffnen Sie das erzeugte PDF, suchen Sie die Kommentar‑Annotation (in der
      Regel als Notiz‑Symbol angezeigt), klicken Sie darauf, um den Kommentartext
      anzuzeigen, und klicken Sie dann auf den blauen unterstrichenen Link; er sollte
      die Ziel‑URL in einem Webbrowser öffnen.
    question: Wie kann ich überprüfen, ob der Hyperlink im Kommentar nach der PDF‑Erstellung
      tatsächlich funktioniert?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Hyperlink‑Comment einfügen & als PDF exportieren
og_description: Lernen Sie, wie man einen anklickbaren Link in einem Word‑Comment einbettet und ihn in eine PDF‑Annotation umwandelt.
og_image_alt: Anleitung, die zeigt, wie man einem Word‑Dokument einen Kommentar mit einem anklickbaren Hyperlink hinzufügt und ihn mit Aspose.Words für .NET als PDF‑Annotation exportiert
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hyperlink‑Comment hinzufügen und als PDF‑Annotation exportieren mit Aspose.Words für .NET
In diesem Tutorial sehen Sie, wie man ein Word‑Dokument erstellt, einen Kommentar einfügt, der einen anklickbaren Hyperlink zu einer externen Website enthält, diesen Kommentar so konfiguriert, dass er als PDF‑Annotation angezeigt wird, das Dokument als PDF exportiert und die resultierende PDF‑Datei überprüft. Der Schritt‑für‑Schritt‑Code ermöglicht das Hinzufügen von reichhaltigen, link‑aktivierten Kommentaren und deren Erhalt beim Konvertieren in PDF, sodass interaktive Notizen leicht mit Lesern geteilt werden können.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: Was steuert das dritte Argument (`false`) in `InsertHyperlink`?**  
A: `InsertHyperlink`s dritter Parameter gibt an, ob der Link als Feld behandelt werden soll; wird er auf `false` gesetzt, wird ein einfacher Hyperlink eingefügt, der in der PDF‑Annotation funktioniert, ohne dass ein Feldcode erforderlich ist.

**Q: Wie kann ich den Kommentar im Word‑Dokument als Sprechblase anzeigen lassen, anstatt als PDF‑Annotation?**  
A: Setzen Sie `myDocument.LayoutOptions.CommentDisplayMode` auf `CommentDisplayMode.ShowInBalloons`, bevor Sie `Save` aufrufen; das PDF enthält dann den Kommentar als regulären Word‑Comment statt als Annotation.

**Q: Wenn ich mehr als einen Kommentar hinzufüge, funktioniert dann jeder Hyperlink im exportierten PDF?**  
A: Ja – jeder `Comment`, den Sie einem Absatz hinzufügen, kann einen eigenen `InsertHyperlink`‑Aufruf enthalten, und alle Hyperlinks werden beim Speichern des Dokuments als separate PDF‑Annotationen erhalten bleiben.

**Q: Wie kann ich überprüfen, ob der Hyperlink im Kommentar nach der PDF‑Erstellung tatsächlich funktioniert?**  
A: Öffnen Sie das erzeugte PDF, suchen Sie die Kommentar‑Annotation (in der Regel als Notiz‑Symbol angezeigt), klicken Sie darauf, um den Kommentartext anzuzeigen, und klicken Sie dann auf den blauen unterstrichenen Link; er sollte die Ziel‑URL in einem Webbrowser öffnen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}