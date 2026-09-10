---
title: Horizontales Trennlinien‑Shape in ein Word‑Dokument einfügen mit Aspose.Words für .NET
weight: 110
limit:
description: Schritt‑für‑Schritt‑Anleitung zum Einfügen eines horizontalen Trennlinien‑Shapes in ein Word‑Dokument mit Aspose.Words für .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Horizontales Trennlinien‑Shape in ein Word‑Dokument einfügen mit Aspose.Words für .NET
Erfahren Sie, wie Sie Aspose.Words für .NET verwenden, um ein horizontales Trennlinien‑Shape in ein Word‑Dokument einzufügen. Dieses Tutorial führt Sie durch das Erstellen eines neuen Dokuments, das Hinzufügen einer Textzeile, das Platzieren eines horizontalen Trennlinien‑Shapes mit DocumentBuilder und das Speichern der Datei. Die horizontale Trennlinie dient als einfacher visueller Trenner für Ihren Inhalt.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Kann ich das Aussehen (Farbe, Dicke) der mit DocumentBuilder.InsertHorizontalRule() eingefügten horizontalen Trennlinie ändern?**
A: InsertHorizontalRule erzeugt ein integriertes horizontales Linien‑Shape mit Standardformatierung; um das Aussehen zu ändern, müssen Sie das eingefügte Shape‑Objekt (builder.CurrentParagraph.LastChild) abrufen und dessen LineFormat‑Eigenschaften anpassen.

**Q: Was passiert, wenn ich InsertHorizontalRule() nach einem Absatz aufrufe, der bereits mit einem Zeilenumbruch endet?**
A: Die Methode fügt die Trennlinie als separaten Absatz ein, sodass ein vorhergehender Zeilenumbruch lediglich einen leeren Absatz vor der Trennlinie erzeugt; die Trennlinie wird weiterhin in einer eigenen Zeile angezeigt.

**Q: Ist es möglich, mit DocumentBuilder mehr als eine horizontale Trennlinie im selben Dokument einzufügen?**
A: Ja, jeder Aufruf von builder.InsertHorizontalRule() fügt ein neues horizontales Trennlinien‑Shape an der aktuellen Cursor‑Position hinzu, wodurch mehrere Trennlinien im gesamten Dokument möglich sind.

**Q: Funktioniert InsertHorizontalRule() beim Speichern des Dokuments in anderen Formaten als DOCX, z. B. PDF?**
A: Die horizontale Trennlinie wird als Shape im Dokumentenmodell gespeichert, sodass sie beim Speichern als PDF, XPS oder in anderen unterstützten Formaten korrekt im Ausgabe‑Dokument gerendert wird.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}