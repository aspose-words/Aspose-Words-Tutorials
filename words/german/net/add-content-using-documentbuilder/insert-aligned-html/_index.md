---
title: HTML mit Ausrichtung in ein Word-Dokument einfügen mit Aspose.Words für .NET
weight: 210
limit:
description: Erfahren Sie, wie Sie HTML mit bestimmter Ausrichtung in ein Word-Dokument einfügen können, indem Sie Aspose.Words für .NET verwenden.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# HTML mit Ausrichtung in ein Word-Dokument einfügen mit Aspose.Words für .NET
Dieses Tutorial zeigt, wie man den DocumentBuilder von Aspose.Words für .NET verwendet, um HTML-Markup in ein Word-Dokument einzubetten und dessen Ausrichtung zu steuern. Sie sehen, wie das HTML eingefügt, die Absatzausrichtung (links, zentriert oder rechts) festgelegt und anschließend das resultierende Dokument gespeichert wird. Das Beispiel ist ideal für Entwickler, die web‑ähnliche Formatierung beibehalten müssen, während sie Word‑Dateien programmgesteuert erzeugen.

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

**Q: Kann InsertHtml verwendet werden, um HTML in ein bestehendes Word-Dokument einzufügen, anstatt in ein neues?**  
A: Ja. Erstellen Sie ein Document aus der vorhandenen Datei, positionieren Sie den DocumentBuilder‑Cursor an die gewünschte Stelle, an der das HTML eingefügt werden soll (z. B. mit builder.MoveToDocumentEnd()), und rufen Sie anschließend builder.InsertHtml mit Ihrem Markup auf.

**Q: Welche HTML-Attribute werden von InsertHtml für die Ausrichtung berücksichtigt?**  
A: InsertHtml berücksichtigt das Attribut "align" bei Block‑Elementen wie &lt;p&gt;, &lt;div&gt; und Überschriften‑Tags und wendet die entsprechende Absatzausrichtung im resultierenden Word-Dokument an.

**Q: Was passiert, wenn die HTML‑Zeichenkette nicht unterstützte Tags oder CSS enthält?**  
A: Nicht unterstützte Tags werden ignoriert und ihr Inhalt als Klartext eingefügt; Inline‑CSS‑Stile, die Aspose.Words nicht erkennt, werden ebenfalls ignoriert, sodass nur der unterstützte Teilbereich von HTML gerendert wird.

**Q: Muss ich den DocumentBuilder schließen, bevor ich das Dokument speichere?**  
A: Ein explizites Schließen ist nicht erforderlich; nach dem Einfügen des HTML können Sie direkt doc.Save mit dem gewünschten Dateinamen und Format aufrufen, und die Ressourcen des Builders werden automatisch freigegeben.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}