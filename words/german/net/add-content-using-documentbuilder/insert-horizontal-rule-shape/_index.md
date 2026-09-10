---
title: Horizontale Regel‑Form in ein Word-Dokument einfügen mit Aspose.Words for .NET
weight: 110
limit:
description: Erfahren Sie, wie Sie mit Aspose.Words for .NET und DocumentBuilder eine horizontale Regel‑Form zu einem Word-Dokument hinzufügen.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Horizontale Regel‑Form in ein Word-Dokument einfügen mit Aspose.Words
In diesem Tutorial lernen Sie, wie Sie programmgesteuert eine horizontale Regel‑Form in ein Word-Dokument mit Aspose.Words for .NET einfügen. Mit den Klassen Document und DocumentBuilder erstellen wir ein neues Dokument, fügen einen Textabsatz hinzu und platzieren anschließend an der gewünschten Stelle eine horizontale Linien‑Form. Die horizontale Regel dient als visueller Trenner, der für Abschnittswechsel oder visuelle Hervorhebungen nützlich sein kann.

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

**Q: Wo genau fügt `builder.InsertHorizontalRule()` die Linie im Dokument ein?**
A: `InsertHorizontalRule` fügt eine horizontale Regel‑Form an der aktuellen Cursorposition des `DocumentBuilder` ein; wenn Sie sie in einer eigenen Zeile haben möchten, rufen Sie vor dem Einfügen `builder.Writeln()` auf.

**Q: Kann ich die Dicke, Farbe oder Breite der eingefügten horizontalen Regel ändern?**
A: `InsertHorizontalRule` fügt eine standardmäßig formatierte Regel hinzu und stellt keine Formatierungsoptionen bereit; um diese Eigenschaften anzupassen, müssen Sie manuell ein `Shape` einfügen (z. B. `builder.InsertShape(ShapeType.HorizontalLine)`) und anschließend dessen `LineFormat`‑Eigenschaften setzen.

**Q: Ist es möglich, mehr als eine horizontale Regel im selben Dokument hinzuzufügen?**
A: Ja – rufen Sie einfach jedes Mal `builder.InsertHorizontalRule()` auf, wenn Sie eine neue Regel benötigen; jeder Aufruf erzeugt eine separate Form an der aktuellen Position des Builders.

**Q: Wird die horizontale Regel sichtbar sein, wenn die gespeicherte .docx in Microsoft Word geöffnet wird?**
A: Auf jeden Fall; die Regel wird als Form innerhalb der .docx-Datei gespeichert, sodass Word sie exakt so anzeigt, wie sie im erzeugten Dokument erscheint.

**Q: Was passiert, wenn das `dataDir`‑Verzeichnis vor dem Aufruf von `doc.Save(...)` nicht existiert?**
A: `doc.Save` wirft eine `DirectoryNotFoundException`; stellen Sie sicher, dass das Zielverzeichnis existiert, oder erstellen Sie es programmgesteuert, bevor Sie speichern.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}