---
title: HTML mit Ausrichtung in ein Word‑Dokument einfügen mit Aspose.Words für .NET
weight: 210
limit:
description: Erfahren Sie, wie Sie rohes HTML mit links, zentriert oder rechts ausgerichtet in ein Word‑Dokument einfügen, indem Sie Aspose.Words für .NET verwenden.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# HTML mit Ausrichtung in ein Word‑Dokument einfügen mit Aspose.Words für .NET
Dieses interaktive Tutorial zeigt, wie rohes HTML in ein Word‑Dokument eingebettet wird, während die Ausrichtung – links, zentriert oder rechts – mit Aspose.Words für .NET gesteuert wird. Durch die Nutzung von Document und DocumentBuilder können Sie einen HTML‑String einfügen und die gewünschte Absatz‑Ausrichtung mit nur wenigen Code‑Zeilen anwenden. Das Beispiel ist ideal, wenn Sie die HTML‑Formatierung beibehalten und den Inhalt präzise in Ihrem Dokument platzieren müssen.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: Was passiert, wenn der an DocumentBuilder.InsertHtml übergebene HTML‑String Tags enthält, die Aspose.Words nicht unterstützt, wie <script> oder <iframe>?**
A: Nicht unterstützte Tags werden ignoriert; Aspose.Words analysiert nur den Teilbereich von HTML, den es rendern kann, sodass <script>, <iframe> und ähnliche Elemente entfernt werden, während der restliche Inhalt eingefügt wird.

**Q: Werden Inline‑CSS‑Stile (z. B. <span style=\"color:red;\">) beim Einsatz von InsertHtml beibehalten?**
A: Ja, InsertHtml berücksichtigt viele Inline‑CSS‑Eigenschaften wie color, font‑size und background und wandelt sie in die entsprechende Word‑Formatierung um.

**Q: Erzeugt InsertHtml automatisch einen neuen Absatz für Block‑Elemente wie <div> oder <h1>?**
A: Block‑Elemente werden Word‑Absätzen zugeordnet, sodass jedes <div>, <p>, <h1> usw. zu einem eigenen Absatz im Dokument wird.

**Q: Wie kann ich HTML an einer bestimmten Stelle in einem bestehenden Dokument einfügen, anstatt am Anfang?**
A: Bewegen Sie den DocumentBuilder‑Cursor zum gewünschten Knoten (z. B. builder.MoveToDocumentEnd() oder builder.MoveToParagraph(index)), bevor Sie InsertHtml aufrufen; das HTML wird an der aktuellen Cursor‑Position eingefügt.

**Q: Wenn das Dokument bereits Text enthält, überschreibt das Aufrufen von InsertHtml den bestehenden Inhalt?**
A: Nein, InsertHtml fügt das geparste HTML an der aktuellen Position des Builders ein, ohne vorhandene Knoten zu löschen, es sei denn, Sie verschieben den Cursor explizit in diese Knoten oder löschen sie vorher.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}